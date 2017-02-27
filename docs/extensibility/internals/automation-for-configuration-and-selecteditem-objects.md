---
title: "自動化的組態和 SelectedItem 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動化 [Visual Studio SDK]，SelectedItem 物件"
  - "建置自動化 [Visual Studio SDK]，"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 自動化的組態和 SelectedItem 物件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以在建立與選取的項目中的程序自動化[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 建置自動化  
 建置\] 或 \[設定具有自動化模型所提供當您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>。  如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。  
  
 如果您建立的 VSPackage，而且想要控制的設定選項，您必須使用 automation 模型。  
  
## SelectedItem 的自動化  
 您沒有提供實作`SelectedItem`物件因為 Visual Studio 包含標準的實作。  不過，您可以執行`SelectedItem`如果您想要的物件。  您必須實作物件，包含`SelectedItem`介面，並將回應傳回至呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>與 VSITEMID 方法設為 \[ <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [提供 Automation 模型](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [了解組建組態](../../ide/understanding-build-configurations.md)