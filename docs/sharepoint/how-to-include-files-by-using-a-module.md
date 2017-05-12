---
title: "如何：使用模組來包含檔案"
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
  - "模組 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 模組"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：使用模組來包含檔案
  「*模組*」\(Module\) \(請勿與 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 模組混淆\) 是可讓您將檔案 \(例如 ASPX 主版頁面、文字檔或影像\) 部署至 SharePoint 的容器。  
  
 您可以選擇將檔案部署至文件庫，或者部署為文件庫外面的一般檔案 \(例如，default.aspx\)。  若要將檔案加入至文件庫，請將 `Type="GhostableInLibrary"` 指定為 **File** 元素中的屬性。  此設定會指示 SharePoint 建立一個加入至文件庫時隨檔案一起加入的清單項目。  若要部署文件庫外面的檔案，請指定 `Type="Ghostable"` 或只省略 **Type** 屬性。  
  
## 將模組加入至 SharePoint 方案  
  
#### 若要加入模組  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟或建立 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 \[**方案總管**\] 中，選擇專案節點，然後在功能表列上選擇 \[**專案**\]、\[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即開啟。  
  
3.  在 SharePoint 範本清單中，選擇 \[**模組**\] 範本，然後選擇 \[**確定**\] 按鈕。  
  
     此步驟會在名為 Module1 的專案中建立新節點。  
  
4.  在 Module1 下方，請移除 Sample.txt 檔。  
  
     Sample.txt 包含在所有新模組中 \(供示範之用\)，但並非必要。\(請注意，刪除檔案的同時會將其項目從模組的 Elements.xml 檔案中移除。\)  
  
5.  如果您想要將檔案部署至 SharePoint 中的特定資料夾結構，可以藉由選取 Module1 節點，然後在功能表列上，選擇 \[**專案**\]、\[**新的資料夾**\]，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 Module1 下方建立這些資料夾。  
  
6.  選取您要加入檔案的資料夾，然後在功能表列上選擇 \[**專案**\]、\[**加入現有項目**\]。  
  
7.  選取您要部署至 SharePoint 的一個或多個檔案，然後選擇 \[**加入**\] 按鈕。  
  
     當您將檔案加入至專案時，會自動將檔案的項目加入至模組的 Elements.xml 檔案。  部署專案時，會將檔案複製至 SharePoint 伺服器，相對於專案的根目錄來說，該位置由 **File** 元素的 **Url** 屬性 \(例如 `Url="Module1/New Folder/SomeFile.doc`\) 指定。  如果您要變更檔案的部署位置，將檔案移至 \[**方案總管**\] 中的另一個資料夾或者變更其 **Url** 設定。  
  
8.  針對您要在文件庫中顯示的任何檔案，在 Elements.xml 中於檔案項目之前加上 `Type="GhostableInLibrary"` 屬性。  例如：  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. 部署專案。  
  
     將檔案複製至 SharePoint 中指定的位置。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  