---
layout: post
tags: [github pages]
title: Use github pages Setup Your Blog
---

服务端

1 首先有github账户

2 创建一个repository, 例如blog 


客户端

    git clone https://github/username/blog.git
    cd blog
    git checkout --orphan gh-pages
 
克隆到本地，切换到gh-pages分支


方法1:
  参考<http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html>的余下步骤创建一个简单的blog，但是这样的页面也太简单，参照方法2可以创建一个正式的blog站点



方法2

  git clone https://github.com/plusjade/jekyll-bootstrap.git 

  复制jekyll-bootstrap下所有的子目录和文件到blog(除了.git)

  修改_config.yml， 替换成自己的信息,
      
      title : Jekyll Bootstrap
      author :
        name : Name Lastname
        email : blah@email.test
        github : username
        twitter : username
        feedburner : feedname
        ...

     
  如果使用 http://username.github.io/blog作为博客地址,需要设置BASE_PATH: /blog
   
       JB:
          version: 0.3.0
          BASE_PATH: /blog

 jekll-bootstrap已经包含disqus和google analytics的支持，只需要配置上short_name和tracking_id
 
        comments :
          provider : disqus
          disqus :
          short_name : your_short_name
    
        analytics :
          provider : google 
          google : 
            tracking_id : 'your tracking_id'    

最后commit 和 push

    git add .
    git commit -m 'new blog'
    git push origin gh-pages

如果创建失败github会发送邮件给你
  
  
- yaml 格式 <http://zh.wikipedia.org/zh/YAML>
- 注册disqus <https://disqus.com/>





- 
