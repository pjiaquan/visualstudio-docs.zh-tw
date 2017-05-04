---
title: "為 Web 組件或應用程式頁面建立可重複使用的控制項 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 使用者控制項"
  - "使用者控制項 [Visual Studio 中的 SharePoint 開發], 建立"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 為 Web 組件或應用程式頁面建立可重複使用的控制項
  在 Visual Studio 中，您可以為在 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用之自訂、可重複使用的控制項。  這些控制項被稱為使用者控制項 \(User Control\)。  如需使用者控制項的詳細資訊，請參閱[ASP.NET User Controls](../Topic/ASP.NET%20User%20Controls.md)。  
  
## 建立使用者控制項  
 若要建立使用者控制項，請將 \[**使用者控制項**\] 加入至 \[**空的 SharePoint 專案**\]。  如需詳細資訊，請參閱[如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)。  
  
 加入 \[**使用者控制項**\] 項目時，Visual Studio 會在您的專案中建立一個資料夾，然後在其中加入數個檔案。  下表將針對各個檔案進行說明。  
  
|檔案|說明|  
|--------|--------|  
|使用者控制項檔案|可定義使用者控制項，  並藉由在這個檔案中加入控制項和標記的方式來設計使用者控制項。|  
|程式碼檔|包含使用者控制項的程式碼。  您可以在這個檔案中加入事件處理程式碼。|  
|設計工具程式碼檔案|包含設計工具產生的程式碼，您不能直接編輯這些程式碼。|  
  
## 設計使用者控制項  
 您可以使用 Visual Studio 中的 Visual Web Developer 設計工具，設計使用者控制項。  這個設計工具會在您開啟專案中的使用者控制項檔案並選取 \[**設計**\] 選項時顯示。  如需使用這個設計工具的詳細資訊，請參閱[Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
## 運用使用者控制項  
 在您將使用者控制項納入應用程式頁面或 Web 組件之前，這些控制項並不會出現在 SharePoint 中。  
  
 若要在應用程式頁面中包含使用者控制項，請將 [@ Register](http://msdn.microsoft.com/zh-tw/66f34922-be41-4e36-9dc8-1774d85311d1) 指示詞加入至應用程式頁面，然後在頁面上的一個或多個內容預留位置內宣告此使用者控制項。  如需如何在標準 ASP.NET 網頁上完成此工作的範例，請參閱 [How to: Include a User Control in an ASP.NET Web Page](../Topic/How%20to:%20Include%20a%20User%20Control%20in%20an%20ASP.NET%20Web%20Page.md)。  
  
 若要在 Web 組件中納入使用者控制項，請將使用者控制項加入至 Web 組件程式碼檔案中的 Web 組件 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 集合。  下列範例會將使用者控制項加入至 Web 組件的 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 集合。  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## 偵錯使用者控制項  
 若要偵錯使用者控制項，請確認使用者控制項已納入 SharePoint 專案中的應用程式頁面或 Web 組件中。  接著，您就能偵錯使用者控制項中的程式碼，其方式就像偵錯任何 Visual Studio 專案中的程式碼一樣。  
  
 當您啟動 Visual Studio 偵錯工具時，Visual Studio 就會開啟 SharePoint 網站。  
  
 在 SharePoint 中，開啟包含使用者控制項的應用程式頁面。  如果使用者控制項包含在 Web 組件中，請將該 Web 組件加入至 SharePoint 中的 \[網頁組件頁面\]。  
  
 如需偵錯 SharePoint 專案的詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何為在 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用之自訂、可重複使用的控制項。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|說明如何使用開啟專案中的網頁時出現的設計工具。|  
  
  