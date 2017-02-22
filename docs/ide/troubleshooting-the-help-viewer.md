---
title: "說明檢視器疑難排解 | Microsoft Docs"
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
  - "說明檢視器 2.0, 疑難排解"
  - "疑難排解 [說明檢視器 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 說明檢視器疑難排解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題討論可能會遇到說明檢視器的問題。  
  
## 音訊無法運作。  
 說明檢視器不含音訊播放程式。  如果要下載包含音訊的內容，但卻什麼都沒發生，當您選取 \[**播放**\]時，請安裝音訊播放程式。  
  
## 搜尋在 Windows Server 2008、Windows Server 2008 SP1 或 Windows Server 2008 R2 中無法運作。  
 說明檢視器中的搜尋和篩選功能需要安裝並開啟 Windows 搜尋服務。  在 Windows Server 2008、Windows Server 2008 Service Pack 1 \(SP1\) 和 Windows Server 2008 R2 中，預設會關閉這項服務。  
  
#### 若要啟動 Windows 搜尋服務  
  
1.  啟動伺服器管理員。  
  
2.  在左邊巡覽窗格中，選取 \[**角色**\]。  
  
3.  在 \[摘要\] 窗格中，選取 \[**新增角色**\]。  
  
4.  選擇檔案服務角色，然後選擇 \[**下一步**\] 按鈕。  
  
5.  選取 \[視窗搜尋\] 角色服務。  
  
## 其他資源  
 您可以使用下列資源，在說明檢視器可以取得詳細資訊及提供意見:  
  
-   若要提供意見，請參閱 Microsoft 網站上的 [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) 或傳送電子郵件給 [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com)。  
  
-   如需詳細資訊，請參閱[開發人員文件及說明系統](http://go.microsoft.com/fwlink/?LinkId=232741)論壇 \(英文\) 和 [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) 部落格 \(英文\)。  
  
## 請參閱  
 [說明檢視器 2.1 系統管理員指南](http://go.microsoft.com/fwlink/?LinkId=243985)