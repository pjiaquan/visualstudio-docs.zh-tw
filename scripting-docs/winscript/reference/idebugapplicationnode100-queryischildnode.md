---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
判斷指定的檔案是否屬於其中一個節點的子節點。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md) 由 PDM v10.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### 參數  
 `pSearchKey`  
 擷取索引鍵。  
  
## 請參閱  
 [IDebugApplicationNode100 介面](../../winscript/reference/idebugapplicationnode100-interface.md)