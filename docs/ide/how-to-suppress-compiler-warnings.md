---
title: "如何：隱藏編譯器警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：隱藏編譯器警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以指定您不希望包含的一個或多個類型可以 declutter 建置記錄編譯器警告。  例如，您可以使用這個技術檢閱自動產生，當您將一般，詳細的組建記錄詳細等級或診斷時的一些，但並非所有資訊。  如需詳細等級的詳細資訊，請參閱 [如何：檢閱、儲存和設定建置記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
### 隱藏 Visual C\# 或 F\# 的特定警告。  
  
1.  在 \[**方案總管**\] 中，選取您要隱藏警告的專案。  
  
2.  在功能表列上，選擇 \[**檢視**\]\]，則 \[**屬性頁**\]。  
  
3.  選取 \[**組建**\] 頁面。  
  
4.  在 \[**隱藏警告**\] 方塊中，指定您要隱藏警告的錯誤碼，並以分號隔開，然後重建方案。  
  
### 隱藏 Visual C\+\+ 的特定警告。  
  
1.  在 \[**方案總管**\] 中，選取您要隱藏警告的專案或原始程式檔。  
  
2.  在功能表列上，選擇 \[**檢視**\]\]，則 \[**屬性頁**\]。  
  
3.  選擇 \[**組態屬性**\] 分類中，選取 \[**C\/C\+\+**\] 分類，然後選取 \[**進階**\] 頁面。  
  
4.  請執行下列其中一個步驟：  
  
    -   在 \[**停用特定警告**\] 方塊中，指定您要隱藏警告的錯誤碼，並以分號隔開。  
  
    -   在 \[**停用特定警告**\] 方塊中選取 \[**編輯**\] ，以顯示更多選項。  
  
5.  選擇 \[**OK**\] 按鈕，然後重建方案。  
  
## 隱藏 Visual Basic 的警告  
 您可以編輯專案的 .vbproj 檔案隱藏 Visual Basic 的特定的編譯器警告。  您也可以使用 [編譯頁面，專案設計工具](../ide/reference/compile-page-project-designer-visual-basic.md) 按類別隱藏警告。  如需詳細資訊，請參閱[在 Visual Basic 中設定警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
#### 隱藏 Visual Basic 的特定警告。  
  
1.  在 \[**方案總管**\] 中，選取您要隱藏警告的專案。  
  
2.  在功能表列上，選擇 \[**專案**\]\]，則 \[**卸載專案**\]。  
  
3.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選取 \[**編輯**\] *ProjectName*\[**.vbproj**\]。  
  
     專案檔在程式碼編輯器中開啟。  
  
4.  在您建置的組建組態中找出 `<NoWarn></NoWarn>` 項目。  
  
     下列範例會在偵錯組建組態的粗體文字顯示 `<NoWarn></NoWarn>` 項目在 x86 平台:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  將一或多個警告編號為 `<NoWarn>` 項目的值。  如果您指定多個警告編號，請分隔它們與逗號，，如下列範例所示。  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  儲存對 .vbproj 檔所做的變更。  
  
7.  在功能表列上，選擇 \[**專案**\]\]，則 \[**重新載入專案。**\]。  
  
8.  在功能表列上，選擇 \[**組建**\]\]，則 \[**重建方案**\]。  
  
     \[**輸出**\] 視窗不再表示警告，您指定了。  
  
 如需詳細資訊，請參閱[\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。  
  
## 請參閱  
 [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)   
 [如何：檢閱、儲存和設定建置記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)