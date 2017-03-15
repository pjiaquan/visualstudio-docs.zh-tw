---
title: "類型的視覺化檢視和自訂檢視器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，自訂檢視器"
  - "偵錯 [偵錯 SDK]，類型的視覺化檢視"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 類型的視覺化檢視和自訂檢視器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

型別視覺化檢視是非常特殊的格式顯示的資料元件。  這種格式完全取決於視覺化檢視的實作器，是一般使用者或協力廠商供應商的視覺化檢視。  
  
 自訂的檢視器是非常特殊的格式，顯示一份資料的自訂運算式評估工具的部分。  這種格式是完全取決於自訂檢視器中，這表示格式是由運算式評估工具 \(EE\) 的實作器的實作器。  
  
## 支援的運算式評估工具中的型別視覺化檢視  
 EE 可以支援一組視覺化工具可存取的介面，支援型別視覺化檢視： 例如介面[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)和[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。  請注意，卻不是負責實作型別視覺化檢視本身： 下，EE 只允許外部的視覺化檢視它的型別資訊的存取權。  可能得知 ee 給予一起隨附這類的視覺化檢視，並將其安裝在適當的地方，在 Visual Studio，另一個的協力廠商，或甚至是由一般使用者提供。  
  
## 自訂檢視器中的運算式評估工具的支援  
 EE 也支援自訂的檢視器中得知 ee 給予本身提供檢視的資料型別程式碼。  自訂的檢視器會實作[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)介面，其會處理所有職務顯示資料，在想要的格式。 \[檢視器\] 已顯示的完全控制權，並可以讓要修改的資料。  提供得知 ee 給予任何自訂的檢視器會隨附得知 ee 給予，當產品出貨。  
  
## 請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)