---
layout: post
title: fastxml jsonformat 设置默认TimeZone
tags: [fastxml,json] 
---

@JsonFormat 提供时间格式化输出，但是默认的TimeZone是GMT, 

   
    private static TimeZone defaultTimeZone = java.util.TimeZone.getDefault();
    
    public static MappingJsonFactory getMappingJsonFactory()
    {
        MappingJsonFactory factory = new MappingJsonFactory();
        factory.getCodec().setTimeZone(defaultTimeZone);
        System.out.println( factory.getCodec().getSerializationConfig().getTimeZone().toString() );
        return factory;
    }


