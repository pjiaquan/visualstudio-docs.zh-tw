---
title: "IManagedAddin::Load"
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
  - "IManagedAddin::Load"
  - "載入方法"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  載入 Managed VSTO 增益集時呼叫。  
  
## 語法  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|*bstrManifestURL*|VSTO 增益集之資訊清單的完整路徑。|  
|*pdispApplication*|IDispatch 的指標，代表載入 VSTO 增益集的主應用程式。|  
  
## 傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## 備註  
 資訊清單是一種檔案 \(通常是 XML 檔案\)，可提供協助載入 VSTO 增益集的資訊。 例如，資訊清單可以指定 VSTO 增益集組件的位置，以及載入 VSTO 增益集時要具現化的進入點類別。  
  
 *bstrManifestURL* 參數包含 `Manifest` 項目的值，該項目位於 VSTO 增益集的 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<應用程式名稱\>*\\Addins\\*\<增益集識別碼\>* 登錄機碼下。 如需詳細資訊，請參閱[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)。  
  
 實作 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 方法可針對所要載入之 VSTO 增益集執行工作，例如設定增益集的應用程式定義域和安全性原則。  
  
## 請參閱  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  