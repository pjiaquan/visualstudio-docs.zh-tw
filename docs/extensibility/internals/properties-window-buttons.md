---
title: "屬性視窗] 按鈕 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性視窗中按鈕"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 屬性視窗] 按鈕
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根據開發語言和產品類型，某些按鈕預設會顯示的工具列上的**屬性**視窗。  在所有情況下， **分類**，  **Alphabetized**， **屬性**，以及 **屬性頁**按鈕即會顯示。  在視覺化 C\# 和 Visual Basic **事件**按鈕也會顯示。  在某些 Visual c \+ \+ 專案中，  **VC \+ \+ 訊息** 和  **VC 會覆寫**按鈕即會顯示。  對於其他專案類型，可能會顯示額外的按鈕。  如需有關在按鈕**屬性** \] 視窗中，請參閱[屬性視窗](../../ide/reference/properties-window.md)。  
  
## 實作的屬性視窗\] 按鈕  
 當您按下**分類**按鈕，Visual Studio 的呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>在具有焦點，若要依類別排序其屬性的物件上的介面。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>實作於`IDispatch`物件，會向**屬性**視窗。  
  
 有 11 有負數值的預先定義的屬性類別。  您可以定義自訂類別，但我們建議您指派它們正數值，以便區別於預先定義的分類。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>方法會傳回適當類別的屬性值指定的屬性。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>方法會傳回字串，包含類別名稱。  您只需要提供自訂類別值的支援，因為 Visual Studio 知道標準屬性的類別目錄值。  
  
 當您按下 **Alphabetized** \] 按鈕，依名稱依字母順序顯示內容。  擷取名稱`IDispatch`根據要當地語系化的排序演算法。  
  
 當**屬性** 視窗是開啟的 **屬性** \] 按鈕會自動顯示為已選取。  環境的其他部分，會顯示相同的按鈕，然後您可以按一下它以顯示**屬性**視窗。  
  
 **屬性頁**按鈕將無法使用如果`ISpecifyPropertyPages`尚未提供所選取的物件。  屬性頁一般與方案和專案的顯示組態相關屬性，但它們是也可以是與專案項目 \(例如，在 Visual c \+ \+\) 相關聯。  
  
> [!NOTE]
>  您無法新增工具列按鈕以**屬性**使用 unmanaged 程式碼\] 視窗。  若要新增工具列按鈕，您必須建立 managed 的物件衍生自<xref:System.Windows.Forms.Design.PropertyTab>。  
  
## 請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)