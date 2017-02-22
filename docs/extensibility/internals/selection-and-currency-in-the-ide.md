---
title: "選取項目和 IDE 中的貨幣 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "貨幣，Visual Studio IDE"
  - "IDE 中，選取項目"
  - "選取項目，Visual Studio IDE"
  - "IDE 貨幣"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 選取項目和 IDE 中的貨幣
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式的開發環境 \(IDE\) 會維護有關使用者的資訊目前選取物件，使用選取 *內容*。 使用選取的內容，VSPackages 可以參加兩種方式追蹤的貨幣︰  
  
-   傳播到 IDE VSPackages 的貨幣資訊。  
  
-   藉由監視使用者在 IDE 中的目前選取項目。  
  
## 選取項目內容  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 全域追蹤的 IDE 貨幣，在它自己的全域選擇內容物件。 下表顯示構成的選取項目內容的項目。  
  
|項目|描述|  
|--------|--------|  
|目前的階層|通常是目前的專案。NULL 目前階層架構表示目前整個解決方案。|  
|目前的項目識別碼|選取的項目內目前的階層。在 \[專案\] 視窗中的多重選取時，可以有多個目前的項目。|  
|目前 `SelectionContainer`|保留 \[屬性\] 視窗應顯示屬性的一個或多個物件。|  
  
 此外，環境會維護兩個全域清單︰  
  
-   使用中的 UI 命令識別碼的清單  
  
-   目前使用中的項目型別清單。  
  
### 視窗類型和選取範圍  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會將 windows 組織成兩種一般類型︰  
  
-   階層類型 windows  
  
-   框架視窗，例如工具和文件視窗  
  
 IDE 會針對每個視窗類型以不同的方式追蹤貨幣。  
  
 最常見的專案類型\] 視窗會是 \[方案總管\]，以控制在 IDE。 專案類型\] 視窗會追蹤通用的階層和項目識別碼的全域範圍內容，而且 \[\] 視窗中依賴使用者的選取項目，以判斷目前的階層。 適用於專案類型 windows 環境提供全域服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, 、 透過哪些 VSPackages 可以監視目前開啟的項目值。 瀏覽環境中的屬性是此全域服務所驅動。  
  
 框架視窗，相反地，會使用框架視窗內 DocObject 推送 SelectionContext 值 （階層\/識別碼\/SelectionContainer 事）。 . 框架視窗會使用服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 針對此目的。 DocObject 可以只將值推選取容器中，只針對階層的本機值和項目識別碼不變，跟一般的 MDI 子文件。  
  
### 事件和貨幣  
 兩種類型的事件可能會發生影響環境的概念的貨幣︰  
  
-   會傳播到全域層級，而變更視窗框架的選取項目內容的事件。 這種事件的範例包括 MDI 子視窗開啟，全域工具視窗開啟或開啟一個專案類型的工具視窗。  
  
-   變更項目追蹤視窗框架的選取項目內容中的事件。 範例包括變更選取範圍內 DocObject 或變更專案類型\] 視窗中的選取項目。  
  
## 請參閱  
 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)   
 [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)