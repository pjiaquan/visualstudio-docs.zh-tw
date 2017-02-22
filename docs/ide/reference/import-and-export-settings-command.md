---
title: "匯入和匯出設定命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "匯入和匯出設定命令"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 匯入和匯出設定命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

匯入、匯出或重設 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定。  
  
## 語法  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## 參數  
 \/export:`filename`  
 選擇項。  會將目前的設定匯出至指定的檔案。  
  
 \/import:`filename`  
 選擇項。  會匯入指定檔案中的設定。  
  
 \/reset 或 \/重設  
 選擇項。  重設目前的設定。  
  
## 備註  
 不加任何參數執行這個命令會開啟 \[**匯入和匯出設定**\] 精靈。  如需詳細資訊，請參閱 [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/zh-tw/1131fb10-35c1-42da-9cd8-91aa3235b882)。  
  
## 範例  
 下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## 請參閱  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)