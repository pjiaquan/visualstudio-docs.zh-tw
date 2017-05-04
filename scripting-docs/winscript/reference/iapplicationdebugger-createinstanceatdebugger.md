---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::CreateInstanceAtDebugger"
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::CreateInstanceAtDebugger
由為跨處理序對偵錯工具的程式碼可讓物件以偵錯工具的處理序。  
  
> [!IMPORTANT]
>  因為它允許未受信任的程式碼會在信任的偵錯工具執行緒，將任意物件不應該實作這個方法。  
  
## 語法  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### 參數  
 `rclsid`  
 \[in\] 類別識別項 \(CLSID\) 分類為所建立的物件。  
  
 `pUnkOuter`  
 \[in\] 為彙總的一部分，因此，如果 `NULL`，並不會建立任何物件。  否則， `pUnkOuter` 是指向彙總物件的 `IUnknown` 介面 \(控制項 `IUnknown`\)。  
  
 `dwClsContext`  
 \[in\] 正在執行的可執行程式碼的內容。  值 `CLSCTX`從列舉型別中取得。  
  
 `riid`  
 \[out\] 用來的介面識別項與物件進行通訊。  
  
 `ppvObject`  
 \[out\] 指標變數的位址，會接收 `riid` 中要求的介面指標。  在成功傳回時，`ppvObject` \*包含要求的介面指標。  在發生失敗， \*`ppvObject` 包含 `NULL`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法 `CoCreateInstance`的委派。  
  
 方法目前並未執行。  
  
## 請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)