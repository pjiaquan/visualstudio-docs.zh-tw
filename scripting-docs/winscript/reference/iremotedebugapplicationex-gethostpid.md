---
title: "IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:GetHostPid
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:GetHostPid"
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:GetHostPid
傳回主應用程式的處理序 ID。  
  
## 語法  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### 參數  
 `dwHostPid`  
 \[in\] 主應用程式處理序識別項。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 使用由 IDE。  
  
## 請參閱  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/zh-tw/2f65fa67-06b7-4053-8945-22383ab66343)