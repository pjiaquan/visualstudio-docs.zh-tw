---
title: "在舊版語言服務中的 [快速諮詢 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "快速諮詢，支援的語言服務 [受管理的封裝 framework]"
  - "IntelliSense、 快速諮詢"
  - "語言服務 [受管理的封裝 framework] 的 IntelliSense 快速諮詢"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 在舊版語言服務中的 [快速諮詢
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense 快速諮詢會顯示來源中識別項的相關資訊時，使用者將插入號識別項中，選取 **快速諮詢** 從 **IntelliSense** 功能表或包含滑鼠游標移識別碼。 這會導致識別碼的相關資訊會出現工具提示。 這項資訊通常包括識別項類型。 使用偵錯引擎時，這項資訊可能包括目前的值。 偵錯引擎會提供運算式的值，而語言服務處理只識別項。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [逐步解說︰ 顯示 QuickInfo 工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 受管理的封裝架構 \(MPF\) 語言服務類別會提供完整支援，來顯示 IntelliSense 快速諮詢工具提示。 您只需要是提供文字顯示，並啟用 \[快速諮詢功能。  
  
 要顯示的文字藉由呼叫取得 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器剖析原因值是 <xref:Microsoft.VisualStudio.Package.ParseReason>。 因此會告知剖析器取得的型別資訊 （或任何適合顯示快速諮詢工具提示） 中指定的位置識別碼 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件。<xref:Microsoft.VisualStudio.Package.ParseRequest> 物件是什麼傳遞給 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。  
  
 剖析器必須剖析所有項目中的位置到 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件以判斷所有的識別項的類型。 然後剖析器必須剖析要求位置取得的識別碼。 最後，剖析器必須傳遞至該識別項相關聯的工具提示資料 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，該物件可以傳回從文字以便 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 方法。  
  
## 啟用 \[快速諮詢功能  
 若要啟用 \[快速諮詢功能，您必須設定 `CodeSense` 和 `QuickInfo` 具名參數的 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。設定這些屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 和 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 屬性。  
  
## 快速諮詢功能的實作  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別會處理在 IntelliSense 快速諮詢 」 作業。 當 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別會收到 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令，類別會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法，剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason> 和時插入號位置 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令傳送。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器必須剖析到指定位置的來源和剖析在指定位置來決定如何在 \[快速諮詢工具提示中顯示的識別項。  
  
 大部分的剖析器整個原始程式檔的初始剖析作業，並將結果儲存在剖析樹狀結構。 完整剖析實行時 <xref:Microsoft.VisualStudio.Package.ParseReason> 傳遞至 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。 其他種類的剖析然後可以使用剖析樹狀結構，以取得所需的資訊。  
  
 例如，剖析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason> 可以尋找在來源位置的識別項，並查閱在剖析樹狀目錄中取得類型資訊。 此型別資訊然後傳遞至 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別，並傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 方法。