---
title: "建置和偵錯 SharePoint 方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 建置與偵錯"
  - "Visual Studio 中的 SharePoint 開發, 偵錯"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 建置和偵錯 SharePoint 方案
  一般而言，建置和偵錯 SharePoint 方案與建置和偵錯 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中其他類型的專案相同。  本節中的主題將會說明目前存在的差異。  
  
## SharePoint 方案的專案輸出  
 建置 SharePoint 方案會建立組件和方案套件 \(.wsp\) 檔案。  下表顯示建置期間這些檔案的位置。  
  
|建置項目|輸出資料夾|  
|----------|-----------|  
|組件、程式資料庫 \(PDB\) 和 .wsp 檔案。|*ProjectName*\\bin\\debug 或 *ProjectName*\\bin\\release|  
|SharePoint 專案項目檔案。|*ProjectName*\\pkg\\debug 或 *ProjectName*\\pkg\\release|  
|建置中繼檔案。|*ProjectName*\\obj\\debug 或 *ProjectName*\\obj\\release|  
|封裝中繼檔案。|*ProjectName*\\pkgobj\\debug 或 *ProjectName*\\pkgobj\\release|  
  
## 建置 SharePoint 方案  
 若要建置 SharePoint 方案，開發電腦必須安裝正確版本的 SharePoint 伺服器。  否則，建置 SharePoint 方案將與建置 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中其他類型的專案相同。  如需詳細資訊，請參閱[如何：建置 SharePoint 案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## 偵錯和測試 SharePoint 方案  
 偵錯之前，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 .wsp 套件複製到 SharePoint 伺服器、啟動網站和 Web 範圍功能，並在某些情況下啟動專案。  在某些情況下，您可能需要手動開啟專案。  如需詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)與[對 SharePoint 方案進行偵錯](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## 使用 ALM 功能偵錯及驗證 SharePoint 方案  
 Visual Studio ALM 功能 \(例如單元測試和 IntelliTrace\) 使您可以更精確地在 SharePoint 方案中察覺的問題。  程式碼剖析讓您可以在 SharePoint 方案找出並識別效能問題區域。  如需詳細資訊，請參閱[驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)與[剖析 SharePoint 應用程式的效能](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## 建置處理序中的安全性  
 若要封裝或部署 SharePoint 方案，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 必須具有將檔案複製到 SharePoint 伺服器的權限。  您必須將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 做為較高權限的處理序來執行，且您的使用者帳戶必須為 SharePoint 伺服器上的「網站集合管理員」。  此外，您必須指定您的專案是沙箱化方案或陣列方案。  如需詳細資訊，請參閱[沙箱化方案與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## 使用清除命令  
 在 SharePoint 伺服器上安裝要進行偵錯的 SharePoint 方案時，\[**清除**\] 命令不會解除安裝該方案。  而您必須透過 SharePoint 組態來停用「功能」。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [使用伺服器總管瀏覽 SharePoint 連線](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  