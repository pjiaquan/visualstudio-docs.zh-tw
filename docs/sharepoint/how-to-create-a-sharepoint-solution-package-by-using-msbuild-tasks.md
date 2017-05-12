---
title: "如何：使用 MSBuild 工作建立 SharePoint 方案套件"
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
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：使用 MSBuild 工作建立 SharePoint 方案套件
  您可以在開發電腦上使用命令列 MSBuild 工作建置、清除和驗證 SharePoint 封裝 \(.wsp\)。  您也可以在組建電腦上使用 Team Foundation Server，以使用這些命令來自動化建置流程。  
  
## 建置 SharePoint 封裝  
  
#### 若要建置 SharePoint 封裝  
  
1.  在 Windows \[**啟動**\] 功能表上，選擇 \[**所有程式**\]、\[**附屬**\]、 \[**命令提示字元**\]。  
  
2.  將目錄變更為 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令，建立專案的封裝。  將 *ProjectFileName* 取代為專案的名稱。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     例如，您可以執行下列其中一個命令來封裝名為 ListDefinition1 的 SharePoint 專案。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## 清除 SharePoint 封裝  
  
#### 若要清除 SharePoint 封裝  
  
1.  開啟命令提示字元視窗。  
  
2.  將目錄變更為 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令，清除專案的封裝。  將 *ProjectFileName* 取代為專案的名稱。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     例如，您可以執行下列其中一個命令來清除名為 ListDefinition1 的 SharePoint 專案。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## 驗證 SharePoint 封裝  
  
#### 若要驗證 SharePoint 封裝  
  
1.  開啟命令提示字元視窗。  
  
2.  將目錄變更為 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令，驗證專案的封裝。  將 *ProjectFileName* 取代為專案的名稱。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     例如，您可以執行下列其中一個命令來驗證名為 ListDefinition1 的 SharePoint 專案。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## 設定 SharePoint 封裝中的屬性  
  
#### 若要設定 SharePoint 封裝中的屬性  
  
1.  開啟命令提示字元視窗。  
  
2.  將目錄變更為 SharePoint 專案所在的目錄。  
  
3.  輸入下列命令，設定專案封裝中的屬性。  將取代為 *PropertyName* 您要設定的屬性。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     例如，您可以執行下列命令來設定警告層級。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## 請參閱  
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  