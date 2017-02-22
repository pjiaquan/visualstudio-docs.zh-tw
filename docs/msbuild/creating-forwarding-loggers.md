---
title: "建立轉送記錄器 | Microsoft Docs"
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
  - "MSBuild, 轉送記錄器"
  - "MSBuild, 記錄"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 建立轉送記錄器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

轉送記錄器可讓您在多處理器系統上建置專案時選擇想要監視的事件，以提高記錄的效率。  啟用轉送記錄器就可避免不想要的事件充斥中央記錄器、拖慢建置速度以及佔用記錄空間。  
  
 若要建立轉送記錄器，您可以實作 <xref:Microsoft.Build.Framework.IForwardingLogger> 介面，然後再手動實作其方法，或者使用 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 類別及其預先設定的方法。  \(對大部分的應用程式而言，後者便已足夠\)。  
  
## 註冊並回應事件  
 轉送記錄器會收集次要建置引擎報告之建置事件的相關資訊，次要建置引擎是主建置引擎在多處理器系統上建置時建立的背景工作處理序。  接著轉送記錄器會根據您所給的指示，選擇要轉送到中央記錄器的事件。  
  
 您必須註冊轉送記錄器，才能處理要監視的事件。  若要註冊事件，記錄器必須覆寫 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 方法。  此時這個方法會包含選擇性參數 `nodecount`，這個參數可設為系統中的處理器數目  \(預設值為 1\)。  
  
 您可以監視的事件有 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 等。  
  
 在多處理器環境中，事件訊息可能不會按照順序收到。  因此，您必須使用轉送記錄器中的事件處理常式評估事件，設定它決定要將哪些事件傳送到重新導向器，再轉送到中央記錄器。  若要完成這項作業，您可以使用 <xref:Microsoft.Build.Framework.BuildEventContext> 類別附加在每個訊息，以協助識別要轉送的事件，然後將事件的名稱傳遞至 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 類別 \(或其子類別\)。  使用這個方法時，不需要撰寫任何其他特定程式碼來轉送事件。  
  
## 指定轉送記錄器  
 在轉送記錄器編譯到組件之後，您必須告知 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在建置時使用該記錄器。  若要執行這項作業，請將 `/FileLogger`、`/FileLoggerParameters` 和 `/DistributedFileLogger` 參數與 MSBuild.exe 一起使用。  `/FileLogger` 參數會告知 MSBuild.exe，記錄器是直接附加的。`/DistributedFileLogger` 參數表示每個節點都有一個記錄檔。  若要設定轉送記錄器上的參數 \(Parameter\)，請使用 `/FileLoggerParameters` 參數 \(Switch\)。  如需這些參數和其他 MSBuild.exe 參數的詳細資訊，請參閱 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)。  
  
## 辨識多處理器的記錄器  
 當您在多處理器系統上建置專案時，每個處理器的建置訊息不會自動按照統一的順序交錯排列。  相反地，您必須使用附加到每個訊息的 <xref:Microsoft.Build.Framework.BuildEventContext> 類別，建立訊息群組優先順序。  如需多處理器建置的詳細資訊，請參閱[在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)。  
  
## 請參閱  
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [組建記錄器](../msbuild/build-loggers.md)   
 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)