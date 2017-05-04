---
title: "如何：使用 MSBuild 目標自訂 SharePoint 方案套件 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 開發, 套件"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：使用 MSBuild 目標自訂 SharePoint 方案套件
  您可以在命令列使用 MSBuild 目標，自訂 Visual Studio 建立 SharePoint 封裝檔案 \(.wsp\) 的方式。  例如，您可以自訂 MSBuild 屬性來改變封裝中繼目錄，以及自訂指定列舉檔案的 MSBuild 項目群組。  
  
## 自訂和執行 MSBuild 目標  
 如果您自訂 BeforeLayout 和 AfterLayout 目標，您可在套件配置之前執行工作，例如加入、移除，或將封裝的修改檔案。  
  
#### 若要自訂 BeforeLayout 目標  
  
1.  開啟編輯器 \(例如記事本\)，然後加入下列程式碼。  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     這個範例在封裝目標前會顯示訊息。  
  
2.  將檔案命名為 **CustomLayout.SharePoint.targets**，然後將其儲存在 SharePoint 專案的資料夾。  
  
3.  開啟專案，開啟其捷徑功能表，然後選擇 \[**卸載專案**\]。  
  
4.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**編輯** *ProjectName***.vbproj**\] 或 \[**編輯** *ProjectName***.csproj**\]。  
  
5.  在專案檔的結尾附近 `Import` 行後面，加入下列程式碼。  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  儲存並關閉專案檔。  
  
7.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**重載專案**\]。  
  
 當您發行專案，訊息會顯示在封裝開始前的輸出。  
  
#### 若要自訂 AfterLayout 目標  
  
1.  在功能表列上，選取 \[**檔案**\]、\[**開啟**\]、\[**檔案**\]。  
  
2.  在 \[**開啟檔案**\] 對話方塊中，巡覽至專案資料夾，選取 CustomLayout.target 檔案，然後選擇 \[**開啟**\] 按鈕。  
  
3.  緊接在 `</Project>` 標籤之前，加入下列程式碼：  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     在此目標封裝之後，此範例會顯示訊息。  
  
4.  儲存並關閉目標檔案。  
  
5.  重新啟動 Visual Studio，然後開啟專案。  
  
 當您發行專案時， BeforeLayout 訊息會在包裝啟動前顯示，而 AfterLayout 訊息會在包裝完成之後顯示。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  