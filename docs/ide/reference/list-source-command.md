---
title: "列出原始碼命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource 命令"
  - "列出原始碼命令"
  - "ListSource 命令"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 列出原始碼命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

顯示原始程式碼的指定行。  
  
## 語法  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## 參數  
 \/Count:`number`  
 選擇項。  指定要顯示的行數。  
  
 \/Current  
 選擇項。  顯示目前的行。  
  
 \/File:`filename`  
 選擇項。  要顯示的檔案路徑。  如果沒有指定檔名，此命令顯示目前陳述式行的原始程式碼。  
  
 \/Line:`number`  
 選擇項。  顯示指定的行號。  
  
 \/ShowLineNumbers:`yes|no`  
 選擇項。  指定是否顯示行號。  
  
## 備註  
  
## 範例  
 此範例從 Form1.vb 檔案的第 4 行列出原始程式碼，並帶有可以看到的行號。  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)