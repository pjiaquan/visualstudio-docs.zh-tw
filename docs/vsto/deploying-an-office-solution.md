---
title: "部署 Office 方案"
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
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發], 關於 ClickOnce 方案部署"
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發], 事件檢視器"
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發], 疑難排解"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發], 事件檢視器"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發], Office 方案 (2007 系統)"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發], 疑難排解"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 部署 Office 方案"
  - "Visual Studio 中的 Office 程式開發, 部署 Office 方案"
  - "Visual Studio 中的 Office 程式開發, 事件檢視器"
  - "Visual Studio 中的 Office 程式開發, 疑難排解"
  - "Office 方案 [Visual Studio 中的 Office 程式開發], 部署"
  - "方案 [Visual Studio 中的 Office 程式開發], 部署 Office 方案 (2007 系統)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# 部署 Office 方案
  您可以使用 ClickOnce 或 Windows Installer 部署 Office 方案。  使用 ClickOnce 可減少部署和更新您的方案所需的步驟。  如果您使用 Windows Installer，就可以控制安裝方案的方式，以及使用者安裝您的方案時安裝程式顯示的頁面。  
  
## 使用 ClickOnce 部署方案  
 當您使用 ClickOnce 部署方案時，會將方案發行至可供使用者安裝及執行的中央位置。  您可以更新方案，而不必將新的安裝程式散發給使用者。這個部署選項比較簡單，不過，您無法對使用者顯示自訂設定頁面。  此外，方案必須在擁有多位使用者的所有電腦上安裝多次。  請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 使用 Windows Installer 部署方案  
 當您使用 Windows Installer 部署方案時，會將安裝程式散發給使用者，而使用者會使用該程式安裝方案。  安裝程式可以同時為電腦的所有使用者安裝方案，而不只是目前使用者。  您還能夠透過在使用者安裝方案時顯示的選項掌控更多方面。  例如，您可以顯示授權合約或是讓使用者安裝方案的特定元件。  不過，如果您更新方案，就必須散發新的安裝程式。  請參閱 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Office 方案部署疑難排解](../vsto/troubleshooting-office-solution-deployment.md)  
  
  