---
title: "&lt;publisherIdentity&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publisherIdentity 項目 [ClickOnce 部署資訊清單], 簡介"
  - "publisherIdentity 項目 [ClickOnce 部署資訊清單], 語法, 項目, 和屬性"
  - "已簽署資訊清單的必要項目 [ClickOnce], publisherIdentity 項目"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;publisherIdentity&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含簽署此部署資訊清單之發行者的資訊。  
  
## 語法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## 項目和屬性  
 `publisherIdentity` 項目是已簽署資訊清單的必要項。  下表顯示 `publisherIdentity` 項目支援的屬性。  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要項。  說明發行此應用程式的協力廠商識別。|  
|`issuerKeyHash`|必要項。  包含憑證簽發者之公開金鑰的 SHA\-1 雜湊。|  
  
#### 參數  
  
## 屬性值\/傳回值  
  
## 例外狀況  
  
## 備註  
  
## 需求  
  
## 副標題