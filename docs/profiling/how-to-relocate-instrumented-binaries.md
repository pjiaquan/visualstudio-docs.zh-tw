---
title: "如何：重新配置所檢測的二進位檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "二進位檔，已檢測的"
  - "檢測，已檢測的二進位檔"
  - "已檢測的二進位檔和重新配置"
  - "程式碼剖析工具，已檢測的二進位檔"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：重新配置所檢測的二進位檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在檢測期間，會將探查插入二進位檔，以便測量應用程式效能。 藉由選擇重新配置所檢測的二進位檔，可以檢測原始二進位檔的複本，並將此複本放在指定的位置。 如果您不想讓分析工具重新命名原始的二進位檔，這個選項會很有用。 如果未重新配置二進位檔，則會覆寫二進位檔的原始版本。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### 重新配置所檢測的二進位檔  
  
1.  在 \[效能總管\] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 \[屬性\]。  
  
2.  在 \[屬性頁\] 中，按一下 \[二進位檔\] 屬性。  
  
3.  選取 \[重新配置所檢測的二進位檔\] 核取方塊。  
  
4.  指定所檢測之二進位檔的位置。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)