---
title: "&lt;Signature&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
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
  - "<Signature> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Signature&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含對此部署資訊清單進行數位簽章時所需的資訊。  
  
## 語法  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## 備註  
 使用信封簽章簽署部署資訊清單是選擇性但建議執行的作業。  如需簽章 XML 檔案的詳細資訊，請參閱 [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/) 的＜XML 簽章語法和處理＞中說明的「全球資訊網協會建議」。  
  
 如果您要簽署資訊清單，則必須為所有檔案提供雜湊。  您無法簽署含有未經雜湊處理之檔案的資訊清單，因為使用者無法驗證未雜湊檔案的內容。  
  
## 範例  
 在下列程式碼範例中，會說明在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署中使用之部署資訊清單中的 `Signature` 項目。  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)