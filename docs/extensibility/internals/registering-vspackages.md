---
title: "註冊 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "註冊的 managed 的 VSPackages"
  - "註冊、 managed VSPackages"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 註冊 Vspackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]依賴來說明，並且找出 VSPackage 的.pkgdef 檔案。  .Pkgdef 檔案會包含所有的註冊資訊，否則會加入至系統登錄。  藉由將屬性加入至原始程式檔，然後執行已登錄的受管理的 VSPackages [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)上產生的組件，以產生.pkgdef 檔。  
  
## 在本節中  
 [指定 VS Shell VSPackage 檔案位置](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 描述載入路徑為 VSPackages。  
  
 [註冊和取消註冊 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 說明如何註冊 VSPackage。  
  
 [使用自訂註冊屬性來登錄延伸模組](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 說明如何建立註冊資訊清單可以用來部署受管理的 VSPackage。