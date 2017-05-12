---
title: "SCRIPTUICITEM 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTUICITEM 列舉
代表 UI 項目的型別。  使用在 [IActiveScriptSiteUIControl::GetUIBehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。  
  
## 語法  
  
```vb  
typedef enum tagSCRIPTUICITEM {   
    SCRIPTUICITEM_INPUTBOX = 1,   
    SCRIPTUICITEM_MSGBOX = 2,   
    } SCRIPTUICITEM;  
  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTUICITEM\_INPUTBOX|輸入控制項。|  
|SCRIPTUICITEM\_MSGBOX|訊息方塊。|