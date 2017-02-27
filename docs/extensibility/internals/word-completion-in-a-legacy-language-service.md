---
title: "在舊版語言服務中的文字完成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務 [受管理的封裝 framework] IntelliSense 自動完成文字"
  - "IntelliSense、 自動完成文字"
  - "自動完成文字"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 在舊版語言服務中的文字完成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

文字完成填入遺漏的字元部分鍵入的文字。 如果只有一個可能的完成，完成字元輸入時完成這個字。 如果部分文字符合一個以上的可能性，會顯示可能的完整命令清單。 完成字元可以是任何不用於識別項的字元。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 實作步驟  
  
1.  當使用者選取 **自動完成文字** 從 **IntelliSense** \] 功能表上， <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令傳送到語言服務。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別會攔截命令，並呼叫 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> 類別則呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法，以取得可能字詞完成，然後顯示工具提示中的字詞清單使用清單 <xref:Microsoft.VisualStudio.Package.CompletionSet> 類別。  
  
     如果只有一個符合的文字， <xref:Microsoft.VisualStudio.Package.Source> 類別完成這個字。  
  
 或者，如果掃描器傳回觸發程序值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 時識別項的第一個字元型別， <xref:Microsoft.VisualStudio.Package.Source> 會偵測到這個類別，並呼叫 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason>。 在此情況下剖析器必須偵測成員選取字元，並提供成員的清單。  
  
## 啟用支援完整單字  
 若要啟用 word 完成集支援 `CodeSense` 名為參數傳遞至 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 語言套件相關聯的使用者屬性。 這會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別。  
  
 您的剖析器必須傳回宣告的清單，以回應剖析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason>, ，word 完成操作。  
  
## 在 ParseSource 方法中實作自動完成文字  
 文字完成的 <xref:Microsoft.VisualStudio.Package.Source> 類別會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 方法 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別，以取得可能字詞相符項目的清單。 您必須從衍生類別中實作清單 <xref:Microsoft.VisualStudio.Package.Declarations> 類別。 請參閱 <xref:Microsoft.VisualStudio.Package.Declarations> 類別，如需詳細資訊，您必須實作的方法。  
  
 如果清單包含只有單一的文字，然後在 <xref:Microsoft.VisualStudio.Package.Source> 類別會自動插入的部分文字取代該文字。 如果清單包含多個單字， <xref:Microsoft.VisualStudio.Package.Source> 類別會顯示工具提示清單，使用者可以從中選取適當的選擇。  
  
 也看範例 <xref:Microsoft.VisualStudio.Package.Declarations> 類別實作中的 [在舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)。