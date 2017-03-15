---
title: "如何：建立 ClickOnce 應用程式的檔案關聯 | Microsoft Docs"
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
  - "ClickOnce 部署, 檔案關聯"
  - "檔案關聯, ClickOnce 應用程式"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：建立 ClickOnce 應用程式的檔案關聯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可與一個或多個副檔名相關聯，如此應用程式將在使用者開啟這類型檔案時自動啟動。  將副檔名支援加入至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的方式相當直接。  
  
### 建立 ClickOnce 應用程式的檔案關聯  
  
1.  正常建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，或是使用您現有的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  
  
2.  使用文字或 XML 編輯器開啟應用程式資訊清單，例如記事本。  
  
3.  尋找 `assembly` 項目。  如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
4.  加入 `fileAssociation` 項目做為 `assembly` 項目的子系。  `fileAssociation` 項目有四個屬性：  
  
    -   `extension`：要與應用程式產生關聯的副檔名。  
  
    -   `description`：檔案類型的說明，將出現在 Windows Shell 中。  
  
    -   `progid`：以唯一方式識別檔案類型的字串，會在登錄中標記該類型。  
  
    -   `defaultIcon`：用於這個檔案類型的圖示。  圖示必須做為檔案資源加入至應用程式資訊清單中。  如需詳細資訊，請參閱 [如何：在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
     如需 `file` 和 `fileAssociation` 項目的範例，請參閱 [\<fileAssociation\> 項目](../deployment/fileassociation-element-clickonce-application.md)。  
  
5.  如果您要將多個檔案類型與應用程式產生關聯，請加入額外的 `fileAssociation` 項目。  請注意，每個項目的 `progid` 屬性都應不相同。  
  
6.  一旦完成應用程式資訊清單，請重新簽署資訊清單。  您可以使用 Mage.exe 從命令列執行這項操作。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     如需詳細資訊，請參閱[Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)。  
  
## 請參閱  
 [\<fileAssociation\> 項目](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)