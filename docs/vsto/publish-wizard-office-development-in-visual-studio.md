---
title: "發行精靈 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發]，發行精靈"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發]，發行精靈"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，發行精靈"
  - "發行精靈，Office 方案"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 發行精靈 (Visual Studio 中的 Office 程式開發)
  使用**發行精靈**若要將方案檔複製到指定的位置中，建立資訊清單的檔案，並建立安裝程式。  
  
 若要存取這個精靈，在**建置** \] 功能表中，選擇 **發行***SolutionName*。  您也可以從 \[**方案總管**\] 存取 \[**發行精靈**\]。  開啟 \[專案\] 節點中，快顯功能表，然後選擇**發行**。  
  
 下列各節將說明精靈的各個頁面。  
  
## 您要將應用程式發行至何處?  
 **指定要發行此應用程式的位置**  
 必要項。  發行位置是 \[**發行精靈**\] 從組建複製方案檔案 \(例如，資訊清單、組件、暫時憑證和其他檔案\) 的目錄。  您必須擁有此目錄的寫入權限，才能存取此目錄。  
  
 輸入該位置的磁碟路徑、 檔案共用、 FTP 站台或網站的 URL，或按一下 \[ **瀏覽**按鈕來瀏覽的位置。  路徑可以是下列格式：  
  
-   標準 Windows 格式的相對路徑或絕對路徑，例如 C:\\Deploy\\MyApplication 或 \\MyApplication。  
  
-   通用命名慣例 \(UNC\) 路徑，例如 \\\\ServerName\\MyApplication\\。  
  
-   例如 http:\/\/www.microsoft.com\/MyApplication 網站的 URL。  
  
 如果您安裝了 IIS 則預設的發行位置為 *http:\/\/localhost\/projectname\/*，如果沒有則為 publish\\ 目錄。  
  
> [!NOTE]  
>  如果目標電腦執行的是 Windows Vista，則有更多考量。  您必須是 Windows Vista 電腦上的系統管理員才能使用本機發行選項。  此外，無論是否已安裝 IIS，預設的位置固定為 *publish\\* 目錄。  
  
## 何謂使用者電腦上預設的安裝路徑？  
 安裝路徑是選擇性的。  如有需要，您可以稍後再設定安裝路徑。  如需詳細資訊，請參閱 [HOW TO：變更 Office 方案的安裝路徑](http://msdn.microsoft.com/zh-tw/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。  
  
 安裝路徑為使用者將從其中安裝自訂的目錄。  這同時也是方案將用來檢查更新的路徑。  除非此路徑與您在上一頁的 \[**指定要發行此應用程式的位置**\] 方塊中輸入的路徑相同，否則 \[**發行精靈**\] 不會將方案部署到此位置。  
  
 **從網站**  
 指定使用者在安裝方案時將使用的 URL。  
  
 **從 UNC 路徑或檔案共用**  
 指定使用者在安裝方案時將使用的 UNC 路徑。  
  
 **從 CD\-ROM 或 DVD\-ROM**  
 此選項不需要安裝路徑。  
  
 Visual Studio 不會燒錄 CD 或 DVD。  您必須將輸出手動複製到 CD 或 DVD。  
  
## 請參閱  
 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [專案設計工具、發行頁 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  