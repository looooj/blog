---
layout: post
title: openssl PEM_read_bio_
tags: [openssl,PEM_read_bio]
category: openssl
---

openssl PEM_read_ 函数是从文件读取pem格式的文件，有时候需要从内存直接读取pem格式，可以使用PEM_read_bio_ 函数

    
    BIO* b = BIO_new_mem_buf( (void*)pem_str, strlen(pem_str) );
    RSA* rsa_read = PEM_read_bio_RSA_PUBKEY( b, &mPublicKey, 0, pass );
    BIO_free( b );
