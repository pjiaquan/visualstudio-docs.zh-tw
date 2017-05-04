---
title: "SCRIPTTRACEINFO 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO 列舉
表示要追蹤的指令碼事件。  使用在 [IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。  
  
## 語法  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|指令碼的開頭。|  
|SCRIPTTRACEINFO\_SCRIPTEND|結尾的指令碼。|  
|SCRIPTTRACEINFO\_COMCALLSTART|COM 呼叫的開始。|  
|SCRIPTTRACEINFO\_COMCALLEND|COM 呼叫的結尾。|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|建立物件時啟動。|  
|SCRIPTTRACEINFO\_CREATEOBJEND|建立物件的結尾。|  
|SCRIPTTRACEINFO\_GETOBJSTART|GetObject 呼叫的開始。|  
|SCRIPTTRACEINFO\_GETOBJEND|GetObject 呼叫的結尾。|