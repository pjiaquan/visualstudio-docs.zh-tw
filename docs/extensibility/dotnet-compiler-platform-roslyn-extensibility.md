---
title: ".NET 編譯器平台 (&quot;Roslyn&quot;) 的擴充性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# .NET 編譯器平台 (&quot;Roslyn&quot;) 的擴充性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.NET 編譯器平台 \("Roslyn"\) 進行核心任務是開啟的 C\# 和 Visual Basic 編譯器，並讓工具和開發人員共用的豐富資訊編譯器中有相關的程式。 程式碼分析工具改善程式碼品質和程式碼產生器中應用程式建構的輔助工具。 當工具成為更聰明，他們需要存取到越來越多的唯一編譯器具備深層的程式碼知識。 而不是不透明的轉譯器 \(程式碼置於和物件程式碼\)，Roslyn 編譯器會提供 Api，您可以使用的工具和應用程式中的程式碼相關的工作。  
  
 最棒的部分是 Roslyn 編譯器、 其 Api、 範例和逐步解說和這些 Api 為基礎的實際工具會在所有完全開放的原始碼 [github.com\/dotnet\/roslyn](https://github.com/dotnet/Roslyn)。 請移至要進一步了解並開始使用 Roslyn OSS 站台。 您會發現連結，以取得最新的 C\# 和 VB 功能可讓您以一般使用者，以及若要開始為運用 Roslyn Api 是工具產生器的連結。  
  
## 請參閱  
 [開始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)