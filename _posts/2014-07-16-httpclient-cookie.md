---
layout: post
title: httpclient cookie
tags: [httpclient] 
---

   
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    
    import org.apache.http.HttpEntity;
    import org.apache.http.client.CookieStore;
    import org.apache.http.client.ResponseHandler;
    import org.apache.http.client.entity.EntityBuilder;
    import org.apache.http.client.methods.HttpPost;
    import org.apache.http.client.protocol.HttpClientContext;
    import org.apache.http.cookie.Cookie;
    import org.apache.http.impl.client.BasicCookieStore;
    import org.apache.http.impl.client.BasicResponseHandler;
    import org.apache.http.impl.client.CloseableHttpClient;
    import org.apache.http.impl.client.HttpClients;
    import org.apache.http.message.BasicNameValuePair;
    import org.apache.shiro.SecurityUtils;
    import org.apache.shiro.authc.AuthenticationToken;
    import org.apache.shiro.authc.UsernamePasswordToken;
    import org.apache.shiro.subject.Subject;
    import org.extt.common.utils.Debug;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestMethod;
    import org.springframework.web.bind.annotation.ResponseBody;
    
    @Controller
    @RequestMapping("/directLogin")
    public class DirectLoginController {
    
        @RequestMapping(method = RequestMethod.POST)
        @ResponseBody
        String exec(HttpServletRequest request, HttpServletResponse response) {
            if (tryLogin(request, response))
                return "1";
            return "0";
        }
        
        //只允许post进行登录
        @RequestMapping(method = RequestMethod.GET)
        @ResponseBody
        String test()
        {
            return "only post";
        }
    
    
        boolean tryLogin(HttpServletRequest request, HttpServletResponse response) {
    
            try {
                Subject subject = SecurityUtils.getSubject();
                String host = request.getRemoteHost();
                String username = request.getParameter("username");
                String password = request.getParameter("password");
    
                AuthenticationToken token = new UsernamePasswordToken(username,
                        password, false, host);
                subject.login(token);
            } catch (Exception e) {
                return false;
            }
    
            return true;
        }
    
        
        public static void testLogin(HttpClientContext context) throws Exception
        {
            CloseableHttpClient client = HttpClients.custom().build();
    
            String fullUrl = "http://localhost:8080/test/directLogin";
            HttpPost request = new HttpPost(fullUrl);
            BasicNameValuePair userName = new BasicNameValuePair("username",
                    "admin");
            BasicNameValuePair password = new BasicNameValuePair("password",
                    "admin");
    
            HttpEntity entity = EntityBuilder.create()
                    .setParameters(userName, password).build();
            ResponseHandler<String> responseHandler = new BasicResponseHandler();
            request.setEntity(entity);
            String text = client.execute(request, responseHandler, context);
            System.out.println("text " + text);
            
            client.close();
        }
        
        public static void testAccountInfo(HttpClientContext context) throws Exception
        {
            CloseableHttpClient client = HttpClients.custom().build();
            String text;
            ResponseHandler<String> responseHandler = new BasicResponseHandler();
    
            text = client.execute( new HttpPost("http://localhost:8080/test/accountInfo"), responseHandler, context);
            System.out.println("acc " + text);
            client.close();
        }
        
        public static void main(String args[]) {
            try {
                
                HttpClientContext context = HttpClientContext.create();
                CookieStore cookieStore = new BasicCookieStore();
                context.setCookieStore(cookieStore);
                
                testLogin(context);
                testAccountInfo(context);
    
                for(Cookie c: cookieStore.getCookies() )
                {
                    Debug.println( c.getDomain(), c.getExpiryDate(), c.getName(), c.getValue() );
                }
    
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }




 




