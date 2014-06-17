---
layout: post
title: shiro ajax user filter
tags: [shiro,ajax] 
---
session超时之后会返回login页面，客户端无法解析

扩展UserFilter，检查是否为ajax请求，如果是响应401
   
    @Component
    public class AjaxUserFilter extends UserFilter {
        @Override
        protected boolean onAccessDenied(ServletRequest request,
            ServletResponse response) throws Exception {
        
            HttpServletRequest req = WebUtils.toHttp(request);
            String xmlHttpRequest = req.getHeader("X-Requested-With");
        
            if ( xmlHttpRequest.equalsIgnoreCase("XMLHttpRequest") )
            {
                HttpServletResponse res = WebUtils.toHttp(response);
                res.sendError(401);
                return false;
            }
        
            return super.onAccessDenied(request, response);
        }
    }  

shiro.xml配置

    <!-- Shiro Filter -->
    <bean id="shiroFilter" class="org.apache.shiro.spring.web.ShiroFilterFactoryBean">
        <property name="securityManager" ref="securityManager" />
        <property name="loginUrl" value="/login" />
        <property name="successUrl" value="/" />
        <property name="filterChainDefinitions">
            <value>
                /login = authc
                /logout = logout
                /pages/** = anon
                /dict/** = anon
                /js-lib/** = anon
                /test/** = anon
                /** = user
            </value>
        </property>
        
        
        <property name="filters">
            <map>
                <entry key="user" value-ref="ajaxUserFilter" />
            </map>
        </property>
        
    </bean>


客户端

    function requestException(conn, response, options, eOpts) {
        var c = parseInt(response.status);
        switch (c) {
            case 401:
                {
                    alert("需要重新登录");
                    locationUrl(contextPath + "/login");
                }
                break;
            case 404:
                writeLog("404");
                break;
            default:
                alert("程序错误");
        }
    }
    Ext.Ajax.on('requestexception', requestException);







