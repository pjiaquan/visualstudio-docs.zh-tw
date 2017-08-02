---
title: "支援多個文件檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，自訂的多個文件檢視"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 支援多個文件檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以藉由編輯器中建立個別的文件資料和文件檢視物件提供文件的多個的檢視。  一些其他的文件檢視很有用的情形如下：  
  
-   新的視窗支援： 您要讓您提供的相同類型而定，兩個或多個檢視的編輯器，以便已經在編輯器中開啟的視窗的使用者可以開啟新視窗中選取**開新視窗** 指令從 **視窗**功能表。  
  
-   表單和程式碼檢視支援： 您想要您的編輯器，以提供型別不同的檢視。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]比方說，提供 \[表單檢視\] 與 \[程式碼\] 檢視。  
  
 如需詳細資訊，請參閱 CreateEditorInstance 中的程序 Visual Studio 的封裝範本所建立的自訂編輯器專案中的 EditorFactory.cs 檔案。  如需有關此專案的詳細資訊，請參閱[逐步解說: 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
## 正在同步化檢視  
 當您實作多個檢視時，文件的資料物件就會有責任保護與資料進行同步處理的所有檢視。  您可以使用事件處理介面，在<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>與資料同步處理多個檢視。  
  
 如果您不使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>用於同步化多重檢視，然後您就必須實作自己的事件系統，以處理文件的資料物件所做的變更物件。  若要保持最新的多個檢視，您可以使用不同等級的細節。  使用的最大的資料粒度設定，當您在某個檢視中輸入其他的檢視會立即更新。  使用最小的資料粒度，其啟動之前，不會更新其他檢視。  
  
## 判斷是否文件資料，是已經開啟  
 在整合式的開發環境 \(IDE\) 中執行文件表格 \(RDT\) 中，可以幫助追蹤是否為文件的資料已經開啟，如下圖所示。  
  
 ![DocDataView 圖形](~/extensibility/media/docdataview.gif "Docdataview")  
多重檢視  
  
 預設情況下，每個檢視 \(文件檢視物件\) 包含在其本身視窗外框 \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\)。  如先前所述，然而，文件資料可以顯示多個檢視中。  若要啟用這種情況，Visual Studio 會檢查以判斷是否有問題的文件已經在編輯器中開啟 RDT。  當 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>若要建立編輯器\] 中，為非 NULL 值傳回的`punkDocDataExisting`參數會指出文件已經被另一個編輯器開啟。  如需有關如何 RDT 函式中，請參閱[執行中的文件表格](../extensibility/internals/running-document-table.md)。  
  
 在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>的實作中，檢查文件的資料物件中傳回`punkDocDataExisting`來決定文件資料是否適用於您的編輯器。  \(比方說，只有 HTML 資料應該會顯示由 HTML 編輯器。\) 如果適當，編輯器工廠應該為資料提供第二個檢視。  如果`punkDocDataExisting`參數不是`NULL`，則可能是文件的資料物件是開啟在另一個編輯器中，或者，更有可能，文件資料已經被不同的檢視，具有相同的編輯器開啟。  在編輯器工廠不支援的其他編輯器中開啟文件資料時，Visual Studio 無法開啟編輯器工廠。  如需詳細資訊，請參閱 [如何︰ 附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)。