---
title: "IEnumCodePaths2 | Microsoft Docs"
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
  - "IEnumCodePaths2"
helpviewer_keywords: 
  - "IEnumCodePaths2 介面"
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示程式碼路徑的清單。  
  
## 語法  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示程式碼路徑的清單。  
  
## 呼叫者的備忘稿  
 呼叫[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)以取得這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumCodePaths2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|擷取指定的列舉型別序列中的程式碼路徑。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|略過指定的數目的列舉型別序列中的程式碼路徑。|  
|[重設](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../Topic/IEnumCodePaths2::GetCount.md)|取得列舉值中的程式碼路徑數目。|  
  
## 備註  
 程式碼路徑代表在程式中的分支點或函式呼叫。  一份程式碼路徑代表透過它所佔用的程式碼執行的路徑。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)