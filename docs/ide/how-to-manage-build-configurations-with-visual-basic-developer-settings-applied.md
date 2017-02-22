---
title: "如何：在套用 Visual Basic 開發者設定的情況下管理組建組態 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "進階組建組態"
  - "使用 Visual Basic 開發者設定來建置"
  - "偵錯組建"
  - "MSBuild, 偵錯組建"
  - "MSBuild, 發行組建"
  - "發行組建"
  - "Visual Studio, 使用 Visual Basic 設定來建置"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：在套用 Visual Basic 開發者設定的情況下管理組建組態
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，在套用了 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開發者設定的情況下，會隱藏所有進階組建組態選項。  本主題將說明，如何以手動方式啟用這些設定。  
  
## 啟用進階組建組態  
 根據預設，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開發者設定會隱藏開啟**組態管理員**對話方塊的選項，以及[專案設計工具](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)中的 \[**組態**\] 和 \[**平台**\] 清單。  
  
#### 若要啟用進階組建組態  
  
1.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。  
  
2.  展開 \[**專案和方案**\]，然後按一下 \[**一般**\]。  
  
    > [!NOTE]
    >  即使未選取 \[**顯示所有設定**\] 選項，仍可看見 \[**一般**\] 節點。  如果您要看見每一個可用的選項，請按一下 \[**顯示所有設定**\]。  
  
3.  按一下 \[**顯示進階組建組態**\]。  
  
4.  按一下 \[**確定**\]。  
  
     現在可在 \[**建置**\] 功能表上使用 \[**組態管理員**\]，並且可在專案設計工具中看見 \[**組態**\] 和 \[**平台**\] 清單。  
  
## 請參閱  
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)