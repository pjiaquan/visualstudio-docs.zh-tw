---
title: "使用在 Office 方案概觀中的本機資料庫檔案"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 本機"
  - "本機資料 [Visual Studio 中的 Office 程式開發]"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 資料"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 使用在 Office 方案概觀中的本機資料庫檔案
  您在 Office 方案中包含資料庫檔案，例如 SQL Server Express \(.mdf\) 檔案或 Microsoft Office Access \(.mdb\) 檔案。  這可讓使用者在不必維護集中式資料庫時，進行本機資料庫的維護，例如，用於單一電腦的本機庫存方案。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 將資料庫檔案匯入專案  
 若要將資料庫檔案匯入您的專案，請使用 \[**資料來源組態精靈**\]，根據資料庫檔案建立資料來源。  該精靈會將資料庫檔案和具型別資料集加入專案。  
  
## 部署資料庫檔案  
 \[**資料來源組態精靈**\] 使用相對路徑建立與本機資料庫檔案的連線。  如果您維護檔案的相對位置，這可以讓您將方案從一部電腦複製到另一部電腦。  
  
 如果要將方案部署至伺服器，然後將文件傳送給每位使用者，則必須手動傳送資料庫檔案，並將檔案安裝在相對於文件的同一位置。  這意味著使用者無法將文件移至其電腦上的新位置，除非使用者同時移動資料庫檔案。  
  
## 本機資料庫檔案和快取資料集  
 在 Microsoft Office Excel 和 Microsoft Office Word 的文件層級方案中，您可以快取文件中的資料集，方法是以屬性 \(Attribute\) <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 標示資料集執行個體 \(Instance\)。  使用 \[**資料來源組態精靈**\] 將資料庫檔案加入專案時，會自動將具型別資料集加入專案。  因為資料已位於使用者的本機電腦，所以幾乎不需要將 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 套用至這個資料集。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [快取資料](../vsto/caching-data.md)  
  
  