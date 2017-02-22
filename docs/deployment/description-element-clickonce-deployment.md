---
title: "&lt;description&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;description&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別應用程式資訊，用於建立 Shell 顯示內容及 \[控制台\] 中的 \[**新增或移除程式**\] 項目。  
  
## 語法  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## 項目和屬性  
 `description` 項目是必要項，而且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間中。  它不包含子項目而且具有下列屬性：  
  
|屬性|描述|  
|--------|--------|  
|`publisher`|必要項。  當設定安裝部署時，識別用在 Windows \[**開始**\] 功能表中和 \[控制台\] 中 \[**新增或移除程式**\] 項目之圖示定位的公司名稱。|  
|`product`|必要項。  識別完整的產品名稱。  做為安裝在 Windows \[**開始**\] 功能表中圖示的標題。|  
|`suiteName`|選擇項。  在 Windows \[**開始**\] 功能表中，識別 `publisher` 資料夾內的子資料夾。|  
|`supportUrl`|選擇項。  指定在 \[控制台\] 的 \[**新增或移除程式**\] 項目中顯示的支援 URL。  在為安裝設定部署時，此 URL 的捷徑也會為應用程式支援在 Windows \[**開始**\] 功能表中建立。|  
  
## 備註  
 description 項目在所有部署組態中都是必要項。  
  
## 範例  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的 `description` 項目。  這個程式碼範例是 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題完整範例的一部分。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)