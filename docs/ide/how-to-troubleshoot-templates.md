---
title: "如何：疑難排解範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 範本, 疑難排解"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：疑難排解範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果範本無法載入開發環境，您有幾個方式可找出問題所在。  
  
## 驗證 .vstemplate 檔  
 如果範本中的 .vstemplate 檔並未遵守 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本結構描述，\[**新增專案**\] 對話方塊中可能無法顯示這個範本。  
  
#### 若要驗證 .vstemplate 檔  
  
1.  尋找包含範本的 .zip 檔。  
  
2.  解壓縮這個 .zip 檔。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 \[**檔案**\] 功能表上，按一下 \[**開啟**\]，再按一下 \[**檔案**\]。  
  
4.  選取範本的 .vstemplate 檔，並按一下 \[**開啟**\]。  
  
5.  請確認 .vstemplate 檔的 XML 遵守 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本結構描述。  如需 .vstemplate 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
    > [!NOTE]
    >  若要在撰寫 .vstemplate 檔時取得 IntelliSense 支援，請將 `xmlns` 屬性 \(Attribute\) 加入至 `VSTemplate` 項目，並將「http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005」這個值指派給它。  
  
6.  儲存並關閉 .vstemplate 檔。  
  
7.  選取範本所包含的檔案，以滑鼠右鍵按一下，選取 \[**傳送到**\] 並按一下 \[**壓縮的 \(zipped\) 資料夾**\]。  您選取的檔案被壓縮在 .zip 檔中。  
  
8.  將新的 .zip 檔放置在與舊 .zip 檔相同的目錄中。  
  
9. 刪除已解壓縮的範本檔和舊範本的 .zip 檔。  
  
## 監視事件記錄檔  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會記錄處理範本 .zip 檔時發生的錯誤。  如果範本沒有如預期般出現在 \[**新增專案**\] 對話方塊中，您可以使用 \[**事件檢視器**\] 對問題進行疑難排解。  
  
#### 若要在事件檢視器中找出範本錯誤  
  
1.  在 Windows 中，按一下 \[**開始**\]、\[**控制台**\]，然後再依序按兩下 \[**系統管理工具**\] 和 \[**事件檢視器**\]。  
  
2.  在左窗格中，按一下 \[**應用程式**\]。  
  
3.  尋找 \[**來源**\] 值為 `Visual Studio - VsTemplate` 的事件。  
  
4.  按兩下範本事件，以檢視錯誤。  
  
## 請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)