---
layout: post
title: openssl PEM\_read\_bio\_
tags:[openssl,PEM_read_bio]
category:openssl
---

openssl PEM\_read\_ 函数是从文件读取pem格式的文件，有时候需要从内存直接读取pem格式，可以使用PEM\_read\_bio\_ 函数

    
    BIO* b = BIO_new_mem_buf( (void*)pem_str, strlen(pem_str) );
    RSA* rsa_read = PEM_read_bio_RSA_PUBKEY( b, &mPublicKey, 0, pass );
    BIO_free( b );
