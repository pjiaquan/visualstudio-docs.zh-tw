---
title: "用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項 | Microsoft Docs"
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
  - "VST.SelectDocWizard.ContainsActiveXControls"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 用來建立此專案的活頁簿包含設計工具無法載入的 ActiveX 控制項
  當您以程式設計的方式將控制項加入至 Word 文件或 Excel 工作表、儲存文件或活頁簿，然後根據文件或活頁簿建立新的文件層級方案，則會出現這個錯誤。  
  
 描述控制項的 managed 類型資訊不會與文件或活頁簿一起儲存。  當您根據文件或活頁簿建立新的方案時，Visual Studio 沒有足夠的資訊以在主機項目設計工具中載入控制項。  
  
### 更正這個錯誤  
  
1.  開啟文件或活頁簿。  
  
2.  移除在執行階段所加入的控制項。  在文件或活頁簿中選取它們，然後按 DELETE 鍵，即可執行這項操作。  
  
3.  根據文件或活頁簿建立文件層級的方案。  
  
## 請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  