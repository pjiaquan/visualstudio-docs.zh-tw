---
title: "關於檔案名稱的副檔名 | Microsoft Docs"
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
  - "副檔名"
  - "檔案名稱的副檔名"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 關於檔案名稱的副檔名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您註冊副檔名為 VSPackage 時，您將它關聯的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  這是很重要的 if 多個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已安裝在電腦上。  
  
 VSPackages 的副檔名集都註冊在 HKEY\_CLASSES\_ROOT 機碼的相關聯的程式設計識別項 \(ProgID\) 所指向的點，預設值。  
  
 以下是.vcproj 檔案的副檔名的註冊資訊的範例：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 相關聯的檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必須有已建立版本的 ProgID，例如`VisualStudio.vcproj.8.0`，而允許並排顯示的安裝，要維護產品版本之間的檔案副檔名關聯的產品。  與版本專屬的 ProgID 也可讓您使用標準動詞命令，例如開啟時，編輯、 等等，而不需要覆寫或被其他應用程式或舊版覆寫，或考慮[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 在某些情況下，應該不會變更檔案副檔名相關聯的 ProgID。  例如，副檔名為.htm ProgID \(progid \= htmlfile\) 是硬式編碼在多種情況，在作業系統中，並已廣為已知且使用中的關聯，使用.htm 和.html 檔案。  
  
## 請參閱  
 [註冊副檔名的並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定檔案名稱的副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)