---
title: "在 Vspackage 中安全性的最佳做法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>在 Vspackage 中的安全性最佳作法
若要安裝[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]電腦時，您必須執行系統管理認證的內容中。 安全性和部署的基本單位[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]應用程式是[VSPackages](../../extensibility/internals/vspackages.md)。 必須使用註冊 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，這也需要系統管理認證。  
  
 系統管理員具有完整權限來寫入登錄和檔案系統，以及執行任何程式碼。 您必須具有這些使用權限來開發、 部署或安裝 VSPackage。  
  
 它會安裝，因為 VSPackage 是完全受信任。 此高層級的權限相關聯的 VSPackage，因為很可能不小心安裝具有惡意的 VSPackage。  
  
 使用者應該確定他們只從信任的來源安裝 Vspackage。 企業發展 VSPackages 應該強式名稱並加以簽署，以確保使用者的竄改時防止。 企業發展 VSPackages 應該檢查其外部的相依性，例如 web 服務和遠端安裝，評估並更正任何安全性問題。  
  
 如需詳細資訊，請參閱 < 安全程式碼撰寫方針適用於.NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx))。  
  
## <a name="see-also"></a>另請參閱  
 [增益集安全性](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 安全性](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
