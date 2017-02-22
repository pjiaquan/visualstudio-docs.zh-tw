---
title: "副檔名、文字編輯器、選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages.text_editor.file_extension"
helpviewer_keywords: 
  - "副檔名, 與編輯器關聯"
  - "編輯經驗"
  - "選項對話方塊"
  - "編輯經驗, 選取"
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 副檔名、文字編輯器、選項
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個 \[選項\] 對話方塊可讓您指定 Visual Studio 整合式開發環境 \(IDE\) 如何處理具有特定副檔名的所有檔案。  您所輸入的每一個 \[**副檔名**\]，都可以選取一種 \[編輯經驗\]。  這可以讓您選擇特定類型的文件應該使用 IDE 編輯器或設計工具來開啟。  若要顯示這些選項，請從 \[**工具**\] 功能表中選擇 \[**選項**\]，展開 \[**文字編輯器**\] 節點，再選取 \[**副檔名**\]。  
  
 如果您選取 \[使用編碼方式\] 選項，則每當您開啟該類型的文件時，便會出現一個對話方塊，供您選取該文件的編碼配置。  當您在準備各種版本的專案文件，以供不同平台或不同目標 \(Target\) 語言使用時，這個選項就相當實用。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## UIElement 清單  
 **副檔名**  
 輸入您想定義其於 IDE 之 \[編輯經驗\] 的副檔名。  
  
 **編輯器**  
 選取用來開啟具有此副檔名之文件的 IDE 編輯器或設計工具。  如果您選取 \[使用編碼方式\] 的選項，則每當您開啟該類型的文件時，便會出現一個對話方塊，供您選取該文件的編碼配置。  
  
 **加入**  
 加入項目，此項目會將指定的 \[**副檔名**\] 和 \[**編輯經驗**\] 併入到 \[副檔名清單\] 中。  
  
 **Remove**  
 從 \[副檔名清單\] 中刪除選取的項目。  
  
 副檔名清單  
 列出已指定 \[編輯經驗\] 的所有副檔名。  
  
 **將無副檔名的檔案對應到**  
 如果您想指定 IDE 應該如何處理沒有副檔名的檔案，請選取這個選項。  
  
 **無副檔名檔案選項**  
 提供與 \[**編輯器**\] 相同的清單。  選取用來開啟沒有副檔名之文件的 IDE 編輯器或設計工具。  
  
## 請參閱  
 [如何：管理編輯器模式](../../ide/how-to-manage-editor-modes.md)