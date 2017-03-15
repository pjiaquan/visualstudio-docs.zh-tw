---
title: "設定目標和工作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 設定目標和工作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以設定MSBuild 目標和工作以跨處理序執行，如此一來你就能把目標設為你現在沒在運行的內文。  例如，在開發電腦上執行 64 位元作業系統的 .NET Framework 4.5 時，您能以 32 位元 .NET Framework 2.0 應用程式為建立目標。  您也可以使用裝有 .NET Framework 4或更早版本的目標電腦。  32\- 或者 64\- 位元和特定版本的 .NET Framework 的組合被稱為 *目標的內容*。  
  
## 安裝  
 .NET Framework 4.5 和 4.5.1 取代 Common Language Runtime \(CLR\)、目標、.NET Framework 4 的工作和工具，而不用重新命名。  .NET Framework 4.5.1 安裝為 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]的一部份。  
  
 如果您想要個別安裝 MSBuild 與 Visual Studio，您可以從[MSBuild 下載](http://go.microsoft.com/fwlink/?LinkId=309745)中下載安裝套件。  您也必須安裝您希望也使用的 .NET Framework 版本。  
  
## 目標和工作  
 MSBuild 執行一些流程之外的組建工作以鎖定一組較大的內容。例如， 32 位元 MSBuild 可能在 64 位元處理序執行組建工作以鎖定 64 位元電腦。  這是提供的 `UsingTask` 和 `Task` 參數的控制項。  以 .NET Framework 4.5 安裝設定這些引數和參數的目標，並不需要變更建立對各種目標內容的應用程式。  
  
 如果您要建立自己的目標內容，您必須適當地設定這些引數和參數。  如果需要參考範例，請看 .NET Framework 4.5 Microsoft.Common.targets 檔案和 Microsoft.Common.Tasks 檔案。如需如何建立可以與多個目標內容一起使用的相關資訊、如何修改現有的工作的自訂工作，請參閱 [如何：設定目標和工作](../msbuild/how-to-configure-targets-and-tasks.md)。  
  
## 請參閱  
 [多目標](../msbuild/msbuild-multitargeting-overview.md)