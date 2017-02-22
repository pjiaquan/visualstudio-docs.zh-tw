---
title: "ClickOnce 快取概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 應用程式, 快取"
  - "ClickOnce 部署, 快取"
  - "Windows 應用程式, ClickOnce 部署"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 快取概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，無論是安裝在本機或是裝載於線上，都是儲存在用戶端電腦的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式「*快取*」\(Cache\) 中。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 快取是一系列的隱藏目錄，位於目前使用者的 \[Documents and Settings\] 資料夾的 \[Local Settings\] 目錄中。  此快取含有所有的應用程式檔案，包括組件、組態檔、應用程式和使用者設定，以及資料目錄。  快取也負責將應用程式的資料目錄移轉到最新的版本。  如需資料移轉的詳細資訊，請參閱[在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
 藉由提供單一的應用程式儲存位置，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 自使用者接管了管理應用程式實體安裝的工作。  藉由分開存放所有應用程式以及其不同版本的組件和資料檔案，快取還有助於隔離應用程式。  例如，當您升級 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，該版本與其資料資源都是由快取中它們自己的目錄所提供。  
  
## 快取儲存配額  
 在線上裝載的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，能夠佔有的空間量都受限於約束 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 快取大小的配額。  快取大小會套用至所有使用者的線上應用程式；但單一部分信任的線上應用程式只能佔用一半的配額空間。  已安裝的應用程式不受快取大小限制，而且不會降低快取限制。  對於所有的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，快取只會保留目前的版本和上一次安裝的版本。  
  
 根據預設，用戶端電腦對線上 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式提供 250 MB 的儲存量。  資料檔案沒有這項限制。  只要變更特定用戶端電腦上的登錄機碼 HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB \(DWORD 值，以 KB 為單位所表示的快取大小\)，系統管理員即可增加或減少這項配額。  例如，為了將快取大小減少到 50 MB，您應該將此值變更為 51200。  
  
## 請參閱  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)