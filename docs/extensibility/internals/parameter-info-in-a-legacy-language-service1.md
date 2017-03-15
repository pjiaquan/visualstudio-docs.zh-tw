---
title: "在舊版語言 Service1 的參數資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務，方法秘訣"
  - "方法的秘訣"
  - "語言服務、 參數資訊工具提示"
  - "IVsMethodData 介面"
  - "參數資訊 (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 在舊版語言服務中的參數資訊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense 參數資訊工具提示會提供使用者有關的語言建構中的提示。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 參數資訊工具提示的運作方式  
 當您在編輯器中輸入陳述式時，VSPackage 會顯示小工具提示視窗，其中包含所輸入的陳述式的定義。 例如，如果您輸入的 Microsoft Foundation Classes \(MFC\) 陳述式 \(例如 `pMainFrame ->UpdateWindow`\) 並按左括號鍵以開始列出參數，就會顯示的定義顯示方法秘訣 `UpdateWindow` 方法。  
  
 參數資訊工具提示通常會用於搭配陳述式完成。 它們是最適合用於有參數或其他方法名稱或關鍵字之後的格式化的資訊的語言。  
  
 透過命令攔截語言服務所起始的參數資訊工具提示。 若要攔截使用者字元，您的語言服務物件必須實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面和文字檢視將指標傳遞至您 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 實作，藉由呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法中的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面。 命令篩選器攔截程式碼視窗中輸入的命令。 監視命令的資訊可以知道何時要向使用者顯示參數資訊。 您可以使用相同的命令篩選陳述式完成、 錯誤標記和其他等等。  
  
 當您輸入的關鍵字，語言服務可以提供提示時，然後語言服務建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件並呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 方法中的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 通知來顯示一個提示，IDE 的介面。 建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 物件使用 `VSLocalCreateInstance` 並指定 coclass `CLSID_VsMethodTipWindow`。`VsLocalCreateInstance` 是函式中呼叫的標頭檔 vsdoc.h 定義 `QueryService` 本機登錄，然後呼叫 `CreateInstance` 針對此物件上 `CLSID_VsMethodTipWindow`。  
  
## 提供方法秘訣  
 若要提供方法秘訣，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 方法中的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 介面，將傳遞給它的實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 介面。  
  
 當您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 會叫用類別、 其方法稱為順序如下︰  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     傳回目前文字緩衝區中的位置和相關資料的長度。 這會指示 IDE 不會遮住該資料以工具提示視窗。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     傳回方法數目 （以零為起始的索引），您想要最先顯示。 例如，如果傳回零，第一個多載的方法會一開始顯示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     傳回適用於目前內容中的多載方法的數目。 如果您傳回值大於 1，此方法，則文字檢視會顯示向上和向下箭號。 如果您按一下向下箭號時，IDE 會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 方法。 如果您按一下向上箭號時，IDE 會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     參數資訊工具提示的文字建構在數個呼叫的期間 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     傳回要顯示在方法的參數數目。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     如果您傳回方法對應數字，以您想要顯示的多載時，呼叫這個方法是，後面接著呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     您的語言服務更新編輯器\] 中顯示方法提示時，就會通知。 在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法，呼叫下列︰  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     您會收到呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 方法，當您關閉方法提示視窗。