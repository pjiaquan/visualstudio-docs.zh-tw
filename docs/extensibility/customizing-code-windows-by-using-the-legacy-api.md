---
title: "使用舊版 API 的自訂程式碼視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的程式碼視窗"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 使用舊版 API 的自訂程式碼視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼視窗是支援一或多個文字檢視的文件視窗物件。 確切的程式碼視窗的功能取決於相關聯的語言服務。 在多重文件介面 \(MDI\) 模式中，程式碼視窗會是 MDI 子框架。  
  
 程式碼視窗由語言服務所控制，而且每個語言服務可以提供它自己的程式碼視窗管理員。 這可讓語言服務，將自己裝飾新增至程式碼\] 視窗中，例如波浪線、 顏色標示、 等等。 如需如何建立核心視窗的詳細資訊，請參閱 [使用舊版 API 執行個體化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)。  
  
 程式碼視窗是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 具有文字檢視和任何裝飾設置在物件的物件。 當您建立的程式碼視窗的核心程式具現化編輯器時，語言服務可以將附加 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 程式碼\] 視窗中，以做為顯示在下圖中。  
  
 ![CodeWindow 圖形](~/extensibility/media/vscodewindow.gif "vscodewindow")  
程式碼視窗  
  
 語言服務會實作程式碼視窗管理員，並負責管理裝飾，例如下拉式清單列。 程式碼的視窗呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 方法的程式碼視窗初始化期間。 下拉式清單列或按鈕列，進行這個呼叫時，可以新增語言服務 \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) 程式碼視窗。  
  
## 本章節內容  
 `Customizing Code Windows by Using the Legacy API`  
 說明如何自訂程式碼視窗使用舊版的 API。  
  
 [How to: 裝載在另一個編輯器中的編輯器](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 說明如何裝載在編輯器視窗內的第二個編輯器。  
  
 [如何: 引發事件時，編輯器會失去焦點](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 說明如何將文件檢視附加至文件資料物件。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [使用舊版 API 執行個體化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [使用舊版 API 存取 Text 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)