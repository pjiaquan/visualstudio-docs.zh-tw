---
title: "擴充獨立的 Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell，隔離模式"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 擴充獨立的 Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以擴充 Visual Studio 隔離 shell 獨立的 shell 應用程式中加入 VSPackage、 Managed Extensibility Framework \(MEF\) 元件的組件或泛型的 VSIX 專案。  
  
> [!NOTE]
>  下列步驟 presuppose 您已使用 Visual Studio Shell 外掛式主控專案範本建立基本的獨立的 shell 應用程式。 如需這個專案範本的詳細資訊，請參閱 [逐步解說: 建立基本的獨立的 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 \[新增專案\] 對話方塊的三個不同位置：  
  
1.  在 **Visual Basic**, ，**擴充性**。 專案的預設語言為 Visual Basic。  
  
2.  在 **Visual C\#**, ，**擴充性**。 專案的預設語言為 C\#。  
  
3.  在 **其他專案類型**, ，**擴充性**。 專案的預設語言為 C\+\+。  
  
## 加入 VSPackage  
 您可以加入 VSPackage 獨立的 shell 應用程式。 下列步驟示範如何建立一個將功能表命令。  
  
#### 若要新增新的 VSPackage  
  
1.  新增名為 Visual Studio Package 專案 `MenuCommandsPackage`。  
  
2.  在 **基本 VSPackage 資訊** 精靈頁面設定 **公司名稱** 至 `Fabrikam` 和 **VSPackage 名稱** 到 `FabrikamMenuCommands`。 選擇 \[**下一步**\] 按鈕。  
  
3.  在下一個頁面上，選取 **功能表命令** ，然後選擇 \[ **下一步**。  
  
4.  在下一個頁面上，設定 **命令名稱** 至 `Fabrikam Command` 和 **命令 ID** 至 `cmdidFabrikamCommand`, ，然後選擇 \[ **下一步**。  
  
5.  在 **選取測試的專案選項** 頁面上，清除測試選項\]，然後選擇 **完成** \] 按鈕。  
  
6.  在 ShellExtensionsVSIX 專案中，開啟 source.extension.vsixmanifest 檔案。  
  
     **資產** 部分應該包含 VSShellStub.AboutBoxPackage 專案的項目。  
  
7.  選擇 \[新增\] 按鈕。  
  
8.  在 **加入新資產** 視窗，請在 **類型** 清單中，選取 **Microsoft.VisualStudio.VsPackage**。  
  
9. 在 **來源** 清單中，請確定 **目前方案中的專案** 已選取。 在 **專案** 清單方塊中，選取 **MenuCommandsPackage**。  
  
10. 儲存並關閉檔案。  
  
11. 重建方案並開始偵錯獨立的 shell。  
  
12. 在功能表列上選擇 \[ **工具** 功能表，然後 **Fabrikam 命令**。  
  
     應該會出現訊息方塊。  
  
13. 停止偵錯應用程式。  
  
## 加入 MEF 元件組件  
 下列步驟顯示如何將 MEF 元件組件加入至您的獨立的 shell 應用程式。  
  
#### 若要新增為 MEF 元件  
  
1.  在 **加入新的專案** 對話方塊的 \[ **Visual C\#**, ，**擴充性**, ，使用 **編輯器邊界** 範本加入專案。 將它命名為 `ShellEditorMargin`。  
  
2.  在 ShellExtensionsVSIX 專案中，開啟 \[設計\] 檢視中，程式碼檢視中的 Source.extension.vsixmanifest 檔案。  
  
3.  在 `Asset` 區段中，選擇 **加入內容**。  
  
4.  在 **加入新資產** 視窗，請在 **類型** 清單中，選取 **Microsoft.VisualStudio.MefComponent**。  
  
5.  在 **來源** 清單中，請確定 **目前方案中的專案** 已選取。 在 **專案** 清單方塊中，選取 **ShellEditorMargin**。  
  
6.  儲存並關閉檔案。  
  
7.  重建方案並開始偵錯獨立的 shell。  
  
8.  開啟文字檔案。  
  
     包含文字"Hello world ！"綠色邊界 應該會顯示在文字檔案\] 視窗的底部。  
  
9. 停止偵錯應用程式。  
  
## 加入泛型 VSIX 專案  
  
#### 若要加入一般的 VSIX 專案  
  
1.  在 **加入新的專案** 對話方塊的 \[ **Visual C\#**, ，**擴充性**, ，使用 **VSIXProject** 範本加入專案。 將它命名為 `EmptyVSIX`。  
  
2.  在 ShellExtensionsVSIX 專案中，開啟 Source.extensions.vsixmanifest 檔案在設計檢視中，程式碼檢視。  
  
3.  在 `Assets` 區段中，選擇 **新增**。  
  
4.  在 **加入新資產** 視窗，請在 **類型** 清單中，選取您想要新增的內容類型。  
  
5.  在 **來源**, ，請確定 **目前方案中的專案** 選項。 在清單方塊中，選取您的 VSIX 專案的名稱。  
  
6.  儲存並關閉檔案。  
  
7.  如果這個專案會包含已編譯程式碼，您必須編輯專案，以便在輸出中包含組件。  
  
    1.  卸載 VSIX 專案，並開啟專案檔案。  
  
    2.  在第一個 `<PropertyGroup>` 區塊中，變更的值 `<CopyBuildOutputToOutputDirectory>` 到 `true`。  
  
    3.  儲存並重新載入專案。  
  
8.  建置並執行方案。  
  
## 請參閱  
 [逐步解說: 建立基本的獨立的 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)