---
title: "如何：建立 SharePoint Web 組件 | Microsoft Docs"
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
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 加入"
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 建立"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：建立 SharePoint Web 組件
  您可以將 \[**Web 組件**\] 項目加入至任何 SharePoint 專案，接著為Web 組件或使用設計工具來編輯程式碼檔，以建立與自訂 Web 組件。  如需詳細資訊，請參閱[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
### 若要建立 SharePoint Web 組件  
  
1.  開啟或建立 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 \[**方案總管**\] 中選取SharePoint專案節點，然後選擇 \[**專案**\] 中的 \[**加入新項目**\]。  
  
3.  在\[ **加入新項目**\]對話方框中展開**SharePoint**節點，接著選取**2010**節點  
  
4.  在 SharePoint 範本清單中，選取 \[**Web 組件**\]。  
  
5.  在 \[**名稱**\] 方塊中指定Web組件的名稱，然後選擇 \[**加入**\] 按鈕。  
  
     \[**Web組件**\] 項目就會出現在 \[方案總管\] 中。  如需Web組件內檔案的詳細資訊，請參閱 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
6.  在 \[**方案總管**\] 中，開啟您建立的 Web 組件的程式碼檔案。  
  
     例如，如果 Web 組件名稱為 WebPart1，開啟 WebPart1.vb \(在 Visual Basic 中\) 或 WebPart1.cs \(在 C\# 中\)，  
  
7.  將控制項加入至程式碼檔案的 <xref:System.Web.UI.Control.CreateChildControls%2A> 方法。  
  
     如需範例，請參閱 [逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)。  
  
## 請參閱  
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  