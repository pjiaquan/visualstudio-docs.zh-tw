---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierDescription2 介面"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

可讓[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI，以顯示內部文字**傳輸資訊**一節的**附加至處理序**對話方塊。  
  
## 語法  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由連接埠的供應商。  
  
## 方法  
 下表顯示的方法`IDebugPortSupplierDescription2`。  
  
|方法|描述|  
|--------|--------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|擷取連接埠提供者的說明和描述中繼資料。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll