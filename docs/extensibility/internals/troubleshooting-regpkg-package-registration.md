---
title: "疑難排解的 RegPkg 套件註冊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 疑難排解的 RegPkg 套件註冊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  在 Visual Studio 中註冊的封裝，最好是使用.pkgdef 檔。 這可讓擴充功能部署而不需要存取系統登錄。 會建立使用 Pkgdef 檔案 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。  
  
 若要如何使用 RegPkg 中的註冊的封裝 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，您必須使用 RegPkg 適用於您的封裝版本。  
  
## 套件版本相關的 RegPkg 版本  
 有兩個 RegPkg 版本。 一個版本包含在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您可以使用這個版本，註冊套件已使用下列組件的其中一個建置:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 它無法登錄已建置之使用舊版 Microsoft.VisualStudio.Shell.dll 組件的封裝。  
  
 舊版的 RegPkg 可以註冊使用 Microsoft.VisualStudio.Shell.dll 組件已建置的封裝。 不過，它無法登錄使用的組件的更新版本所建置的封裝。  
  
## 請參閱  
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)