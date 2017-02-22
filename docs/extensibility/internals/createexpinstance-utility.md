---
title: "CreateExpInstance 公用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "實驗的組建"
  - "實驗登錄區"
  - "實驗執行個體"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# CreateExpInstance 公用程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 CreateExpInstance 公用程式來建立，重設，或刪除的 Visual Studio 的實驗執行個體。 偵錯及測試 Visual Studio 擴充功能，而不需要變更基礎的產品，您可以使用實驗性執行個體。  
  
## 語法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### 參數  
 \/ 建立  
 建立實驗性執行個體。  
  
 \/ 重設  
 刪除的實驗執行個體，並接著會建立一個新。  
  
 \/Clean  
 刪除的實驗執行個體。  
  
 \/ VSInstance  
 包含要複製基底的 Visual Studio 執行個體的目錄名稱。  
  
 \/ RootSuffix  
 要附加到實驗執行個體目錄的名稱尾碼。  
  
## 備註  
 當您使用 Visual Studio 擴充功能上時，您可以按 F5 以開啟預設的實驗執行個體，並安裝目前的擴充功能。 如果沒有實驗執行個體功能，Visual Studio 會建立一個有預設設定。  
  
 實驗執行個體的預設位置取決於 Visual Studio 版本號碼。 例如，Visual Studio 2015 的位置是 %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ 目錄位置中的所有檔案都視為該執行個體的一部分。 除非變更預設位置的目錄名稱，任何額外的實驗性執行個體不會載入由 Visual Studio。  
  
 在開啟的實驗執行個體時，visual Studio 不會存取系統登錄。 這不同於舊版的 Visual Studio 中，使用實驗性的登錄 hive 的版本。  
  
 CreateExpInstance 公用程式會取代 VsRegEx 公用程式。  
  
 下列範例會重設 Visual Studio 的預設實驗性執行個體。  
  
 **CreateExpInstance.exe \/Reset \/VSInstance \= 14.0 \/RootSuffix \= Exp**  
  
## 請參閱  
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)