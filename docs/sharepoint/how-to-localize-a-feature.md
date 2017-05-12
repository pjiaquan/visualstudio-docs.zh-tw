---
title: "如何：當地語系化功能"
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
  - "功能 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 當地語系化"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：當地語系化功能
  根據預設，功能標題和描述會使用硬式編碼字串值。  若要當地語系化功能標題和描述，請將字串取代為參考當地語系化資源的運算式。  
  
## 當地語系化功能  
  
#### 若要當地語系化功能  
  
1.  在 \[**方案總管**\] 中，開啟 \[**Feature1**\] 節點的捷徑功能表，然後選擇 \[**加入功能資源**\]。  
  
2.  在 \[**加入資源**\] 對話方塊中，從清單中選取 \[**固定語言**\] 做為預設語言功能資源檔的文化特性。  
  
3.  針對每種當地語系化的語言重複先前步驟，同時針對當地語系化的功能資源檔選取您所選擇的語言。  
  
     建立不同的功能資源檔：一個為預設語言，另一個為要支援的每種當地語系化語言。  
  
4.  開啟 \[資源編輯器\] 中的每個資源檔，然後輸入所有 ID 字串及其值。  
  
     例如，在預設功能資源檔中，輸入值為 \[My Feature Title\] 的 ID 字串 ，並輸入值為 \[My Feature Description\] 的第二個 ID 字串 。  針對每個當地語系化的資源檔，使用預設功能資源中所使用的相同 ID 字串 ，但要輸入當地語系化的值字串。  
  
5.  在您輸入所有資源值之後，請開啟功能的捷徑功能表 \(例如， Feature1.feature\)，然後選擇 \[**檢視表設計工具**\] 以開啟功能設計工具中的功能。  
  
6.  若要將功能中的 \[**標題**\] 和 \[**描述**\] 欄位當地語系化，請使用下列格式在方塊中輸入值：  
  
     `$Resources:` *String ID*  
  
     例如，在 \[**功能標題**\] 方塊中輸入 $Resources:Title，並在 \[**功能描述**\] 方塊中輸入 $Resources:Description。  
  
     ID 字串必須與資源檔中所使用的字串相符。  
  
7.  選擇 F5 鍵以建置和執行應用程式。  
  
8.  在 SharePoint 中，開啟 \[**網站動作**\] 功能表，選擇 \[**網站設定**\]，然後在 \[**網站動作**\] 區段中，選擇 \[**管理網站功能**\] 連結。  
  
9. 在 SharePoint 中，變更預設的顯示語言。  
  
     當地語系化的功能標題和描述便會出現在應用程式中。  若要顯示當地語系化資源，SharePoint 伺服器必須已安裝符合資源檔之文化特性的語言套件。  
  
## 請參閱  
 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)  
  
  