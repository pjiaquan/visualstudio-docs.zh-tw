---
title: "XDCMake Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "XDCMake task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), XDCMake task"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# XDCMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 XML 文件工具 \(xdcmake.exe\)，此工具可將 XML 文件註解 \(.xdc\) 檔合併成 .xml 檔案。  
  
 當您在 Visual C\+\+ 原始程式碼中提供文件註解，並透過使用 [\/ doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp) 編譯器選項編譯時，會產生 .xdc 檔案。  如需詳細資訊，請參閱 [XDCMake 參考](/visual-cpp/ide/xdcmake-reference)、[XML 文件產生器工具屬性頁](/visual-cpp/ide/xml-document-generator-tool-property-pages)，以及 xdcmake.exe 的命令列說明選項 \(**\/?**\)。  
  
## 備註  
 預設情況下，xdcmake.exe 工具支援幾個命令列選項。  當指定 **\/old** 命令列選項時，可支援額外的選項。  
  
## 參數  
 下表說明 **XDCMake** 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|**AdditionalDocumentFile**|選擇性 **String\[\]** 參數。<br /><br /> 指定一或多個要合併的額外 .xdc 檔。<br /><br /> 如需詳細資訊，請參閱 [XML 文件產生器工具屬性頁](/visual-cpp/ide/xml-document-generator-tool-property-pages) 中的 **其他文件檔案**描述。  亦請參閱 xdcmake.exe 的 **\/old** 和 **\/Fs**  命令列選項。|  
|**AdditionalOptions**|選擇性 **String** 參數。<br /><br /> 在命令列指定之選項的清單。  例如 "*\/option1 \/option2 \/option\#*"。  使用這個參數指定不由任何其他 **XDCMake** 工作參數的選項。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/visual-cpp/ide/xdcmake-reference)、[XML 文件產生器工具屬性頁](/visual-cpp/ide/xml-document-generator-tool-property-pages)，以及 xdcmake.exe 的命令列說明 \(**\/?**\)。|  
|**DocumentLibraryDependencies**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true` 和目前的專案會依賴方案中的靜態程式庫 \(.lib\) 專案，則該程式庫專案的 .xdc 檔案會包含在目前專案的 .xml 檔案輸出中。<br /><br /> 如需詳細資訊，請參閱 [XML 文件產生器工具屬性頁](/visual-cpp/ide/xml-document-generator-tool-property-pages) 中的**文件庫相依性**描述。|  
|**OutputFile**|選擇性 **String** 參數。<br /><br /> 覆寫預設的輸出檔名稱。  預設名稱衍生自第一個處理的 .xdc 檔案之名稱。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/visual-cpp/ide/xdcmake-reference) 中的 **\/out:**`filename` 選項。  亦請參閱 xdcmake.exe 的 **\/old** 和 **\/Fo**  命令列選項。|  
|**ProjectName**|選擇性 **String** 參數。<br /><br /> 目前專案的名稱。|  
|**SlashOld**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，會啟用其他的 xdcmake.exe 選項。<br /><br /> 如需詳細資訊，請參閱 xdcmake.exe 的 **\/old** 命令列選項。|  
|**Sources**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義可由工作使用和發出的 MSBuild 來源檔項目陣列。|  
|**SuppressStartupBanner**|選擇性 **Boolean** 參數。<br /><br /> 如果 `true`，可防止在工作啟動時顯示版權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/visual-cpp/ide/xdcmake-reference) 中的 **\/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性 **String** 參數。<br /><br /> 指定追蹤記錄檔的目錄。|  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)