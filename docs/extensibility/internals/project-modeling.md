---
title: "專案模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動化 [Visual Studio SDK]，實作專案物件"
  - "專案模型自動化"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 專案模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您的專案實作標準專案物件，提供自動化的下一步： <xref:EnvDTE.Projects>和`ProjectItems`集合。 the `Project` and <xref:EnvDTE.ProjectItem> objects; 與您的實作只用於其餘的物件。  這些標準的物件被定義在 Dteinternal.h 檔案中。  BscPrj 範例中，提供標準的物件的實作。  您可以使用這些類別為模型來建立您自己突顯並排顯示的標準專案物件與其他專案類型的專案物件。  
  
 自動化消費者假設，才能夠呼叫<xref:EnvDTE.Solution>\("`<UniqueProjName>")` 和<xref:EnvDTE.ProjectItems> \(`n`\)， n以取得特定方案的專案中的索引編號。  此自動化呼叫會造成環境以呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>上適當的專案階層架構，為項目識別碼參數而 VSHPROPID\_ExtObject 與 VSHPROPID 參數中傳遞 VSITEMID\_ROOT。  `IVsHierarchy::GetProperty`傳回`IDispatch`提供核心的自動化物件指標`Project`已實作的介面。  
  
 下面是語法`IVsHierarchy::GetProperty`。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 專案容納巢狀結構，並使用集合來建立的專案項目群組。  階層架構看起來像這樣。  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 指的是巢狀結構<xref:EnvDTE.ProjectItem>物件可以是<xref:EnvDTE.ProjectItems>集合，同時因為`ProjectItems`集合可以包含巢狀的物件。  基本專案範例不會示範這個巢狀結構。  藉由實作`Project`物件時，您參與特性化整體的 automation 模型的設計類似樹狀結構的結構。  
  
 專案自動化依照下圖中的路徑。  
  
 ![Visual Studio 專案物件](../../extensibility/internals/media/projectobjects.png "ProjectObjects")  
專案自動化  
  
 如果您不會實作`Project`物件時，環境仍會傳回泛型`Project`物件，其中包含專案的名稱。  
  
## 請參閱  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>