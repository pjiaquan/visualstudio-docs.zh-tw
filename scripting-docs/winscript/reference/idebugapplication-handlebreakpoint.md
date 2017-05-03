---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
導致目前的執行緒封鎖並傳送中斷點的通知至偵錯工具 IDE。  
  
## 語法  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### 參數  
 `br`  
 \[in\] 中斷的原因。  
  
 `pbra`  
 \[in\] 要採取的動作，在偵錯工具繼續執行應用程式。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 語言引擎呼叫這個方法會在中斷點的執行緒中。  這個方法會封鎖目前的執行緒並傳送中斷點通知至偵錯工具 IDE。  當偵錯工具繼續執行應用程式時， `pbra` 參數指定採取動作。  
  
> [!NOTE]
>  在中斷點期間，語言引擎可能由執行緒呼叫執行像是列舉型別或堆疊框架來評估運算式。  
  
 這個方法會 `IApplicationDebugger::onHandleBreakPoint` 呼叫。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)