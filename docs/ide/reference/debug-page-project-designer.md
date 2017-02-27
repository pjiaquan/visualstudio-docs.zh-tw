---
title: "專案設計工具、偵錯頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "專案設計工具, 偵錯頁面"
  - "專案設計工具中的 [偵錯] 頁面"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 專案設計工具、偵錯頁
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  本主題將不會套用至存放區 Windows 應用程式。  請參閱 [啟動偵錯工作階段 \(VB、C\#、C\+\+ 和 XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) 在視窗 Dev 中心。  
  
 使用 \[**專案設計工具**\] 的 \[**除錯**\] 頁面設定偵錯行為的屬性 \(在 Visual Basic 或 C\# 專案。  
  
 若要存取 \[**除錯**\] 頁面，請選取 \[**方案總管**\]\) 中的專案節點。  在 \[**專案**\] 功能表上，選擇 *ProjectName* \[**內容**\]。  當 \[**專案設計工具**\] 出現時，按一下 \[**除錯**\] 索引標籤。  
  
## 組態和平台  
 下列選項可以讓您選取要顯示或修改的組態和平台。  
  
 **組態**  
 指定要顯示或修改的組態設定。  設定可以是 \[**除錯**\] \(預設值\)， \[**版本**\] 或 \[**所有組態**\]。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
 **平台**  
 指定要顯示或修改的平台設定。  選項包括 \[**任何 CPU**\] \(預設值\)， \[**x64**\] 和 \[**x86**\]。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
## 起始動作  
 \[**起始動作**\] 會指出在進行應用程式偵錯時所要啟動的項目：專案、自訂程式、URL 或是沒有任何項目。  根據預設，這個選項設定為 \[**啟動專案。**\]。  設定 \[**除錯**\] 網頁的 \[**起始動作**\] 判斷 `StartAction` 屬性的值。  
  
 **起始專案**  
 選取這個選項會指定應該啟動可執行檔 \(針對 Windows 應用程式和主控台應用程式專案\)，當應用程式偵錯時。  預設已選取此選項。  
  
 **起始外部程式**  
 選取這個選項會指定應該啟動特定的程式，當應用程式偵錯時。  
  
 **瀏覽器起始 URL**  
 選取這個選項會指定應該存取特定的 URL，當應用程式偵錯時。  
  
## 起始選項  
 **命令列引數**  
 請在這個文字方塊中，輸入要用於偵錯的命令列引數。  
  
 **工作目錄**  
 請在這個文字方塊中，輸入啟動專案的目錄。  或者按一下瀏覽按鈕 \(**...**\) 選取目錄。  
  
 **使用遠端機器**  
 若要偵錯應用程式從遠端電腦，請選取這個核取方塊，然後輸入路徑加入至文字方塊的遠端電腦。  
  
## 啟用偵錯工具  
 **啟用 Unmanaged 程式碼偵錯**  
 這個選項會指定是否支援機器碼偵錯。  選取這個核取方塊，如果正在呼叫 COM 物件，或是啟動以機器碼撰寫並呼叫專案中，而且您必須偵錯機器碼的機器碼撰寫之使用者的程式。  若要停用 Unmanaged 程式碼偵錯，則請清除這個核取方塊。  這個核取方塊預設為清除。  
  
 **啟用 SQL Server 偵錯**  
 選取或清除此核取方塊來啟用或停用 SQL 程序的偵錯從 Visual Basic 應用程式中。  這個核取方塊預設為清除。  
  
 **啟用 Visual Studio 裝載處理序**  
 若要啟用 Visual Studio 裝載處理序，請選取這個核取方塊。  預設情況下會選取此核取方塊。  如需詳細資訊，請參閱[裝載處理序 \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md)。  
  
 若要偵錯在安全性區域，您必須啟用這個選項並 \[**偵錯以選取的使用權限集合的這個應用程式**\] 在 [進階安全性設定對話方塊](../../ide/reference/advanced-security-settings-dialog-box.md)。  
  
## 請參閱  
 [Visual Studio 偵錯](../../debugger/debugging-in-visual-studio.md)   
 [C\# 偵錯組態的專案設定](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/zh-tw/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [如何：以限制使用權限偵錯 ClickOnce 應用程式](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：建立和編輯組態](../../ide/how-to-create-and-edit-configurations.md)