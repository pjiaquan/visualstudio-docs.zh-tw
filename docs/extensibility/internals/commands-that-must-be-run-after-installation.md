---
title: "必須在安裝後執行的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "後續安裝命令"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# 必須在安裝後執行的命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果您透過.msi 檔案部署您的擴充功能，您必須執行 `devenv /setup` 順序來探索您的擴充功能的 Visual Studio 安裝的一部分。  
  
> [!NOTE]
>  本主題中的資訊適用於尋找 DevEnv Visual Studio 2008 及更早版本。 如需如何探索 DevEnv Visual Studio 的版本資訊，請參閱 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
## 尋找 devenv.exe  
 您可以找到每個版本 devenv.exe 從登錄值 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 撰寫安裝程式，使用 RegLocator 資料表和 AppSearch 資料表來儲存登錄值做為屬性。 如需詳細資訊，請參閱[偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)。  
  
### 若要找出從不同版本的 Visual Studio 的 devenv.exe RegLocator 資料表資料列  
  
|Signature\_|根目錄|索引鍵|名稱|類型|  
|-----------------|---------|---------|--------|--------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### AppSearch 對應 RegLocator 資料表資料列的資料表資料列  
  
|屬性|Signature\_|  
|--------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 例如，Visual Studio 安裝程式會將登錄值的 **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** 為 **C:\\VS2008\\Common7\\IDE\\devenv.exe**, ，必須執行安裝程式的可執行檔的完整路徑。  
  
 **注意** RegLocator 類型資料行是 2，因為不需要指定簽章資料表中的其他版本資訊。  
  
## 執行 devenv.exe  
 之後執行安裝程式中的標準動作 AppSearch，AppSearch 資料表中的每個屬性具有對應版本的 Visual Studio 的 devenv.exe 檔案所指向的值。 如果任何指定的登錄值不存在，因為未安裝該版本的 Visual Studio — 指定的屬性設定為 null。  
  
 執行自訂動作屬性所指向的可執行檔的 Windows 安裝程式支援輸入 50。 自訂動作應該包含在指令碼的執行選項、 msidbCustomActionTypeInScript \(1024\) 和 msidbCustomActionTypeCommit \(512\)，以確保 VSPackage 已整合到之前已成功安裝 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 CustomAction 資料表和自訂動作指令碼中執行的選項。  
  
 自訂動作類型 50 的指定屬性包含可執行檔做為來源資料行和目標資料行中的命令列引數的值。  
  
### 若要執行 devenv.exe CustomAction 資料表資料列  
  
|動作|類型|來源|目標|  
|--------|--------|--------|--------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/setup|  
  
 若要在安裝期間執行的排程來 InstallExecuteSequence 資料表必須撰寫自訂動作。 若要避免如果執行自訂動作使用條件資料行的每個資料列中對應的屬性版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 未安裝在系統上。  
  
> [!NOTE]
>  `Null` 屬性評估為 `False` 時條件中使用。  
  
 針對每個自訂動作 \[順序\] 欄的值取決於 Windows Installer 封裝中的其他順序值。 序列值應為使 devenv.exe 自訂動作以執行盡可能接近前 InstallFinalize 標準動作。  
  
### 若要安排 devenv.exe 自訂動作 InstallExecuteSequence 資料表  
  
|動作|條件|序列|  
|--------|--------|--------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## 請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)