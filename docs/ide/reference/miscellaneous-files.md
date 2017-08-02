---
title: "其他檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.newfile"
  - "VS.OpenWith"
  - "MiscellaneousFilesProject"
helpviewer_keywords: 
  - "方案，其他檔案"
  - "組建 [Visual Studio]，其他檔案"
  - "獨立的檔案"
  - "方案總管，其他檔案"
  - "其他檔案資料夾"
  - "檔案 [Visual Studio]，容器外"
  - "檔案 [Visual Studio]，其他檔案資料夾"
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 其他檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您或許想要使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 編輯器在專案或方案之外的檔案上工作。  當方案開啟時，您可以開啟並修改檔案而毋需將它們加入方案或專案。  您想要在容器之外工作的檔案被稱為其他檔案。  其他檔案是在方案和專案之外，也不包括在組建中，而且也不能隨方案被包括在原始檔控制之下。  
  
 在容器之外開啟檔案在許多方面是很有用處的。  您或許有個檔案是在開發專案架構式方案時想要檢視的，但是它卻不是構成該方案開發整體的一部分。  常見的例子包括開發註記或說明、資料庫結構描述 \(Database Schema\) 及程式碼片段。  而且，您或許會想要建立獨立的檔案。  
  
 ![方案專案](~/ide/reference/media/projects_solutions_misc.gif "Projects\_Solutions\_Misc")  
  
 如果啟用了 \[其他檔案\] 資料夾選項的話，方案總管可以顯示這些檔案的 \[其他檔案\] 資料夾。  這個選項可從[選項對話方塊、環境、文件](../../ide/reference/documents-environment-options-dialog-box.md)中設定。  當您關閉其他檔案之後，它不會與任何特定方案或專案關聯，除非您也啟用了這種關聯的選項。  
  
 \[其他檔案\] 資料夾是將檔案表示為連結。  雖然這個資料夾不是方案的一部分，但是當您開啟方案時，上次方案關閉時為開啟的某些或所有其他檔案就會依據該資料夾的設定被重新開啟。  
  
> [!NOTE]
>  某些未顯示在 \[其他檔案\] 資料夾中的檔案就是您無法在 IDE 內修改的檔案，例如 .zip 檔和 .doc 檔。  IDE 將不會追蹤只能透過外部編輯器修改的檔案。  
  
## 在 IDE 中可用的命令  
 功能表、工具列，以及它們所包含的命令會依據您所開啟檔案的格式而變更。  例如，當您開啟文字檔時，\[文字編輯器\] 工具列就會出現，而且它的命令也可以使用。  如果您接著開啟一個 XML 結構描述檔案，則 XML 結構描述工具列便會出現。  當您在編輯 XML 結構描述時，文字編輯器工具列的命令 \(或工具列本身\) 就無法使用了。  XML 結構描述是使用中視窗，因而擁有目前選取範圍內容。  當您由專案檔案切換控制到其他檔案時，所有與專案相關的命令就會消失，只有直接與其他檔案相關的命令才會出現。  
  
## 資料夾顯示選項  
 您可以設定 \[其他資料夾\] 的顯示選項，讓這個資料夾在您沒有開啟任何其他檔案時也會出現。  方案檔案不會永久管理其他檔案的清單。  它是使用一項選擇性的功能，可以讓它記位每位使用者最近使用的 \(MRU\) 檔案清單。  
  
## 請參閱  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)   
 [選項對話方塊、環境、文件](../../ide/reference/documents-environment-options-dialog-box.md)