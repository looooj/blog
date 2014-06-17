---
layout: post
title: spring jpa hibernate lazy 异常解决办法
tags: [spring,hibernate,jpa]
---

org.hibernate.LazyInitializationException

配置hibernate.enable_lazy_load_no_trans属性为true可以解决


    <?xml version="1.0" encoding="UTF-8"?>
    <persistence xmlns="http://java.sun.com/xml/ns/persistence"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                 xsi:schemaLocation="http://java.sun.com/xml/ns/persistence http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd"
                 version="2.0">
        <persistence-unit name="default" transaction-type="RESOURCE_LOCAL">
             <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
           <non-jta-data-source>dataSource</non-jta-data-source>
            <properties>
             ...
            <property name="hibernate.enable_lazy_load_no_trans" value="true" />
             ...
        </properties>
       </persistence-unit>
     </persistence>

