---
title: "ShowWebBrowser 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser 命令"
  - "View.ShowWebBrowser 命令"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ShowWebBrowser 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

顯示您在整合開發環境 \(IDE\) 中或 IDE 外部的 Web 瀏覽器視窗中所指定的 URL。  
  
## 語法  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## 引數  
 `URL`  
 必要項。  網站的統一資源定位器 \(URL\)。  
  
## 參數  
 \/new 或 \/開新視窗  
 選擇項。  指定顯示在 Web 瀏覽器新執行個體中的網頁。  
  
 \/ext 或 \/使用外部瀏覽器開啟  
 選擇項。  指定顯示在 IDE 外部的預設 Web 瀏覽器中的網頁。  
  
## 備註  
 **ShowWebBrowser** 命令的別名是 **navigate** 或 **nav**。  
  
## 範例  
 下列範例將在 IDE 外部的 Web 瀏覽器顯示 MSDN Online 首頁。  如果已經開啟一個 Web 瀏覽器執行個體，則使用該執行個體，否則，將啟動新的執行個體。  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)