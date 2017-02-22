---
title: "DA0002：遺漏 VSPerfCorProf.dll | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002：遺漏 VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0002|  
|分類|程式碼剖析工具使用|  
|程式碼剖析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令列工具進行程式碼剖析|  
|訊息|收集到的檔案似乎未用 VSPerfCLREnv.cmd 正確設定環境變數。  Managed 二進位檔的符號可能無法解析。|  
|規則型別|資訊|  
  
## 原因  
 程式碼剖析工具在執行程式碼剖析期間找不到 VSPerfCorProf.dll。  使用命令列工具收集分析工具資料，但未使用 VSPerfCLREnv.cmd 工具初始化必要的環境變數時，會發生這個警告。  如果當程式碼剖析工具啟動時，另一個分析工具正在執行，也可能會引發警告。  
  
## 規則描述  
 必須先設定特定的環境變數，程式碼剖析工具才能執行程式碼剖析以解析 .NET Framework 二進位檔中的符號。  此警告表示 VSPerfCLREnv.cmd 工具未在收集程式碼剖析資料之前執行。  Managed 二進位檔的符號可能未解析。  如需從命令列使用程式碼剖析工具的詳細資訊，請參閱[從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## 如何修正違規  
 當您使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具中的命令列工具來剖析 Managed 應用程式時，請在開始收集資料之前，執行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令列工具。