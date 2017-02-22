---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
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
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount 方法"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得陣列中的項目的計數。  
  
## 語法  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### 參數  
 `pdwElements`  
 \[\] out傳回的計數。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法可看到所有的陣列物件項目為一維陣列，即使多維陣列的物件。  例如，假設陣列`myarray[3][2][6]`，這個方法會傳回在 36 `pdwElements`參數。  使用[GetElement](../Topic/IDebugArrayObject::GetElement.md)方法來擷取個別的項目一次。  
  
## 請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)