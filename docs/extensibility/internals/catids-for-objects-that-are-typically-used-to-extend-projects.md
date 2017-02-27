---
title: "物件，通常會用來擴充專案的 Catid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，catid 的方式"
  - "Vspackage 的 Guid"
  - "Vspackage 的 Catid"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 物件，通常會用來擴充專案的 Catid
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下表列出用來擴充 catid 的方式`Project`和`ProjectItem`自動化物件的[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，以及[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案。  VSLangProj.olb 中定義這些 catid 的方式。  
  
## 列出的 catid 的方式  
  
|名稱|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{} 610D4614\-D0D5\-11D2\-8599\-006097C68E81|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{} 610D4615\-D0D5\-11D2\-8599\-006097C68E81|  
  
## Visual Basic catid 的方式  
 下表列出用來擴充 catid 的方式[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]瀏覽物件。  所有定義這些 VSLangProj.olb。  
  
|名稱|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{} E0FDC879\-C32A\-4751\-A3D3\-0B3824BD575F|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{} 67F8DD11\-14EB\-489b\-87F0\-F01C52AF3870|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{} EA5BD05D\-3C72\-40A5\-95A0\-28A2773311CA|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{} 932DC619\-2EAA\-4192\-B7E6\-3D15AD31DF49|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{} 2289B812\-8191\-4e81\-B7B3\-174045AB0CB5|  
  
## 視覺 C\# catid 的方式  
 下列 catid 的方式可以用來擴充[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]瀏覽物件。  所有定義這些 VSLangProj.olb。  
  
|名稱|GUID|  
|--------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{} 4EF9F003\-DE95\-4d60\-96B0\-212979F2A857|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{} A12CE10A\-227F\-4963\-ADB6\-3A43388513CA|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{} 8D58E6AF\-ED4E\-48B0\-8C7B\-C74EF0735451|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{} 914FE278\-054A\-45DB\-BF9E\-5F22484CC84C|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{} 2F0FA3B8\-C855\-4a4e\-95A5\-CB45C67D6C27|  
  
## C \+ \+ catid 的方式  
 下列[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案的 catid 的方式不會顯示在型別程式庫中的系統[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。NET 2003，可能會包含在程式碼中，每當您想要擴充這些專案物件。  這些 catid 的方式將會包含在型別程式庫的新版本當中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
|名稱|GUID|  
|--------|----------|  
|`CVCProjectNode`|{} EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFolderNode`|{} EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFileNode`|{} EE8299C9\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
  
 下列程式碼範例示範如何在程式碼中這些 catid 的方式進行程式設計。  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 下列[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案的系統 catid 的方式也不會顯示在型別程式庫，在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。NET 2003，可能會包含在程式碼中，每當您想要擴充這些專案物件。  這些 catid 的方式是只在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。NET 2003，並不會出現在後續的發行版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
|名稱|GUID|  
|--------|----------|  
|`CVCAssemblyReferenceNode` **:**|{} FE8299C9\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCProjectReferenceNode`|{} 593DCFCE\-20A7\-48e4\-ACA1\-49ADE9049887|  
|`CVCActiveXReferenceNode`|{} 9E8182D3\-C60A\-44f4\-A74B\-14C90EF9CACE|  
|`CVCReferences`|{} FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
  
 下列程式碼範例示範如何以程式設計這些程式碼中 catid 的方式：  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Guid [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型\] 下表所示。  
  
|專案類型|GUID|  
|----------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{} FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{} F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F|  
  
## 請參閱  
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)