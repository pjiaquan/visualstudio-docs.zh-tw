---
title: "如何：從文件移除 Managed 程式碼擴充"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "文件 [Visual Studio 中的 Office 程式開發], Managed 程式碼擴充"
  - "Managed 程式碼擴充 [Visual Studio 中的 Office 程式開發], 移除"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：從文件移除 Managed 程式碼擴充
  您可以用程式設計的方式從文件或活頁簿中移除自訂組件，這個文件或活頁簿屬於 Microsoft Office Word 或 Microsoft Office Excel 文件層級自訂的一部分。  使用者可以接著開啟文件並檢視內容，但是您加入至文件的任何自訂使用者介面 \(UI\) 都不會出現，而且程式碼也不會執行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的其中一個 RemoveCustomization 方法移除自訂組件。  您使用的方法取決於想要在執行階段移除自訂 \(也就是在 Word 文件或 Excel 活頁簿開啟時於自訂中執行程式碼\)，或是從已關閉的文件或未安裝 Microsoft Office 之伺服器上的文件移除自訂。  
  
 ![視訊的連結](~/docs/data-tools/media/playvideo.gif "視訊的連結") 如需觀看相關示範影片，請參閱[如何在 Word 文件中附加或中斷連結 VSTO 組件？](http://go.microsoft.com/fwlink/?LinkId=136782)\(英文\)。  
  
### 若要在執行階段移除自訂組件  
  
1.  在自訂程式碼中，呼叫 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> 方法 \(適用於 Word\) 或 <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> 方法 \(適用於 Excel\)。  這個方法應該只在不再需要自訂之後呼叫。  
  
     您在程式碼中呼叫這個方法的位置，取決於您使用自訂的方式。  例如，如果客戶使用自訂的功能，直到準備好將文件傳送至只需要文件本身 \(不需要自訂\) 的其他用戶端，則您可以提供一些在客戶按下時呼叫 RemoveCustomization 的 UI。  或者，如果您的自訂會在初次開啟文件時填入資料，但是自訂不會提供客戶可直接存取的任何其他功能，則您可以在自訂完成初始化文件時立即呼叫 RemoveCustomization。  
  
### 若要從已關閉文件或伺服器上的文件移除自訂組件  
  
1.  在不需要 Microsoft Office，例如主控台應用程式或 Windows Form 專案，將 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 組件的參考。  
  
2.  將下列 **Imports** 或 **using** 陳述式加入至程式碼檔的最上方。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  呼叫 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法，然後指定參數的方案文件路徑。  
  
     下列程式碼範例假設您是從桌面上的 **WordDocument1.docx** 文件中移除自訂。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  在您要移除自訂的電腦上，建置專案並執行應用程式。  電腦必須安裝 Visual Studio Visual Studio Tools for Office Runtime 安裝。  
  
## 請參閱  
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何：將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  