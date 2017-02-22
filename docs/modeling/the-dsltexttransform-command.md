---
title: "DslTextTransform 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "定義域專屬語言命令"
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# DslTextTransform 命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DslTextTransform.cmd 是指令碼呼叫 TextTransform.exe 並執行常見的選項。 您可以使用 DslTextTransformation.cmd 自動夜間組建的程式 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 專案。 如需詳細資訊，請參閱 [使用 TextTransform 公用程式產生的檔案](../modeling/generating-files-with-the-texttransform-utility.md)。  
  
 DslTextTransform.cmd 位於下列目錄︰  
  
 **\< visual Studio SDK 安裝路徑>\VisualStudioIntegration\Tools\Bin**  
  
 您可以指定下列引數做為 DslTextTransform.cmd 輸入︰  
  
-   網域模型專案的輸出目錄。  
  
-   設計工具定義專案的輸出目錄。  
  
-   文字範本檔案的位置。  
  
 DslTextTransform.cmd 處理指定的文字範本檔案，使用預設指示詞處理器和組件。 如果您建立自訂指示詞處理器，您可以建立您自己呼叫 TextTransform.exe 的批次檔。 在批次檔案中，您可以指定組件和相關聯的自訂指示詞處理器。