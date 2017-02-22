---
title: "屬性視窗物件清單 | Microsoft Docs"
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
  - "屬性視窗中，物件清單"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 屬性視窗物件清單
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[物件\] 清單中的**屬性**視窗是可讓您變更一或多個選取的視窗中可用的其他物件的選取範圍下拉式清單。  選取 \[從這個清單中不同的物件會觸發呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>通知環境已選取新的物件。  在顯示的資訊**屬性**視窗再變更為顯示新選取的物件相關聯的屬性。  
  
## \[物件\] 清單  
 \[物件\] 清單包含兩個欄位： 物件名稱 \(以粗體顯示\) 和物件型別。  
  
 從物件本身，擷取到左側以粗體顯示的物件型別所顯示的物件名稱使用`Name`屬性所提供的<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>介面。  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>唯一的方法，在<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，會傳回<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>為該介面 coclass。  **屬性** \] 視窗使用<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>取得 coclass，顯示為下拉式清單中的物件名稱的名稱。  
  
 如果物件沒有`Name`屬性，名稱不會顯示在 \[物件\] 清單中的 \[名稱\] 區域中。  如果您想要在 \[物件\] 清單中所顯示的名稱，您可以新增 \[名稱\] 屬性的物件。  
  
 如果 COM 物件並未實作<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>、 **屬性** \] 視窗會顯示在左邊的清單的介面名稱的物件名稱的位置。  
  
## 請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)