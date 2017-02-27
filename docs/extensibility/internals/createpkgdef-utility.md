---
title: "CreatePkgDef 公用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "封裝定義"
  - "建立 pkgdef"
  - "pkgdef"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# CreatePkgDef 公用程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

採用 Visual Studio 延伸模組做為參數的.dll 檔案，建立伴隨著.dll.pkgdef 檔。 .Pkgdef 檔包含會否則寫入系統登錄延伸模組已安裝的所有資訊。  
  
> [!NOTE]
>  大部分的專案範本隨附於 Visual Studio SDK 會自動建立.pkgdef 檔做為建置流程的一部分。 這份文件的適用對象對於想要以手動方式建立封裝，或使用.pkgdef 部署的現有封裝轉換。  
  
## 語法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## 引數  
 \/ 出 \=`FileName`  
 必要項。 設定.pkgdef 輸出檔案名稱```FileName`。  
  
 \/codebase  
 選擇項。 強制使用程式碼基底公用程式的註冊。  
  
 \/assembly  
 強制註冊組件的公用程式。  
  
 `AssemblyPath`  
 您要產生.pkgdef.dll 檔案的路徑。  
  
## 備註  
 藉由使用.pkgdef 檔案的擴充功能部署會取代舊版的 Visual Studio 的登錄需求。  
  
 .Pkgdef 檔必須安裝在下列位置之一: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ 或 %vsinstalldir%\\common7\\ide\\extensions\\。 如果 %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ 安裝資料夾，擴充功能將無法辨識的 Visual Studio 中，但預設會停用。 使用者可以啟用延伸模組使用 **擴充功能和更新**。 如果安裝資料夾 %vsinstalldir%\\common7\\ide\\extensions\\，預設會啟用擴充功能。  
  
> [!NOTE]
>  **擴充功能和更新** 工具無法用來存取延伸模組，除非安裝 VSIX 套件的一部分。  
  
## 請參閱  
 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)