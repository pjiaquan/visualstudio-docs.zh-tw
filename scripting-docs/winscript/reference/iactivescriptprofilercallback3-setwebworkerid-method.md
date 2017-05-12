---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知背景工作 ID 的分析工具對程式碼剖析工作階段使用。  如果函式不會執行在頁面中，則這個方法不會叫用。  `webWorkerId` 的值除以 1 加入每個背景工作的開始， 1。  ID 值也不會穩定的在工作階段以後，並且只在對應至背景工作的建立順序。  
  
## 語法  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### 參數  
 `webWorkerId`  
 網路背景工作 ID.  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。