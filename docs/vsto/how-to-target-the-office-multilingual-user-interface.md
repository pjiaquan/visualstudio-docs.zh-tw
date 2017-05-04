---
title: "如何：以 Office 多語系使用者介面為目標 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "全球化 [Visual Studio 中的 Office 程式開發], 使用者介面目標"
  - "當地語系化 [Visual Studio 中的 Office 程式開發], 使用者介面目標"
  - "MUI [Visual Studio 中的 Office 程式開發]"
  - "多語系使用者介面 [Visual Studio 中的 Office 程式開發]"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 全球化"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 當地語系化"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：以 Office 多語系使用者介面為目標
  多語系使用者介面 \(Multilingual User Interface，MUI\) 是 Microsoft Office 的功能，可以讓使用者變更使用者介面 \(UI\) 的語言。  例如，使用英文 UI 的使用者可以將 UI 的語言變更為西班牙文。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果應用程式的使用者會使用多種語言的 Office，您可以加入程式碼來自動變更 UI 字串的語言，以符合使用者電腦上 Office 所使用的語言 \(如果使用者已安裝了正確的資源\)。  
  
### 若要檢查目前 Office UI 的設定  
  
1.  請使用目前執行緒的 <xref:System.Threading.Thread.CurrentUICulture%2A> 屬性。  設定 UI 字串的語言，以符合目前在使用者電腦上執行的 Office 版本所用的語言。  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## 請參閱  
 [如何：透過主要 Interop 組件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)  
  
  