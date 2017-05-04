---
title: "URL 選擇器對話方塊 (Visual Studio 中的 SharePoint 開發) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 設計工具"
  - "Visual Studio 中的 SharePoint 開發, URL 選擇器"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# URL 選擇器對話方塊 (Visual Studio 中的 SharePoint 開發)
  您可以使用 URL 選擇器對話方塊，選取位於您專案或本機伺服器中正在執行 SharePoint 的檔案，例如主版頁面檔案或影像檔。  
  
 當您可以選擇檔案設定屬性時，便會顯示這個對話方塊。  在 \[**屬性**\] 視窗中，選擇各屬性旁邊的省略符號按鈕 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\)，即可開啟這個對話方塊。  當您在設計工具的 \[**原始碼**\] 檢視中指派特定屬性的值時，省略符號按鈕也會以 IntelliSense 提示的形式出現。  
  
## UIElement 清單  
 **專案資料夾**  
 顯示專案中或正在執行 SharePoint 的本機伺服器上定義之資料夾的清單。  選擇展開按鈕，以顯示子資料夾。  
  
 展開 \[**專案**\] 節點以選取專案中的檔案。  若要以可選取的形式出現在對話方塊中，專案中的檔案必須符合下列準則：  
  
-   檔案必須包含於對應資料夾中。  
  
-   檔案必須已加入至方案套件。  
  
-   檔案不能位於其他專案中。  
  
 如果您要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。  
  
 展開 \[**伺服器**\] 節點，選擇本機伺服器上正在執行 SharePoint 的檔案。  若要以可選取的形式出現在對話方塊中，這些檔案必須符合下列準則：  
  
-   檔案必須位於下列其中一個對應資料夾中：**Images**、**Layouts** 或 **ControlTemplates**。  
  
-   檔案不能位於 SharePoint 內容資料庫中。  
  
 如果您要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。  
  
 **資料夾內容**  
 顯示所選資料夾中的檔案清單。  選取檔案並按下 \[**確定**\] 按鈕，以關閉對話方塊，並將您的選擇傳送至呼叫它的處理序。  
  
 **檔案類型**  
 可讓您為正在執行的工作選取適當的檔案清單。  
  
## 請參閱  
 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  