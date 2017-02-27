---
title: "解除安裝 Windows Installer VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "解除安裝的封裝"
  - "VSPackages，解除安裝"
  - "解除安裝 Vspackage"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 解除安裝 Windows Installer VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大多數的情況下，Windows Installer 可以解除安裝 VSPackage 只由 「 復原 」 一樣安裝 VSPackage。 自訂動作所述 [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 必須也解除安裝後執行。 因為 devenv.exe 呼叫 InstallFinalize 標準動作，如安裝和解除安裝之前，CustomAction 和 InstallExecuteSequence 資料表項目會提供這兩種情況。  
  
> [!NOTE]
>  執行 `devenv /setup` MSI 套件解除安裝之後。  
  
 一般而言，如果您將自訂動作加入至 Windows Installer 封裝時，您必須處理這些動作期間解除安裝和復原。 如果您加入自訂動作來自行註冊您的 VSPackage，比方說，您必須新增自訂動作，太取消註冊。  
  
> [!NOTE]
>  也可讓使用者安裝您的 VSPackage，然後解除安裝舊版 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 與它整合。 您可以協助確定 VSPackage 的解除安裝可在這個案例中藉由消除執行程式碼具有相依性的自訂動作 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 處理啟動條件，在解除安裝期間  
 LaunchConditions 標準動作會讀取 LaunchCondition 資料表來顯示錯誤的資料列不符合條件的訊息。 當啟動條件通常用來確保符合系統需求，您通常可以跳解除安裝期間啟動條件，將條件加入 `NOT Installed`, ，LaunchCondition 資料表的 LaunchConditions 資料列。  
  
 替代方式是將 `OR Installed` 啟動解除安裝期間不重要的條件。 這可確保條件在解除安裝期間永遠是 true，因此不會顯示啟動條件錯誤訊息。  
  
> [!NOTE]
>  `Installed` 這是當它偵測到 VSPackage 確實已安裝在系統上，設定 Windows Installer 屬性。  
  
## 請參閱  
 [Windows Installer](http://msdn.microsoft.com/zh-tw/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)