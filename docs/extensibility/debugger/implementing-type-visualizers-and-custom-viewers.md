---
title: "實作類型的視覺化檢視和自訂檢視器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，自訂檢視器"
  - "偵錯 [偵錯 SDK]，類型的視覺化檢視"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 實作類型的視覺化檢視和自訂檢視器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 類型的視覺化檢視和自訂檢視器可讓使用者檢視特定類型的資料比簡單的數字十六進位傾印更有意義的方式。 運算式評估工具 \(EE\) 可以將自訂檢視器與特定類型的變數或資料產生關聯。 這些自訂檢視器的實作方式 EE。 EE 也支援外部型別視覺化檢視，可能是來自另一個協力廠商或甚至是一般使用者。  
  
## 討論  
  
### 類型的視覺化檢視  
 Visual Studio 會要求類型的視覺化檢視和每個物件的自訂檢視器監看式視窗中顯示的清單。 運算式評估工具 \(EE\) 會提供這類它要支援類型的視覺化檢視和自訂檢視器的每一個型別清單。 呼叫 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 開始整個程序的存取類型的視覺化檢視和自訂檢視器 \(請參閱 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md) 的呼叫順序的詳細資訊\)。  
  
### 自訂檢視器  
 自訂檢視器中的特定資料型別 EE 實作，都由 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 介面。 自訂檢視器並不具有彈性的型別視覺化檢視，因為實作該特定的自訂檢視器 EE 正在執行時，才會使用。 實作自訂的檢視器會比實作類型的視覺化檢視支援簡單的。 不過，支援類型的視覺化檢視提供最大的彈性使用者他 \/ 她的資料視覺化。 在本文中的其餘部分是關於只有使用視覺化檢視類型。  
  
## 介面  
 EE 實作下列介面來支援視覺化檢視的類型，以供 Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE 取用下列介面，才能支援類型的視覺化檢視︰  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)