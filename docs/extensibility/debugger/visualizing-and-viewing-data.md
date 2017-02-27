---
title: "視覺化及檢視資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，檢視資料"
  - "偵錯 [偵錯 SDK]，將資料視覺化"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 視覺化及檢視資料
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

輸入的視覺化檢視和自訂的檢視器呈現的資料都是開發人員迅速有意義的方式。  運算式評估工具 \(EE\) 可支援協力廠商型別視覺化檢視，以及提供它自己的自訂檢視器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]決定多少的型別視覺化檢視和自訂的檢視器物件的型別相關聯藉由呼叫[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)方法。  如果有一個以上的型別視覺化檢視或自訂的檢視器可用，會呼叫 Visual Studio [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法來擷取一份這些視覺化檢視和檢視器 \(事實上，一份`CLSID`s 實作之視覺化工具和檢視器\) 並呈現給使用者。  
  
## 支援的型別視覺化檢視  
 有幾個得知 ee 給予必須實作用來支援型別視覺化檢視的介面。  這些介面可以區分為兩大類： 所列出的型別視覺化檢視，另一種存取屬性的資料。  
  
### 列出型別視覺化檢視  
 得知 ee 給予支援清單的型別視覺化檢視，在實作`IDebugProperty3::GetCustomViewerCount`和`IDebugProperty3::GetCustomViewerList`。  這些方法會傳遞至對應的方法呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)藉由呼叫[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。  這個方法會要求[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)介面，您可以從取得[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面傳遞至[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  `IEEVisualizerServiceProvider::CreateVisualizerService`也需要[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)和[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)介面傳給此`IDebugParsedExpression::EvaluateSync`。  建立所需的最後一個介面`IEEVisualizerService`介面是[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)得知 ee 給予實作的介面。  這個介面允許正以視覺化檢視的屬性進行變更。  所有的屬性資料封裝在[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)也得知 ee 給予實作的介面。  
  
### 存取屬性的資料  
 存取屬性的資料會透過[IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。  若要取得這個介面，呼叫 Visual Studio [QueryInterface](/visual-cpp/atl/queryinterface)屬性之物件取得[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面 \(在同一個實作的物件上實作[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面\)，接著再呼叫[GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)方法，以取得`IPropertyProxyEESide`介面。  
  
 所有資料都傳遞進出`IPropertyProxyEESide`介面會封裝在[IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)介面。  這個介面表示的位元組陣列，而 Visual Studio，並得知 ee 給予由存取關聯式資料庫。  變更屬性的資料時，會建立 Visual Studio 的`IEEDataStorage`物件持有的新資料和呼叫[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)與該資料物件，以取得新的`IEEDataStorage`物件，反而會傳遞至[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)更新屬性的資料。  `IPropertyProxyEESide::CreateReplacementObject`可讓自己實作的類別具現化 EE `IEEDataStorage`介面。  
  
## 支援的自訂檢視器  
 旗標`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`中設定的`dwAttrib`欄位的[DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構 \(呼叫所傳回的[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\) 表示該物件具有與其相關聯的自訂檢視器。  當設定這個旗標時，會取得 Visual Studio [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面從[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面使用[QueryInterface](/visual-cpp/atl/queryinterface)。  
  
 如果使用者選取自訂的檢視器\] 時，Visual Studio 會具現化自訂檢視器\]，並使用 「 檢視器 」 的`CLSID`所提供的`IDebugProperty3::GetCustomViewerList`方法。  然後呼叫 Visual Studio [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)來向使用者顯示的值。  
  
 一般情況下， `IDebugCustomViewer::DisplayValue`呈現唯讀方式檢視資料。  若要允許資料變更，得知 ee 給予必須實作自訂介面屬性的物件上支援變更的資料。  `IDebugCustomViewer::DisplayValue`方法會使用這個自訂介面以支援變更的資料。  方法會在 \[尋找自訂介面`IDebugProperty2`介面做為傳入的`pDebugProperty`引數。  
  
## 同時支援輸入視覺化檢視和自訂的檢視器  
 型別視覺化檢視，並在 \[自訂檢視器，可支援 EE [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法。  首先，得知 ee 給予新增的數目在提供的自訂檢視器所傳回的值[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)方法。  其次，得知 ee 給予附加`CLSID`s 自己自訂的檢視器所傳回的清單的[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。  
  
## 請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [類型的視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)