---
title: "Visual Studio Tools for Unity 程式設計 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Visual Studio Tools for Unity 程式設計
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本節中，您將找到使用 Visual Studio Tools for Unity 應用程式開發介面的範例。  
  
## 範例  
 以下是一些範例，示範如何使用 Visual Studio Tools for Unity 應用程式開發介面。  
  
### 自訂 VSTU 所建立的專案檔  
 Visual Studio Tools for Unity 在專案檔產生期間提供 Unity 樣式回呼。  若要了解如何在每次重新產生時修改專案檔，請參閱[範例：產生專案檔](../cross-platform/customize-project-files-created-by-vstu.md)。  
  
### 與 VSTU 共用 Unity 記錄回呼  
 Visual Studio Tools for Unity 使用 Unity 註冊記錄回呼，以便將其主控台串流至 Visual Studio。  如果您的編輯器指令碼也使用 Unity 註冊記錄回呼，VSTU 回呼可能會與這個回呼相衝突。  若要了解如何與 VSTU 共用 Unity 記錄回呼，請參閱[範例：記錄回呼](../cross-platform/share-the-unity-log-callback-with-vstu.md)。