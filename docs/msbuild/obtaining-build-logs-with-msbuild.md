---
title: "使用 MSBuild 取得組建記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild，記錄"
  - "記錄 [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 使用 MSBuild 取得組建記錄檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

透過使用 MSBuild 的參數，您可以指定要建置資料要檢閱，以及您是否要將組建資料至一個或多個檔案。  您也可以指定自訂記錄器收集組建資料。  如需 MSBuild 這個主題並未涵蓋的命令列參數的詳細資訊，請參閱 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  使用 Visual Studio IDE 中，如果您建立專案，您可以檢閱組建記錄疑難排解這些組建。  如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
## 設定詳細程度  
 當您建立專案使用 MSBuild 時，如果沒有指定詳細程度，下列資訊會顯示在輸出記錄:  
  
-   錯誤、被分類為高度和重要的警告訊息。  
  
-   某些狀態事件。  
  
-   組建的摘要。  
  
 使用 **\/verbosity** \(**\/v**\) 參數，您可以控制多少資料出現在輸出記錄。  如需疑難排解，請使用詳細等級 `detailed` \(`d`\) 或 `diagnostic` \(`diag`\)，提供大部分的資訊。  
  
 建置流程可能較慢，當您將 **\/verbosity** 設為 `detailed` 和慢，當您將 **\/verbosity** 設為 `diagnostic`。  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## 儲存檔案的建置記錄  
 您可以使用 **\/fileLogger** \(**fl**\) 參數儲存組建資料至檔案。  下列範例會將組建資料至名為 `msbuild.log`的檔案。  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 在下列範例中，記錄檔會命名為，則為 `MyProjectOutput.log`，而且記錄檔輸出的詳細等級設定為 `diagnostic`。  使用 **\/filelogparameters** \(`flp`\) 參數，請指定這兩個設定。  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 如需詳細資訊，請參閱[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)。  
  
## 儲存記錄檔輸出到多個檔案。  
 下列範例將整個記錄至 `msbuild1.log`，錯誤和警告對 `JustErrors.log`為 `JustWarnings.log`。  這個範例使用三個檔案都使用檔案編號。  檔案號碼在 **\/fl** 和 **\/flp** 參數指定之後 \(例如， `/fl1` 和 `/flp1`\)。  
  
 檔案 2 和 3 的 **\/filelogparameters** \(`flp`\) 參數在每個檔案指定如何命名每個檔案和如何包含。  名稱不能為檔案指定 1，因此，使用 `msbuild1.log` 的預設名稱。  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 如需詳細資訊，請參閱[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)。  
  
## 使用自訂記錄器  
 若想撰寫自己的記錄器，您可以撰寫一個實作 <xref:Microsoft.Build.Framework.ILogger> 介面的 Managed 型別。  您可以使用自訂記錄器，例如，透過電子郵件傳送的建置錯誤，記錄到資料庫或記錄至 XML 檔案。  如需詳細資訊，請參閱[組建記錄器](../msbuild/build-loggers.md)。  
  
 使用 **\/logger** 參數，可以在 MSBuild 命令列，您可以指定自訂記錄器。  您也可以使用 **\/noconsolelogger** 參數來停用預設主控台記錄器。  
  
## 請參閱  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [組建記錄器](../msbuild/build-loggers.md)   
 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)   
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)