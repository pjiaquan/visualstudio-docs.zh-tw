---
title: "64 位元應用程式的部署必要條件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 位元 [Visual Studio]"
  - "64 位元應用程式 [Visual Studio]"
  - "64 位元程式設計 [Visual Studio]"
  - "部署應用程式 [Visual Studio], 64 位元"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 64 位元應用程式的部署必要條件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 部署支援在 64 位元平台上的應用程式的安裝。  目標平台包括 **x86** \(表示 32 位元平台\)、**x64** \(表示支援 AMD64 和 EM64T 指令集的電腦\)，以及 **Itanium** \(表示 64 位元 Itanium 處理器\)。  
  
## 必要條件  
 下表列出一些可轉散發套件，您可以將它們當做 64 位元應用程式安裝的必要條件來使用。  
  
 如果您選取沒有 64 位元元件的必要條件，可能會出現警告，指出選取的套件不適用於 64 位元平台。  
  
|可轉散發套件|x64 支援|IA64 支援|  
|------------|------------|-------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|是|否|  
|Visual C\+\+ 2010 執行階段程式庫 \(IA64\)|否|是|  
|Visual C\+\+ 2010 執行階段程式庫 \(x64\)|是|否|  
|Microsoft .NET Framework 4 \(x86 和 x64\)|是||  
|Microsoft .NET Framework 4 Client Profile \(x86 和 x64\)|是||  
  
## 請參閱  
 [部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)   
 [如何：使用 ClickOnce 應用程式安裝必要條件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [64 位元應用程式](../Topic/64-bit%20Applications.md)