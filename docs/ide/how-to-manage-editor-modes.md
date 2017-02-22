---
title: "如何：管理編輯器模式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼編輯器, 模式"
  - "程式碼編輯器, 檢視和顯示選項"
  - "字型和大小"
  - "全螢幕模式"
  - "行號"
  - "行號, 顯示"
  - "檢視, 變更模式"
  - "檢視, 建立新視窗"
  - "檢視, 行號"
  - "檢視, 大綱"
  - "檢視, 分割"
  - "檢視, 虛擬空間"
  - "檢視, 自動換行"
  - "虛擬空間模式"
  - "自動換行"
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：管理編輯器模式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用不同的顯示模式來顯示 Visual Studio 程式碼編輯器。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 啟用全螢幕模式  
 您可以選擇隱藏所有工具視窗，並啟用 \[**全螢幕**\] 模式，只檢視文件視窗。  
  
#### 若要啟用全螢幕模式  
  
-   按一下 ALT\+SHIFT\+ENTER 即可進入或結束 \[**全螢幕**\] 模式。  
  
     \-或\-  
  
-   在 \[**命令**\] 視窗中發送 `View.Fullscreen` 命令。  
  
## 啟用虛擬空間模式  
 在 \[**虛擬空間**\] 模式中，每一行程式碼的結尾都會插入空格。  若選取這個選項，則可在程式碼旁邊一致的位置上放置註解。  
  
#### 若要啟動虛擬空間模式  
  
1.  選取 \[**工具**\] 功能表上的 \[**選項**\]。  
  
2.  展開 \[**文字編輯器**\] 資料夾，然後選擇 \[**所有語言**\] 將這個選項套用到所有語言，或者選擇特定語言的資料夾   \(例如，如果只想在 Visual Basic 中開啟行號功能，請依序選擇 \[Basic\] 和 \[文字編輯器\] 選項\)。  
  
3.  選取 \[**一般**\] 選項，再於 \[**設定**\] 下選取 \[**啟用虛擬空間**\]。  
  
    > [!NOTE]
    >  會以 \[**資料行選取**\] 模式啟用 \[**虛擬空間**\]。  若 \[**虛擬空間**\] 模式未啟用，插入點就會從一行的結尾直接移到下一行的第一個字元。  
  
## 請參閱  
 [自訂編輯器](../ide/customizing-the-editor.md)   
 [如何：排列和停駐視窗](../misc/how-to-arrange-and-dock-windows.md)   
 [選項對話方塊、環境、字型和色彩](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)