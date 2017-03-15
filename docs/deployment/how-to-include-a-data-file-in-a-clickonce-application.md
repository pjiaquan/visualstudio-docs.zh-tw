---
title: "如何：在 ClickOnce 應用程式中納入資料檔案 | Microsoft Docs"
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
  - "ClickOnce 部署, 資料"
  - "資料存取, ClickOnce 應用程式"
  - "部署應用程式 [ClickOnce], 資料檔案"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：在 ClickOnce 應用程式中納入資料檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您所安裝的每個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，都在目的電腦的本機磁碟上具有資料目錄，應用程式可在其中管理自己的資料。  資料檔可以包括任何類型的檔案：文字檔、XML 檔，或甚至是 Microsoft Access 資料庫 \(.mdb\) 檔案。  下列程序會示範如何將任何類型的資料檔案，加入您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  
  
### 若要使用 Mage.exe 併入資料檔  
  
1.  將資料檔和其餘的應用程式檔案加入至應用程式目錄中。  
  
     應用程式目錄通常是標記為部署的目前版本 \(例如 v1.0.0.0\) 的目錄。  
  
2.  將您的應用程式資訊清單更新為資料檔的清單。  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     執行這項工作會在應用程式資訊清單中重新建立檔案清單，並且也會自動產生雜湊簽章。  
  
3.  在慣用的文字或 XML 編輯器中開啟應用程式資訊清單，並找到新加入檔案的 `file` 項目。  
  
     如果您加入了名為 `Data.xml` 的 XML 檔案，則此檔案看起來會類似下列程式碼範例。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  對此項目加入屬性 `type`，並對之提供 `data` 的值。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  使用金鑰組或憑證重新簽章應用程式資訊清單，然後再重新簽章部署資訊清單。  
  
     您必須重新簽章部署資訊清單，因為它的應用程式資訊清單雜湊已經變更。  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### 若要使用 MageUI.exe 併入資料檔  
  
1.  將資料檔和其餘的應用程式檔案加入至應用程式目錄中。  
  
2.  應用程式目錄通常是標記為部署的目前版本 \(例如 v1.0.0.0\) 的目錄。  
  
3.  在 \[**檔案**\] 功能表上，按一下 \[**開啟**\] 以開啟您的應用程式資訊清單。  
  
4.  選取 \[**檔案**\] 索引標籤。  
  
5.  在索引標籤頂端的文字方塊中，輸入含有應用程式檔案的目錄，然後按一下 \[**填入**\]。  
  
     資料檔就會出現在方格中。  
  
6.  將資料檔的 \[**檔案類型**\] 值設定為 \[**資料**\]。  
  
7.  儲存應用程式資訊清單，然後重新簽章檔案。  
  
     MageUI.exe 將會提示您重新簽章檔案。  
  
8.  重新簽章部署資訊清單  
  
     您必須重新簽章部署資訊清單，因為它的應用程式資訊清單雜湊已經變更。  
  
## 請參閱  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)