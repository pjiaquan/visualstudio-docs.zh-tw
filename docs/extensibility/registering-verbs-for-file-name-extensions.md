---
title: "註冊副檔名動詞命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動詞命令註冊"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 註冊副檔名動詞命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

與應用程式關聯的檔案名稱副檔名通常會有更好的方法，發生於使用者按兩下檔案。 此慣用動作都會連結到一個動詞命令，例如開啟時，對應的動作。  
  
 您可以註冊在 HKEY\_CLASSES\_ROOT\\ 使用 Shell 機碼位於與擴充功能的程式設計識別項 \(ProgID\) 相關聯的動詞*progid*\\shell。 如需詳細資訊，請參閱 [檔案類型](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## 註冊標準動詞命令  
 作業系統會辨識下列的標準動詞命令︰  
  
-   開啟  
  
-   Edit  
  
-   播放  
  
-   列印  
  
-   預覽  
  
 可能的話，註冊標準的動詞。 最常見的方式是開啟的動作。 只有在清楚的差異開啟檔案並編輯檔案時，請使用編輯動詞命令。 例如，開啟.htm 的檔案其顯示在瀏覽器中，而編輯.htm 檔案啟動 HTML 編輯器中。 標準動詞命令已當地語系化的作業系統地區設定。  
  
> [!NOTE]
>  註冊時的標準動詞，請勿設定開啟索引鍵的預設值。 預設值包含在功能表上的顯示字串。 作業系統會提供此字串的標準動詞命令。  
  
 專案檔應該開始的新執行個體註冊 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 當使用者開啟檔案。 下列範例說明的標準動詞註冊 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案。  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 若要開啟現有的執行個體中的檔案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，註冊 DDEEXEC 金鑰。 下列範例說明的標準動詞註冊 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .cs 檔案。  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## 設定預設的動詞命令  
 預設動作是使用者按兩下 Windows 檔案總管\] 中的檔案時，所執行的動作。 預設動作為動詞命令指定的預設值為 HKEY\_CLASSES\_ROOT\\*progid*\\Shell 索引鍵。 如果未不指定任何值，這個預設動作是 HKEY\_CLASSES\_ROOT\\ 中指定的第一個動詞*progid*\\Shell 索引鍵清單。  
  
> [!NOTE]
>  如果您想要變更預設的並存部署中的延伸模組的動詞命令，請考慮對安裝和移除的影響。 在安裝期間會覆寫原始的預設值。  
  
## 請參閱  
 [Creating a File Association](_win32_file_associations)   
 [管理並行的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)