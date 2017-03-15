---
title: "如何：自訂 ClickOnce 應用程式的預設 Web 網頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Publish.htm Web 網頁"
  - "ClickOnce 部署預設 Web 網頁"
  - "部署應用程式 [ClickOnce]，發行"
  - "發行，ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：自訂 ClickOnce 應用程式的預設 Web 網頁
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將 ClickOnce 應用程式發行至 Web 時，會產生 Web 網頁，與應用程式一起發行。  這個預設網頁包含應用程式名稱，以及安裝應用程式、必要條件或 MSDN 上存取說明的連結。  
  
> [!NOTE]
>  在網頁上您所看到的實際連結取決於檢視網頁所在的電腦，以及包含的必要條件。  
  
 此 Web 網頁的預設名稱為 Publish.htm；您可以使用 \[**專案設計工具**\] 變更名稱。  如需詳細資訊，請參閱[如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)。  
  
 只有在偵測到更新版本時，才會發行 Publish.htm Web 網頁。  
  
> [!NOTE]
>  \[**發行**\] 設定變更不會影響 Publish.htm 網頁，唯一例外是：最初發行之後，如果您加入或移除必要條件，則必要條件清單不再是正確。  您必須編輯必要條件連結的文字，反映變更。  
  
### 若要自訂發行 Web 網頁  
  
1.  將 ClickOnce 應用程式發行至 Web 位置。  如需詳細資訊，請參閱[如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
2.  在 Web 伺服器上，以 Visual Web 設計工具或其他 HTML 編輯器開啟 Publish.htm 檔案。  
  
3.  依需要自訂網頁，並儲存它。  
  
4.  選擇項。  若要防止 Visual Studio 覆寫自訂的發行網頁，請取消核取 \[發行選項\] 對話方塊中的 \[**每次發行之後自動產生部署網頁**\]。  
  
## 請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 ClickOnce 應用程式安裝必要條件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [如何：指定 ClickOnce 應用程式的發行頁面](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)