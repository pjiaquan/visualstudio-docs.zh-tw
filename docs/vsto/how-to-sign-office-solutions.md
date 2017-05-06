---
title: "如何：簽署 Office 方案"
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
  - "憑證 [Visual Studio 中的 Office 程式開發], Office 方案"
  - "安全性 [Visual Studio 中的 Office 程式開發], 簽署 Office 方案"
  - "簽署資訊清單 [Visual Studio 中的 Office 程式開發]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：簽署 Office 方案
  如果您簽署了方案，則可以使用憑證做為辨識項，將信任授與方案。  您可以將相同的憑證用於多個方案，而且不需要額外安全性原則更新就會信任所有方案。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果您手動使用了資訊清單產生和編輯工具 \(mage.exe 和 mageui.exe\) 編輯應用程式和部署資訊清單，則必須先重新簽署資訊清單，才能使用資訊清單。  如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](~/deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## 使用憑證進行簽署  
 憑證是一種檔案，這個檔案包含方案發行者 \(Publisher\) 的唯一金鑰和識別 \(Identity\)。  您可以向憑證授權單位購買憑證，也可以自行建立憑證並讓憑證授權單位簽署該憑證。  
  
 Visual Studio 會使用暫時憑證來簽署 Office 方案以啟用偵錯功能。  您不應該在已部署的方案中使用暫時憑證做為辨識項。  
  
#### 若要使用憑證簽署 Office 方案  
  
1.  按一下 \[**專案**\] 功能表上的 \[*SolutionName* **屬性**\]。  
  
2.  按一下 \[**簽署**\] 索引標籤。  
  
3.  選取 \[**簽署 ClickOnce 資訊清單**\]。  
  
4.  按一下 \[**從存放區選取**\] 或 \[**從檔案選取**\]，並巡覽至憑證，以尋找憑證。  
  
5.  若要確認使用的是正確憑證，請按一下 \[**其他詳細資料**\] 檢視憑證資訊。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)   
 [專案設計工具、簽署頁](../ide/reference/signing-page-project-designer.md)  
  
  