---
title: "選項對話方塊、環境、自動回復 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPag.Environment.AutoRecover"
  - "VS.DialogAutoRestore"
  - "VS.ToolsOptionsPages.Environment.AutoRecover"
  - "VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore"
helpviewer_keywords: 
  - "檔案, 復原"
  - "自動回復頁面"
  - "儲存檔案, 自動"
  - "檔案, 自動儲存"
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 選項對話方塊、環境、自動回復
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用這個 \[選項\] 對話方塊頁面來指定檔案是否自動備份。  這個頁面也允許您指定，當整合式開發環境 \(IDE\) 發生未預期關閉時，是否要還原修改過的檔案。  選取 \[**工具**\] 功能表並選擇 \[**選項**\]，然後選取 \[**環境**\] 資料夾並選擇 \[**自動回復**\] 頁面，即可存取這個對話方塊。  如果這一頁沒有出現在清單上，請在 \[**選項**\] 對話方塊中選取 \[**顯示所有設定**\]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[工具\] 功能表中選取 \[匯入和匯出設定\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 **每 \<n\> 分鐘儲存一次自動回復資訊**  
 使用此選項來自訂檔案在編輯器中自動儲存的頻率。  對於先前儲存過的檔案，檔案複本會儲存到 \\...  \\My Documents\\Visual Studio \<*版本*\>\\Backup Files\\\<*專案名稱*\>。  如果檔案是新的，而且沒有經過手動儲存，便會使用隨機產生的檔案名稱加以儲存。  
  
 **將自動回復資訊保留 \<n\> 天**  
 使用此選項來指定對於建立的自動回復檔案，Visual Studio 會保留多久。  
  
## 請參閱  
 [選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)