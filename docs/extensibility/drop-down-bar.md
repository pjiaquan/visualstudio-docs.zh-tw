---
title: "下拉式清單列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版下拉式清單列"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 下拉式清單列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下拉式列僅在程式碼\] 視窗的頂端，包含兩個下拉式清單中。  
  
## 下拉式列介面  
 在[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]，下拉式選單\] 列，例如包含清單的[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]項目和[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]項目成員函式，如下圖所示。  
  
 ![下拉式清單列](../extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
下拉式列  
  
 在實作下拉式列時，有四個最重要的一點的介面：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     實作這個介面可以插入下拉式列的內容。  每一個下拉式組合可以包含純文字\] 或 \[作花式文字 \(粗體、 底線或斜體\)、 可以有視窗文字的字型色彩或灰色的字型上色，並可選擇性地提供下拉式項目旁邊的小型點陣圖。  類似於<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面，點陣圖影像所提供的影像清單。  每一個下拉式組合可以有不同的影像清單。 不過，每個影像清單必須包含相同的高度的影像。  此外，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>方法，您可以為每一種組合提供工具提示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     呼叫這個介面來建立或損毀的程式碼\] 視窗的下拉式選單\] 列。  此介面也可用來判斷是否下拉式列已經附加至程式碼視窗藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法。  Call <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> for <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> from <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     呼叫此介面，直接與下拉式列。  您可以使用這個介面，以強制重新整理的下拉箭號列內容，或變更其中一個清單方塊中的選取項目。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果您已經登錄`ShowDropdownBarOption`在程式語言服務登錄機碼中，然後您的程式碼視窗管理員必須監視是否應該顯示下拉式列有關的使用者喜好設定與同步處理這個事件。  如果您沒有註冊在您語言服務機碼中，這個選項，則可以顯示或隱藏 \[鉛版\] 列上已停用**選項**功能表。  
  
## 附加到程式碼視窗的下拉式列  
 建立時，請將下拉式列附加至程式碼\] 視窗中，語言服務應該附加至下拉式列的時機<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>就會呼叫方法。  如果呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法會指示下拉式列不會尚未存在，請洽詢<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>。  若要存取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>介面，呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>指標傳給您何時您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>實作已附加。  
  
## 請參閱  
 [使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [在舊版語言服務中的導覽列的支援](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)