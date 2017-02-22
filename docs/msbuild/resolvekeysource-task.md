---
title: "ResolveKeySource Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ResolveKeySource task [MSBuild]"
  - "MSBuild, ResolveKeySource task"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveKeySource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

決定強式名稱 \(Strong Name\) 金鑰來源。  
  
## 工作參數  
 下表說明 `ResolveKeySource` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AutoClosePasswordPromptShow`|選擇性 `Int32` 參數。<br /><br /> 取得或設定顯示倒數計時訊息的時間長度，以秒為單位。|  
|`AutoClosePasswordPromptTimeout`|選擇性 `Int32` 參數。<br /><br /> 取得或設定關閉密碼提示對話方塊前的等候時間長度，以秒為單位。|  
|`CertificateFile`|選擇性 `String` 參數。<br /><br /> 取得或設定憑證檔案的路徑。|  
|`CertificateThumbprint`|選擇性 `String` 參數。<br /><br /> 取得或設定憑證指模 \(Certificate Thumbprint\)。|  
|`KeyFile`|選擇性 `String` 參數。<br /><br /> 取得或設定金鑰檔的路徑。|  
|`ResolvedKeyContainer`|選擇性 `String` 輸出參數。<br /><br /> 取得或設定已解析的金鑰容器。|  
|`ResolvedKeyFile`|選擇性 `String` 輸出參數。<br /><br /> 取得或設定已解析的金鑰檔。|  
|`ResolvedThumbprint`|選擇性 `String` 輸出參數。<br /><br /> 取得或設定已解析的憑證指模。|  
|`ShowImportDialogDespitePreviousFailures`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則不管先前的失敗，仍顯示匯入對話方塊。|  
|`SuppressAutoClosePasswordPrompt`|選擇性 `Boolean` 參數。<br /><br /> 取得或設定布林值，這個值指定密碼提示對話方塊是否不應該自動關閉。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)