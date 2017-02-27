---
title: "How to: 實作錯誤標記 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-錯誤標記"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# How to: 實作錯誤標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

錯誤標記 \(或紅色的波浪狀底線\) 都是最困難的文字編輯器的自訂實作。  不過，它們提供給使用者的您 VSPackage 的優點遠超過有提供兩者的成本。  錯誤標記方式來標示您的語言剖析器成員不正確的曲線或波浪紅色底線的文字。  它能協助程式設計人員以視覺化方式顯示不正確的程式碼。  
  
 用於實作紅色的波浪底線的文字標記。  一般而言，語言服務加入紅色波浪底線文字緩衝區作為背景的行程中，在閒置時間，或在背景執行緒。  
  
### 若要實作紅色的波浪狀底線功能  
  
1.  選取您想要在其下放置紅色的波浪狀底線的文字。  
  
2.  建立型別的標記`MARKER_CODESENSE_ERROR`。  如需詳細資訊，請參閱 [如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
3.  在那之後，傳入<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面指標。  
  
 此程序也可讓您透過指定的標記中建立秘訣的文字或特殊的快顯功能表。  如需詳細資訊，請參閱 [如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)。  
  
 可以顯示錯誤標記之前，都需要下列的物件。  
  
-   剖析器。  
  
-   工作提供者 \(也就是實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\)，來維護記錄的列資訊變更，以辨認為 re\-parsed 的線條。  
  
-   文字檢視篩選器，可擷取插入號變更事件\] 檢視使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\) 方法。  
  
 剖析器、 工作提供者，以及篩選器提供的基礎結構，讓可能的錯誤資料標記。  下列步驟提供的程序來顯示錯誤的資料標記。  
  
1.  正在篩選的檢視，篩選器會取得與該檢視表的資料相關聯的工作提供者的指標。  
  
    > [!NOTE]
    >  您可以使用相同的命令過濾器方法秘訣、 陳述式完成、 錯誤標記等等。  
  
2.  當篩選器接收事件，指示您已經移動到另一列時，建立任務時，檢查有錯誤。  
  
3.  工作處理常式會檢查行是否已變更。  如果是的話，它會剖析錯誤的行。  
  
4.  如果發現任何錯誤，工作提供者會建立工作項目執行個體。  這個執行個體建立環境會使用作為錯誤標記，在 \[文字\] 檢視中的文字標記。  
  
## 請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何: 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何: 使用文字標記](../extensibility/how-to-use-text-markers.md)