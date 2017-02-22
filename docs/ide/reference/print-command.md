---
title: "列印命令 | Microsoft Docs"
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
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print 命令"
  - "列印命令"
  - "列印方法"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 列印命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

評估運算式或顯示指定的文字。  
  
## 語法  
  
```  
Debug.Print text  
```  
  
## 引數  
 `text`  
 必要項。  要評估的運算式或要顯示的文字。  
  
## 備註  
 您可以使用問號 \(?\) 做為此命令的別名。  所以，例如，命令  
  
```  
>Debug.Print expA  
```  
  
 也可以寫入。  
  
```  
>? expA  
```  
  
 此命令的這兩種版本都會傳回運算式 `expA` 目前的值。  
  
## 範例  
  
```  
>Debug.Print varA  
```  
  
## 請參閱  
 [評估陳述式命令](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)