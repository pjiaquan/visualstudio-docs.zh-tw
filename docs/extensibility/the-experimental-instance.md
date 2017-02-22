---
title: "實驗執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "實驗的組建"
  - "VSPackages，實驗的組建"
  - "VSIP，實驗的組建"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# 實驗執行個體
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為了保護未經測試可能會變更它的應用程式從 Visual Studio 開發環境，VSSDK 提供實驗性的空間可供您實驗。 像往常一樣，使用 Visual Studio 開發新的應用程式，但您使用此實驗執行個體執行。  
  
 每個都有 VSIX 套件的應用程式會啟動偵錯模式中的 Visual Studio 實驗性執行個體。  
  
 如果您想要開始在特定的方案之外的 Visual Studio 的實驗執行個體，請在命令視窗執行下列命令:  
  
 「*\< visual studio 安裝路徑 \>*\\Common7\\IDE\\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  實驗性執行個體寫入登錄 `<version number>Exp` 和 `<version number>Exp_Config` 節點。 比方說是 Visual Studio 2015 實驗登錄區  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 我們建議您在實驗執行個體中執行您的擴充功能，在開發過程。 當您部署擴充功能時，它會在開發執行個體中執行。 如需登錄應用程式的詳細資訊，請參閱 [註冊 Vspackage](../extensibility/internals/registering-vspackages.md)。