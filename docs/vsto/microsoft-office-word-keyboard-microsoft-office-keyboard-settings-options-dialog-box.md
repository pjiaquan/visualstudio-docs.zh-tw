---
title: "選項對話方塊、Microsoft Office 鍵盤設定、Microsoft Office Word 鍵盤 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "鍵盤快速鍵，Visual Studio 中的 Office 程式開發"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 選項對話方塊、Microsoft Office 鍵盤設定、Microsoft Office Word 鍵盤
  Microsoft Office Word 和 Visual Studio 都可處理快速鍵。  相同的快速鍵組合可以在 Word 和 Visual Studio 中代表不同的命令。  當 Word 在 Visual Studio 中的文件層級專案內開啟時，一次只有一個應用程式可接收快速鍵命令。  根據預設，Visual Studio 會接受所有快速鍵命令，不過您可選取 \[**動態鍵盤配置**\]，使 Word 在文件取得焦點時接收快速鍵命令。  
  
 如果您使用的快速鍵未指派給應用程式中目前正在處理快速鍵的命令，則該快速鍵就會傳遞至其他應用程式。  
  
 您選取的選項在您變更之前，在 Word 專案中都還是有效的。  而且，選取的結果不會影響 Microsoft Office Excel 專案。您必須使用 Microsoft Office Excel 鍵盤選項為 Excel 進行任何變更。  
  
## UIElement 清單  
 **Visual Studio 鍵盤配置**  
 Visual Studio 會接收所有快速鍵命令，即使 Word 文件取得焦點也一樣。  例如，如果您在文件取得焦點時按功能鍵 F5，Visual Studio 會開始偵錯方案。  
  
 **動態鍵盤配置**  
 Visual Studio 只會在其取得焦點時接收快速鍵命令。  當 Word 文件取得焦點時，Word 會接收所有快速鍵命令。  例如，當 Word 文件具有焦點時，如果您按下功能鍵 F5，Word 會開啟已選取的 \[**尋找和取代**\] 對話方塊的 \[**到**\] 索引標籤。  如果您在 Visual Studio 取得焦點時按 F5，Visual Studio 會開始偵錯方案。  
  
## 請參閱  
 [選項對話方塊、Microsoft Office 鍵盤設定、Microsoft Office Excel 鍵盤](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  