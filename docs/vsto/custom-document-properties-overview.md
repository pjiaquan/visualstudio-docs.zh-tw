---
title: "自訂文件屬性概觀"
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
helpviewer_keywords: 
  - "_AssemblyLocation 屬性"
  - "_AssemblyName 屬性"
  - "自訂文件屬性"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發], 自訂屬性"
  - "文件 [Visual Studio 中的 Office 程式開發], 自訂屬性"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 自訂屬性"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 自訂文件屬性概觀
  當您建置文件層級專案時，Visual Studio 會在專案的文件中加入兩個自訂屬性：\_AssemblyLocation 和 \_AssemblyName。  當使用者開啟文件時，Microsoft Office 應用程式會檢查這些自訂文件屬性。  如果這些屬性存在文件中，則應用程式會載入 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 以啟動自訂。  如需詳細資訊，請參閱[Office 方案在 Visual Studio 中的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 這個屬性包含 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的 Office 方案載入器元件中介面的 CLSID。  CLSID 值為 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B。  您不得變更此值。  
  
## \_AssemblyLocation  
 這個屬性包含了可提供自訂之部署資訊清單相關詳細資訊的字串。  如需資訊清單的詳細資訊，請參閱[Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)。  
  
 根據方案的部署方式而定，\_AssemblyLocation 屬性值可以有不同的格式：  
  
-   如果發行的方案要從網站、UNC 路徑或 CD 或 USB 磁碟機進行安裝，則 \_AssemblyLocation 屬性的格式為 *DeploymentManifestPath*|*SolutionID*。  以下字串即為一個範例：  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   如果您正從 Visual Studio 執行方案或進行偵錯，則 \_AssemblyLocation 屬性的格式為 *DeploymentManifestName*|*SolutionID*|vstolocal。  以下字串即為一個範例：  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *SolutionID* 是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 用來識別方案的 GUID。  會在您建置專案時， *SolutionID* 自動產生。**vstolocal** 詞彙表示對 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 詞彙表示應從與文件相同的資料夾載入組件的。  
  
## 請參閱  
 [Office 方案在 Visual Studio 中的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)   
 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [HOW TO：使用 ClickOnce 發行 Office 方案](http://msdn.microsoft.com/zh-tw/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [如何：建立及修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  