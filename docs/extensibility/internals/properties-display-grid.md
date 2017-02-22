---
title: "屬性顯示格線 | Microsoft Docs"
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
  - "屬性 [Visual Studio SDK]，方格"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 屬性顯示格線
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**屬性** \] 視窗會顯示在方格內的欄位。  左邊的欄包含屬性名稱。 右欄則包含屬性值。  
  
## 使用格線  
 雙欄式\] 清單會顯示組態無關的屬性，可以在設計階段和其目前的設定變更。  請注意，可能不會顯示所有屬性。  屬性設定為隱藏，比方說，是藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>方法。  明確地說，如果要隱藏屬性具有子屬性，請參閱， [隱藏具有子屬性的屬性](../../misc/hiding-properties-that-have-child-properties.md)。  
  
 資訊推入至**屬性** \] 視窗中，IDE 會使用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>每個視窗，其中包含與相關的屬性，來顯示可選取的物件會呼叫 VSPackages **屬性**視窗。  **方案總管\] 中**的實作<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>呼叫`GetProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>取得的可瀏覽的物件階層架構中的專案階層架構中。  
  
 如果您的 VSPackage 不支援<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>，IDE 會嘗試使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>使用的值為<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>的階層架構項目或項目提供。  
  
 您的專案不需要建立 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為 IDE 提供視窗套件之實作該 \(比方說， **方案總管\] 中**\) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代表它執行。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>包含 IDE 所呼叫的三種方法：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>包含要顯示在 \[選取的物件數目**屬性**視窗。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>傳回`IDispatch`物件，選取要顯示在**屬性**視窗。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>可讓任何物件所傳回的<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>成選取的使用者。  這可讓視覺上更新選取項目顯示在 UI 中的使用者 VSPackage。  
  
 **屬性** \] 視窗中擷取資訊，從`IDispatch`物件來擷取要瀏覽的內容。  屬性瀏覽器會使用`IDispatch`詢問物件的屬性，它支援藉由查詢`ITypeInfo`，而取自`IDispatch::GetTypeInfo`。  瀏覽器再使用這些值來填入**屬性**視窗\] 和 \[變更顯示在方格中的個別屬性的值。  屬性會維護資訊內物件本身。  
  
 因為傳回的物件支援`IDispatch`，呼叫端可以取得資訊，例如物件的名稱，藉由呼叫其中一個`IDispatch::Invoke`或`ITypeInfo::Invoke`與預先定義的分派識別項 \(DISPID\)，表示您想要的資訊。  宣告的 Dispid 是負數，以確保它們不會和使用者定義的識別項衝突。  
  
 **屬性** \] 視窗會顯示不同類型的欄位取決於所選物件的特定屬性的屬性。  這些欄位包括編輯方塊、 下拉式清單及自訂編輯器對話方塊的連結。  
  
-   列舉的清單中所包含的值會由擷取<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>進行查詢以`IDispatch`。  從列舉清單取得的值可以變更在屬性方格裡，連按兩下欄位名稱，或藉由按一下值，並從下拉式清單中選取新的值。  對於有預先定義的列舉清單中的設定值的屬性，屬性名稱，在 \[屬性\] 清單中的色彩上連按兩下循環可用的選項。  對於預先定義的屬性，只有兩個選項，例如真\/假，按兩下選項之間切換的屬性名稱。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>是`false`，表示此值變更時，這個值會以粗體文字顯示。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>用來決定的值是否可以重設為原始值。  因此，您可以變更回預設值上按一下滑鼠右鍵，然後選擇如果**重設**從顯示的功能表。  否則，您必須以手動方式變更回預設值的值。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>也可以讓您以當地語系化，並隱藏顯示在設計階段屬性的名稱，但不會影響在 run time 時所顯示的屬性名稱。  
  
-   按一下省略符號 \(...\) 按鈕，便會顯示一份使用者可從中選取 \(例如色彩選擇器或 \[字型\] 清單中\) 的屬性值。  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>提供這些值。  
  
## 請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)