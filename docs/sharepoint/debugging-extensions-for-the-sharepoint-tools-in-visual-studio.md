---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio"
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
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  您可以在 Visual Studio 的實驗執行個體或一般執行個體中，偵錯 SharePoint 工具擴充功能。  如果您需要對擴充功能的行為進行疑難排解，也可以藉由修改登錄值，來顯示更多錯誤資訊，以及設定 Visual Studio 執行 SharePoint 命令的方式。  
  
## 在 Visual Studio 的實驗執行個體中偵錯擴充功能  
 若要保護您的 Visual Studio 開發環境免遭未經測試之擴充功能的意外毀損，Visual Studio SDK 提供一個稱為「*實驗執行個體*」\(Experimental Instance\) 的替代 Visual Studio 執行個體，您可以使用實驗執行個體來安裝和測試擴充功能。  您可以使用 Visual Studio 的一般執行個體來開發新的擴充功能，但是在實驗執行個體中偵錯和執行它們。  如需詳細資訊，請參閱[實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
 如果您使用 VSIX 專案來部署擴充功能，且 VSIX 專案是您方案中的啟動專案，則 Visual Studio 會在您偵錯方案時自動於實驗執行個體中安裝和執行擴充功能。  啟動專案是指偵錯含有多個專案的方案時所啟動的專案。  如需使用 VSIX 專案部署擴充功能的詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  如需啟動專案的詳細資訊，請參閱 [如何：設定啟始專案](http://msdn.microsoft.com/zh-tw/31465836-0911-48db-a5d9-e456b635e970)。  
  
 如需示範如何在 Visual Studio 的實驗執行個體中偵錯各種擴充功能類型的範例，請參閱下列逐步解說：  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## 在 Visual Studio 的一般執行個體中偵錯擴充功能  
 如果您要在 Visual Studio 的一般執行個體中偵錯擴充功能專案，請首先在該一般執行個體中安裝擴充功能。  接著，將偵錯工具附加至第二個 Visual Studio 程序。  完成之後，可以移除擴充功能，以便開發電腦不會再載入該擴充功能。  
  
#### 若要安裝擴充功能  
  
1.  關閉 Visual Studio 的所有執行個體。  
  
2.  在擴充專案的組建輸出資料夾中，開啟 .vsix 檔案（按兩下該項目或是透過開啟其捷徑功能表並選取 \[**開啟**\]）：  
  
3.  在 \[**Visual Studio 擴充功能安裝程式**\] 對話方塊中，選取您要安裝擴充功能的 Visual Studio 版本，然後按一下 \[**安裝**\] 按鈕。  
  
     Visual Studio 會將擴充檔安裝至 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*。  這個路徑中的最後三個資料夾是從擴充功能之 extension.vsixmanifest 檔案的 `Author`、`Name` 和 `Version` 項目建構而成。  
  
4.  Visual Studio 安裝這個擴充功能後，選擇 \[**關閉**\] 按鈕。  
  
#### 若要偵錯擴充功能  
  
1.  以系統管理員權限啟動 Visual Studio，並開啟擴充功能專案。  下列步驟將 Visual Studio 的這個執行個體當做「*第一個執行個體*」\(First Instance\)。  
  
2.  以系統管理員權限啟動 Visual Studio 的另一個執行個體。  下列步驟將 Visual Studio 的這個執行個體當做「*第二個執行個體*」\(Second Instance\)。  
  
3.  切換至 Visual Studio 的第一個執行個體。  
  
4.  在功能表上選擇 \[**偵錯**\]，\[**附加至處理序**\]  
  
5.  按一下 \[**可使用的處理序**\] 清單，選擇 devenv.exe。  這個項目參考 Visual Studio 的第二個執行個體，這是您要在其中對專案擴充功能進行偵錯的執行個體。  
  
6.  選擇 \[**附加**\] 按鈕。  
  
     Visual Studio 會以偵錯模式執行擴充功能專案。  
  
7.  切換至 Visual Studio 的第二個執行個體。  
  
8.  建立會載入擴充功能的新 SharePoint 專案。  例如，如果您對清單定義專案項目的擴充功能進行偵錯，請建立 \[**清單定義**\] 專案。  
  
9. 執行測試擴充功能程式碼所需的任何步驟。  
  
10. 完成對擴充功能的偵錯時，關閉 Visual Studio 的第二個執行個體。  
  
#### 若要移除擴充功能  
  
1.  在 Visual Studio 中，在功能表列上選擇 \[**工具**\]，\[**擴充功能和更新**\]。  
  
     \[**擴充功能和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選擇擴充功能的名稱，然後選擇 \[**解除安裝**\]。  
  
3.  在所顯示的對話方塊中，選擇 \[**是**\]，確認您要解除安裝擴充功能。  
  
4.  選擇 \[**重新開始**\] 按鈕以完成解除安裝。  
  
## 偵錯 SharePoint 命令  
 如果您要偵錯 SharePoint 工具擴充功能中的 SharePoint 命令，則必須將偵錯工具附加至 vssphost4.exe 處理序。  這是執行 SharePoint 命令的 64 位元主機處理序。  如需 SharePoint 命令和 vssphost4.exe 的詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
#### 若要將偵錯工具附加至 vssphost4.exe 處理序  
  
1.  依照前述指示，開始在 Visual Studio 的實驗執行個體或 Visual Studio 的一般執行個體中偵錯您的擴充功能。  
  
2.  在您執行偵錯工具的 Visual Studio 實驗執行個體中，選擇功能表上的 \[**偵錯**\]、\[**附加至處理序**\]。  
  
3.  按一下 \[**可使用的處理序**\] 清單，選擇 vssphost.exe。  
  
    > [!NOTE]  
    >  如果 vssphost.exe 未出現在清單中，您必須在執行擴充功能的 Visual Studio 執行個體中啟動 vssphost4.exe 處理序。  通常這麼做的方法，是執行一個動作，讓 Visual Studio 連接至開發電腦上的 SharePoint 網站。  例如，當您在 \[**伺服器總管**\] 視窗中展開 \[**SharePoint 連接**\] 節點下的網站連接節點 \(一個顯示網站 URL 的節點\)，或是將特定 SharePoint 專案項目 \(例如 \[**清單執行個體**\] 或 \[**事件接收器**\] 項目\) 加入至 SharePoint 專案時，Visual Studio 即會啟動 vssphost4.exe。  
  
4.  選擇 \[**附加**\] 按鈕。  
  
5.  在要偵錯的 Visual Studio 執行個體中，執行在執行您的命令時所需的步驟。  
  
## 修改登錄值以協助偵錯 SharePoint 工具擴充功能  
 在 Visual Studio 中偵錯 SharePoint 工具的擴充功能時，您可以修改登錄中的值，以利擴充功能的疑難排解。  這些值存在於 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools 機碼下。  這些值預設並不存在。  
  
 若要更順利地對 SharePoint 工具的任何擴充功能進行疑難排解，您可以建立並設定 EnableDiagnostics 值。  下表會說明此值。  
  
|值|描述|  
|-------|--------|  
|EnableDiagnostics|指定是否在 \[**輸出**\] 視窗中顯示診斷訊息的 REG\_DWORD。<br /><br /> 若要顯示診斷訊息，請將此值設定為 1。  若要停止顯示訊息，請將此值設定為 0，或刪除此值。<br /><br /> 若要將訊息寫入 SharePoint 工具擴充功能的 \[**輸出**\] 視窗，請使用 SharePoint 專案服務。  如需詳細資訊，請參閱[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。|  
  
 如果擴充功能包含 SharePoint 命令，您可以建立並設定其他值以利命令的疑難排解。  下表會說明這些值。  
  
|值|描述|  
|-------|--------|  
|AttachDebuggerToHostProcess|REG\_DWORD，指定當 vssphost4.exe 啟動時，是否立即顯示讓您將偵錯工具附加至 vssphost4.exe 的對話方塊。  如果 vssphost.exe 啟動後會立即執行您所要偵錯的命令，而您沒有足夠的時間在此命令執行前手動附加偵錯工具，這會很有用。  若要顯示對話方塊，vssphost4.exe 會在啟動時呼叫 <xref:System.Diagnostics.Debugger.Break%2A> 方法。<br /><br /> 若要啟用這個行為，請將此值設定為 1。  若要關閉這個行為，請將此值設定為 0，或刪除此值。<br /><br /> 如果您將此值設定為 1，您可能也需要增加 HostProcessStartupTimeout 值，以便有足夠的時間在 Visual Studio 預期 vssphost4.exe 指出它已順利啟動之前附加偵錯工具。|  
|ChannelOperationTimeout|指定 Visual Studio 等待執行 SharePoint 命令所需時間 \(以秒為單位\) 的 REG\_DWORD。  如果未及時執行命令，則會擲回 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>。<br /><br /> 預設為 120 秒。|  
|HostProcessStartupTimeout|指定 Visual Studio 等待 vssphost4.exe 發出成功啟動信號所需時間 \(以秒為單位\) 的 REG\_DWORD。  如果 vssphost4.exe 未及時發出成功啟動的信號，則會擲回 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>。<br /><br /> 預設為 60 秒。|  
|MaxReceivedMessageSize|指定 Visual Studio 與 vssphost4.exe 之間所傳遞之 WCF 訊息允許的大小上限 \(以位元組為單位\) 的 REG\_DWORD。<br /><br /> 預設為 1,048,576 位元組 \(1 MB\)。|  
|MaxStringContentLength|指定 Visual Studio 與 vssphost4.exe 之間所傳遞之字串允許的大小上限 \(以位元組為單位\) 的 REG\_DWORD。<br /><br /> 預設為 1,048,576 位元組 \(1 MB\)。|  
  
## 請參閱  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  