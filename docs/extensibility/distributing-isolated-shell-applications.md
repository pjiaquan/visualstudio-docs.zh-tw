---
title: "散發獨立的 Shell 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 散發獨立的 Shell 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您必須安裝 Visual Studio 和 Visual Studio SDK，才能建立獨立的 shell 應用程式。 散發給其他使用者或客戶的應用程式的機器，請您必須加入特殊的可轉散發套件，為獨立的 shell。  
  
## 散發獨立的 Shell 應用程式的必要條件  
  
|名稱|描述|  
|--------|--------|  
|Visual Studio SDK|您必須開發及測試的擴充功能 SDK [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您也可以使用 SDK 來建立您自己的 Visual Studio 隔離 shell 執行個體。<br /><br /> Visual Studio 是 SDK 的必要條件。|  
|Microsoft Visual Studio 隔離 Shell 可轉散發套件|可轉散發套件建置在 Visual Studio 工具環境時，包含在您的安裝程式隔離 shell。 隔離的 Shell 可轉散發套件包含.NET Framework 4.5。|  
  
## 建立應用程式的安裝程式  
 整合式或外掛式主控殼層應用程式，您必須建立特殊的安裝程式。 如需詳細資訊，請參閱[安裝獨立的 Shell 應用程式](../extensibility/installing-an-isolated-shell-application.md)。  
  
## 允許您的應用程式的更新  
 安裝程式必須允許，您的應用程式會更新，Microsoft 更新或貴公司的更新的可能性。 如需更新的詳細資訊，請參閱 [獨立的 Shell 應用程式服務的指導方針](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。