---
title: "RC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "RC task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), RC task"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 Microsoft Windows Resource Compiler 工具 \(rc.exe\)。  **RC** 工作會編譯將資料指標、圖示、點陣圖、對話方塊及字型等資源編譯成資源 \(.res\) 檔。  如需詳細資訊，請參閱[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的「資源編譯器」。  
  
## 參數  
 下表說明 RC工作的參數。  大部分的工作參數及部分參數集會對應到命令列選項。  
  
|參數|描述|  
|--------|--------|  
|**AdditionalIncludeDirectories**|選擇性 **String\[\]** 參數。<br /><br /> 將目錄加入至要搜尋 Include 檔的目錄清單。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/I** 選項。|  
|**AdditionalOptions**|選擇性 **String** 參數。<br /><br /> 命令列選擇程式範例的 **"***\/ option1 \/option2 \/option\#*" 的清單。  使用這個參數來指定不由其他任何 **RC** 工作參數代表的命令列選項。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的選項。|  
|**Culture**|選擇性 **String** 參數。<br /><br /> 指定地區設定 ID，此 ID 表示資源中使用的文化特性。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/l** 選項。|  
|**IgnoreStandardIncludePath**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，可防止資源編譯器在搜尋標頭檔或資源檔時檢查  INCLUDE 環境變數。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/x** 選項。|  
|**NullTerminateStrings**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，會以 Null終止束字串資料表中的所有字串。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/n** 選項。|  
|**PreprocessorDefinitions**|選擇性 **String\[\]** 參數。<br /><br /> 定義資源編譯器的一或多個前置處理器符號。  指定巨集符號的清單。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/d** 選項。  亦請參閱這個資料表中的 **UndefinePreprocessorDefinitions**。|  
|**ResourceOutputFileName**|選擇性 **String** 參數。<br /><br /> 指定資源檔的名稱。  指定資源檔案名稱。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/fo** 選項。|  
|**ShowProgress**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，會顯示報告編譯器進度的訊息。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/v** 選項。|  
|**Source**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義可由工作使用和發出的 MSBuild 來源檔項目陣列。|  
|**SuppressStartupBanner**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，可防止在工作啟動時顯示版權和版本號碼訊息。<br /><br /> 如需詳細資訊，請輸入 **\/?** 命令列選項，然後查看 **\/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性 **String** 參數。<br /><br /> 指定追蹤記錄檔目錄。|  
|**UndefinePreprocessorDefinitions**|取消定義前置處理器符號。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC \(RC 命令列\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(英文\) 中的 **\/u** 選項。  亦請參閱這個資料表中的 **PreprocessorDefinitions**。|  
  
## 備註  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)