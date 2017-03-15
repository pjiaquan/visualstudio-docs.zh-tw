---
title: "原則範本和 [屬性] 視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性視窗中，原則範本"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 原則範本和 [屬性] 視窗
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當專案包含在企業樣板專案時，則該企業樣板專案可以強制執行原則。  樣板原則就會變成一種限制的系統，可用來設定屬性的預設值、 隱藏的屬性、 加入 \[工具\] 功能表等等。  
  
 使用樣板原則來控制顯示的資訊**屬性**視窗是不同於實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>處理元件等級的物件屬性，而樣板原則可以用來限制在方案或專案層級的物件屬性。  亦即  
  
-   實作方法，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>來判斷項目會顯示在**屬性**特定物件的視窗  
  
-   在方案和專案層級使用樣板原則，來判斷項目會顯示在**屬性**先前指定的物件的視窗  
  
 使用樣板原則選擇性地限制特定的屬性，在**屬性** 時指定型別的專案項目\] 視窗中選取 **方案總管\] 中**來使用專案的開發小組的所有成員會非常方便。  例如，使用樣板原則時，您可以設定連接字串中的所有資訊的資料庫為程式開發人員並將連接字串為唯讀。  如此一來，您可以提供簡單的方法，來確保每位開發人員會使用正確的路徑進行資料存取。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [擴充屬性](../../extensibility/internals/extending-properties.md)