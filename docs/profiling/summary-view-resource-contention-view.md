---
title: "摘要檢視 - 程式碼剖析工具：資源爭用檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "摘要檢視"
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 摘要檢視 - 程式碼剖析工具：資源爭用檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[摘要\] 檢視會針對在等待存取資源的同時暫止執行緒或處理序的應用程式，顯示其中事件的相關資訊。  
  
 如需詳細資訊，包括通知連結和報表清單的說明，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## 時間表圖形  
 \[摘要\] 檢視中的時間表圖形會顯示程式碼剖析期間，程式碼剖析之應用程式的爭用事件數目。  您可以使用時間表圖形，將檢視篩選至選取的時間範圍。  如需詳細資訊，請參閱[如何：從摘要時間表篩選報表檢視](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 最多爭用的資源  
 \[**最多爭用的資源**\] 會列出應用程式中造成最多爭用事件的資源。  按一下資源名稱即可顯示 \[爭用\] 檢視。  \[爭用\] 檢視會依照執行緒提供資源爭用的詳細時間表。  
  
 \[**最多爭用的資源**\] 包括每個資源的下列資料。  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|資源名稱。|  
|**爭用 %**|程式碼剖析資料中，此資源的爭用佔所有爭用事件的百分比。|  
  
## 最多爭用的執行緒  
 \[**最多爭用的執行緒**\] 會列出應用程式中擁有最多爭用事件數的執行緒。  按一下執行緒名稱即可顯示 \[爭用\] 檢視，其中會依照執行緒提供資源爭用的詳細時間表。  
  
 \[**最多爭用的執行緒**\] 包括每個執行緒的下列資料。  
  
|資料行|描述|  
|---------|--------|  
|**ID**|執行緒識別項。|  
|**名稱**|擁有執行緒的處理序名稱。|  
|**爭用 %**|程式碼剖析資料中，此資源的爭用佔所有爭用事件的百分比。|