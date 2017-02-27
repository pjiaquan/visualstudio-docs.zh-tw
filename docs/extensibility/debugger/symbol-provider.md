---
title: "符號提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "符號處理常式"
  - "[偵錯 SDK] 進行偵錯，符號處理常式"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 符號提供者
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

運算式評估工具實作必須存取以評估變數與運算式語言編譯器所產生的符號偵錯資訊。  它會藉由使用的符號提供者 \(SP\)，介面也稱為符號處理常式。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供用於 managed 程式碼，以及使用的程式資料庫 \(PDB\) 符號檔案格式的原生程式碼的預存程序。  除非另有增強式必須為您的程式是使用儲存在自訂格式的符號，所以建議您在使用預存程序所提供的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 實作的注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎預期要與預存程序，使用通用語言執行階段 \(CLR\) 介面。  如此一來，會使用 Visual Studio 的偵錯引擎會使用預存程序必須支援 CLR。  所有的 CLR 偵錯介面的完整清單，請參閱 debugref.doc，也就是組件的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]。  
  
 如果您的預存程序只會使用自訂的偵錯引擎，您就可以實作預存程序，視您的偵錯引擎的需求而定。  
  
## 請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)