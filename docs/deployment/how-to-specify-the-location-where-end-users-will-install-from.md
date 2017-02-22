---
title: "如何：指定位置讓使用者從此處執行安裝作業 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "部署應用程式 [ClickOnce], 指定安裝 URL"
  - "安裝 URL 屬性"
  - "安裝, 指定安裝 URL"
  - "URL, 指定安裝 URL"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：指定位置讓使用者從此處執行安裝作業
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，使用者要下載和安裝應用程式而前往的位置，不一定就是最初發行應用程式的位置。  例如，在某些組織中，開發人員可能將應用程式發行至開發用伺服器 \(Staging Server\)，再由系統管理員將應用程式移至 Web 伺服器。  
  
 在這個情況下，您可以使用 `Installation URL` 屬性，指定使用者將前往 Web 伺服器，下載應用程式。  這是必要的，應用程式資訊清單才會知道到哪裡尋找更新檔。  
  
 在 \[**專案設計工具**\] 的 \[**發行**\] 頁面上，可以設定 `Installation URL` 屬性。  
  
 **注意**：也可以使用 \[**發行精靈**\] 設定 `Installation URL` 屬性。  如需詳細資訊，請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
### 若要指定安裝的 URL  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  在 \[安裝的 URL\] 欄位中，使用完整的 URL \(格式為 http:\/\/www.microsoft.com\/ApplicationName\) 或 UNC 路徑 \(格式為 \\\\Server\\ApplicationName\)，輸入安裝位置。  
  
## 請參閱  
 [如何：指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)