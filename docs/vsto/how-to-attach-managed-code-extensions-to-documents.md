---
title: "如何：將 Managed 程式碼擴充附加至文件"
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
  - "Managed 程式碼擴充 [Visual Studio 中的 Office 程式開發], 附加"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：將 Managed 程式碼擴充附加至文件
  您可以將自訂組件附加至現有的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿。  文件或活頁簿可以在 Microsoft Office 專案和開發工具支援在 Visual Studio 的任何檔案格式。  如需詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 若要將自訂附加至 Word 或 Excel 文件，請使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。  由於 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的設計是在未安裝 Microsoft Office 的電腦上執行，因此您可以在未與 Microsoft Office 開發工作 \(例如主控台或 Windows Form 應用程式\) 直接相關的方案中使用這個方法。  
  
> [!NOTE]  
>  如果程式碼預期收到指定文件未擁有的控制項時，自訂就會失敗。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需觀看相關示範影片，請參閱[如何在 Word 文件中附加或中斷連結 VSTO 組件？](http://go.microsoft.com/fwlink/?LinkId=136782)\(英文\)。  
  
### 若要將 Managed 程式碼擴充附加至文件  
  
1.  在不需要 Microsoft Office，例如主控台應用程式或 Windows Form 專案，將 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 和 Microsoft.VisualStudio.Tools.Applications.Runtime.dll 組件的參考。  
  
2.  將下列 **Imports** 或 **using** 陳述式加入至程式碼檔的最上方。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  呼叫靜態 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。  
  
     下列程式碼範例會使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 多載。  這項多載採用文件的完整路徑以及 <xref:System.Uri>，後者指定了您要附加至文件的自訂之部署資訊清單位置。  此範例假定名為 **WordDocument1.docx** 的 Word 文件位於桌面上，且部署資訊清單位於名為 **Publish** 的資料夾中 \(同樣位於桌面\)。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  在您要附加自訂的電腦上，建置專案並執行應用程式。  電腦必須安裝 Visual Studio Visual Studio Tools for Office Runtime 安裝。  
  
## 請參閱  
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [如何：從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  