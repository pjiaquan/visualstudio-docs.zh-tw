---
title: "Office 方案的部署資訊清單 | Microsoft Docs"
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
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，部署資訊清單"
  - "部署資訊清單 [Visual Studio 中的 Office 程式開發]"
  - "資訊清單 [Visual Studio 中的 Office 程式開發]，部署"
  - "Visual Studio 中的 Office 程式開發，部署資訊清單"
ms.assetid: 3fb29743-fb96-4d61-a99a-9b1bbafeee13
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Office 方案的部署資訊清單
  部署資訊清單是 XML 檔案，這個檔案會描述 Office 方案的部署設定，並識別目前的應用程式版本。  
  
 Visual Studio 中的 Office 程式開發會使用 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)參考中定義的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署資訊清單結構描述。  
  
## 備註  
 Office 方案的部署資訊清單檔會識別目前版本及其他部署設定。  它會參考應用程式資訊清單，其中描述了方案目前的版本，以及方案中包含的所有檔案。  
  
## 檔名語法  
 部署資訊清單的檔名必須以 .vsto 副檔名為結尾。  雖然這是一種標準[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]部署資訊清單，若要啟用Visual Studio工具來控制代碼檔案的 Office執行階段為不同的副檔名。  
  
## 範例  
 下列程式碼範例說明Visual Studio工具 Office解決方案的部署資訊清單。  
  
```  
  
<asmv1:assembly   
  xsi:schemaLocation=  
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"   
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"   
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"   
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"   
  xmlns="urn:schemas-microsoft-com:asm.v2"   
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"   
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"   
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="ContosoOfficeSolutions.vsto"   
    version="1.0.0.0"   
    publicKeyToken="25d0f3ca94156f1f"   
    language="neutral"   
    processorArchitecture="msil"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description   
    asmv2:publisher="Microsoft"   
    asmv2:product="ContosoOfficeSolutions"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="false" mapFileExtensions="true" />  
  <dependency>  
    <dependentAssembly   
      dependencyType="install"   
      codebase="ContosoOfficeSolutions.dll.manifest"   
      size="13545">  
      <assemblyIdentity   
        name="ContosoOfficeSolutions.dll"   
        version="1.0.0.0"   
        publicKeyToken="25d0f3ca94156f1f"   
        language="neutral"   
        processorArchitecture="msil"   
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm=  
            "urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>PoY</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
  <publisherIdentity name="name" issuerKeyHash="003" />  
<Signature   
  Id="StrongNameSignature"   
  xmlns="http://www.w3.org/2000/09/xmldsig#">    
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
      "http://www.w3.org/2001/10/xml-exc-c14n#" />  
  <SignatureMethod Algorithm=  
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
        <Transform Algorithm=  
          "http://www.w3.org/2001/10/xml-exc-c14n#" />  
      </Transforms>  
      <DigestMethod Algorithm=  
        "http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>5oz</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>nNG</SignatureValue>  
  <KeyInfo Id="StrongNameKeyInfo">  
    <KeyValue>  
      <RSAKeyValue>  
        <Modulus>ufI</Modulus>  
        <Exponent>AQAB</Exponent>  
      </RSAKeyValue>  
    </KeyValue>  
    <msrel:RelData   
      xmlns:msrel=  
        "http://schemas.microsoft.com/windows/rel/2005/reldata">  
      <r:license   
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
        xmlns:as=  
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">  
        <r:grant>  
          <as:ManifestInformation   
            Hash="099"   
            Description=""   
            Url="">  
            <as:assemblyIdentity   
              name="ContosoOfficeSolutions.vsto"   
              version="1.0.0.0"   
              publicKeyToken="25d0f3ca94156f1f"   
              language="neutral"   
              processorArchitecture="msil"   
              xmlns="urn:schemas-microsoft-com:asm.v1" />  
          </as:ManifestInformation>  
          <as:SignedBy />  
          <as:AuthenticodePublisher>  
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>  
          </as:AuthenticodePublisher>  
        </r:grant>  
        <r:issuer>  
          <Signature   
            Id="AuthenticodeSignature"   
            xmlns="http://www.w3.org/2000/09/xmldsig#">  
            <SignedInfo>  
              <CanonicalizationMethod   
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />  
              <SignatureMethod   
                Algorithm=  
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
              <Reference URI="">  
                <Transforms>  
                  <Transform Algorithm=  
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
                  <Transform Algorithm=  
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />  
                </Transforms>  
                <DigestMethod   
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
                <DigestValue>iAd</DigestValue>  
              </Reference>  
            </SignedInfo>  
            <SignatureValue>HL9</SignatureValue>  
            <KeyInfo>  
              <KeyValue>  
                <RSAKeyValue>  
                  <Modulus>ufI</Modulus>  
                  <Exponent>AQAB</Exponent>  
                </RSAKeyValue>  
              </KeyValue>  
              <X509Data>  
                <X509Certificate>MII</X509Certificate>  
              </X509Data>  
            </KeyInfo>  
          </Signature>  
        </r:issuer>  
      </r:license>  
    </msrel:RelData>  
  </KeyInfo>  
</Signature>  
</asmv1:assembly>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)  
  
  