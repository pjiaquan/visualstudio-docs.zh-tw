---
title: "安全的部署"
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
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發], 安全性"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發], 安全性"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 安全性"
  - "Visual Studio 中的 Office 程式開發, 安全性"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 安全的部署
  當您建立 Office 方案時，開發電腦會自動更新，以允許您專案中的程式碼執行。  但是，當您部署方案時，必須使用憑證來簽署方案，或是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰，以做為信任決策的證明基礎。  如需詳細資訊，請參閱[授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 在文件層級自訂中，如果您將文件部署至網路位置，則必須同時將文件位置加入至 Office 應用程式信任中心的受信任位置清單中。  如需如何在使用者電腦上設定文件使用權限的詳細資訊，請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。  
  
## 防止 Office 方案執行程式碼  
 系統管理員可以使用登錄來防止所有的 Office 方案在電腦上執行。  當含有 Managed 程式碼擴充時開啟的 Office 方案時， Visual Studio Tools for Office Runtime 檢查名為 `Disabled` 的項目是否存在於電腦上的下列登錄機碼下列其中一項:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 若要防止 Office 方案執行程式碼，請在其中一個或兩個登錄機碼底下建立 `Disabled` 項目，然後為 `Disabled` 指定下列其中一個資料型別和值：  
  
-   REG\_SZ 或 REG\_EXPAND\_SZ，並設定為 "0" \(零\) 以外的任何字串。  
  
-   REG\_DWORD，並設定為 0 \(零\) 以外的任何值。  
  
 若要讓 Office 方案執行程式碼，請同時將兩個 `Disabled` 項目設定為 0 \(零\)，或是刪除這些登錄項目。  
  
## 請參閱  
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [準備電腦來執行或裝載 Office 方案](http://msdn.microsoft.com/zh-tw/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  