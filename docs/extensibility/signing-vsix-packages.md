---
title: "簽署 VSIX 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>簽署 VSIX 封裝
延伸模組組件不需要經過簽署才能在 Visual Studio 中，可以執行，但最好這麼做。  
  
 如果您想要保護您的擴充功能，並確定沒有遭到竄改，您可以加入 VSIX 套件來數位簽章。 當已簽署 VSIX 時，VSIX 安裝程式會顯示一則訊息指出它已簽署，再加上簽章本身的詳細資訊。 如果 VSIX 內容已經被修改，而且尚未重新簽署此 VSIX，VSIX 安裝程式會顯示簽章無效。 在安裝時不會停止，但會警告使用者。  
  
> [!IMPORTANT]
>  從 2015年，使用 SHA256 加密以外的任何簽章的 VSIX 套件將會識別為具有無效簽章。 不會封鎖 VSIX 安裝，但使用者將會收到警告。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>簽章與 VSIXSignTool VSIX  
 沒有簽署工具可從 SHA256 加密[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)在 nuget.org 上[VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)。  
  
#### <a name="to-use-the-vsixsigntool"></a>若要使用 VSIXSignTool  
  
1.  將您的 VSIX 加入至專案。  
  
2.  以滑鼠右鍵按一下專案節點，在 [方案總管] 中，選取**新增 |管理 NuGet 封裝**。  如需有關 NuGet 和加入 NuGet 封裝請參閱[NuGet 概觀](http://docs.nuget.org/)和[使用對話方塊管理 NuGet 套件](http://docs.nuget.org/Consume/Package-Manager-Dialog)。  
  
3.  搜尋從 VisualStudioExtensibility VSIXSignTool 並安裝 NuGet 封裝。  
  
4.  您現在可以執行 VSIXSignTool 從專案的本機封裝位置。 如您簽署的案例，請參閱工具的命令列說明 (VSIXSignTool.exe /？)。  
  
 例如若要登入與密碼保護的憑證檔案︰  
  
 VSIXSignTool.exe 登 /f \<certfile > / p\<密碼 > \<VSIXfile >  
  
## <a name="see-also"></a>另請參閱  
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
