---
title: "API 參考 (Visual Studio 偵錯) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]、 [API 參考"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# API 參考 (Visual Studio 偵錯)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

＜ 參考 ＞ 章節會包含 API，也就是顯示的語法和用法，所有的 API 項目，如本指南的概觀，並有各種的程式碼範例。  依類別字母順序列出的所有參考。  
  
 下表顯示一般`HRESULT`方法所傳回的值。  
  
|名稱|描述|值|  
|--------|--------|-------|  
|S\_OK|成功。|0x00000000|  
|E\_UNEXPECTED|未預期的錯誤。|0x8000FFFF|  
|E\_NOTIMPL|尚未實作。|0x80004001|  
|E\_OUTOFMEMORY|記憶體不足，無法完成這項作業。|0x8007000E|  
|E\_INVALIDARG|一個或多個引數無效。|0x80070057|  
|E\_NOINTERFACE|不支援這種介面。|0x80004002|  
|E\_POINTER|無效的指標。|0x80004003|  
|E\_HANDLE|無效的控制代碼。|0x80070006|  
|E\_ABORT|操作中止。|0x80004004|  
|E\_FAIL|未預期的錯誤。|0x80004005|  
|E\_ACCESSDENIED|一般性存取被拒的錯誤。|「 0x80070005|  
  
> [!NOTE]
>  當[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯方法會傳回`S_OK`，則會假設全都列出參數仍然有效，也就是沒有驗證在中執行 out 參數的指標時`S_OK`會傳回。  
  
> [!NOTE]
>  不正確或`NULL` \[out\] 參數可能會造成當機 IDE。  
  
## 請參閱  
 [介面](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio 偵錯工具擴充性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)