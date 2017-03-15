---
title: "如何：指定偵錯的 .NET Framework 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, 指定偵錯版本"
  - "偵錯 [Visual Studio], 指定 .NET Framework 版本"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：指定偵錯的 .NET Framework 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 偵錯工具支援偵錯舊版 Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 以及最新的版本。  如果從 Visual Studio 啟動應用程式，偵錯工具一定可以為正在偵錯的應用程式識別正確的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  如果應用程式已經在執行且您使用 \[**附加至**\]，偵錯工具就不一定能夠識別舊版的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  如果發生這種情況，就會出現錯誤訊息：  
  
 偵錯工具對於應用程式所要使用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本做了不正確的假設。  
  
 在這些不常見的情況中，您可以設定登錄機碼指示偵錯工具要使用的版本。  
  
### 若要指定偵錯的 .NET Framework 版本  
  
1.  查詢目錄 Windows\\Microsoft.NET\\Framework 以尋找電腦上已安裝的 .NET Framework 版本。  版本號碼看起來如下所示：  
  
     `V1.1.4322`  
  
     識別正確的版本編號然後記下來。  
  
2.  啟動 \[**登錄編輯程式**\] \(regedit\)。  
  
3.  在 \[**登錄編輯程式**\] 中開啟 HKEY\_LOCAL\_MACHINE 資料夾。  
  
4.  巡覽至：HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     如果此機碼不存在，請以滑鼠右鍵按一下 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine，然後按一下 \[**新增機碼**\]。  將新增機碼命名為 `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。  
  
5.  在巡覽至 {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} 後，查詢 \[**名稱**\] 欄位然後尋找 CLRVersionForDebugging 機碼。  
  
    1.  如果機碼不存在，請以滑鼠右鍵按一下 {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}，然後按一下 \[**新增字串值**\]。  然後以滑鼠右鍵按一下新的字串值，按一下 \[**重新命名**\]，再輸入 `CLRVersionForDebugging`。  
  
6.  按兩下 \[**CLRVersionForDebugging**\]。  
  
7.  在 \[**編輯字串**\] 方塊的 \[**值**\] 方塊中輸入 .NET Framework 版本編號。  例如：V1.1.4322。  
  
8.  按一下 \[**確定**\]。  
  
9. 關閉 \[**登錄編輯程式**\]。  
  
     如果在開始偵錯時仍然出現錯誤訊息，請確認已經在登錄中正確輸入版本編號。  同時確認是使用 Visual Studio 支援的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  偵錯工具與 .NET Framework 的最新版本和舊版相容，但是不一定與未來的版本相容。  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)