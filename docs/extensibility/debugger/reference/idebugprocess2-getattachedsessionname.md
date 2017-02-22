---
title: "IDebugProcess2::GetAttachedSessionName | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
helpviewer_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得工作階段是偵錯此處理程序的名稱。  IDE 偵錯特定電腦上的特定程序的使用者，可以顯示這項資訊。  
  
> [!NOTE]
>  這個方法已被取代，而且它的實作應該一律會傳回`E_NOTIMPL`。  
  
## 語法  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### 參數  
 `pbstrSessionName`  
  
## 傳回值  
 這個方法永遠會傳回`E_NOTIMPL`。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)