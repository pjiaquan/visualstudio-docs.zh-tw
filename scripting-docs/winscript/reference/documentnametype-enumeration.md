---
title: "DOCUMENTNAMETYPE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE 列舉"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE 列舉
描述輸入為檔案取得。  
  
## 語法  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|DOCUMENTNAMETYPE\_APPNODE|其出現在應用程式樹狀結構，取得名稱。|  
|DOCUMENTNAMETYPE\_TITLE|當它在檢視器標題列，取得名稱。|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|取得檔案名稱，但不包含路徑。|  
|DOCUMENTNAMETYPE\_URL|取得文件的 URL。|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|取得這個標頭附加與識別的列舉型別。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)