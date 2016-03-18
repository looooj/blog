---
layout: post
title: spring @Transactional exception not rollback
category: spring
tags: [spring]
---
spring  @Transactional  exception not rollback


org.springframework.transaction.interceptor.TransactionAspectSupport

     protected Object invokeWithinTransaction(Method method, Class targetClass, final      InvocationCallback invocation)
			throws Throwable {

       try {
           ...
       }
       catch (Throwable ex) {
          // target invocation exception
          completeTransactionAfterThrowing(txInfo, ex);
          throw ex;
       }
       ...
    }

completeTransactionAfterThrowing  call rollback

    protected void completeTransactionAfterThrowing(TransactionInfo txInfo, Throwable ex) {
        ...
        if (txInfo.transactionAttribute.rollbackOn(ex)) {
            ...
            txInfo.getTransactionManager().rollback(txInfo.getTransactionStatus());
            ...
        }
        else
        {
            ...
            txInfo.getTransactionManager().commit(txInfo.getTransactionStatus());
            ...
        }

    }

txInfo.transactionAttribute

    public boolean rollbackOn(Throwable ex) {
        return (ex instanceof RuntimeException || ex instanceof Error);
    }

other Exception not rollback

use rollbackForClassName

    @Transactional(propagation=Propagation.REQUIRED,rollbackForClassName={"Exception"})
