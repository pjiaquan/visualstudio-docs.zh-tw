---
title: "註冊及取消註冊 VSPackages |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 Vspackage
您可以使用屬性來註冊 VSPackage，但  
  
## <a name="registering-a-vspackage"></a>註冊 VSPackage  
 您可以使用屬性來控制 managed VSPackages 的註冊。 所有的註冊資訊會包含在.pkgdef 檔。 多個檔案為基礎的註冊的詳細資訊，請參閱[CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。  
  
 下列程式碼示範如何使用標準的註冊屬性，以註冊您的 VSPackage。  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>取消註冊延伸模組  
 如果您一直在試驗不同 VSPackages 很多，而且想要移除的實驗執行個體，您就可以執行**重設**命令。 尋找**重設 Visual Studio 的實驗執行個體**您的電腦，[開始] 頁面上，或從命令列執行這個命令︰  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要解除安裝 Visual Studio 程式開發執行個體已安裝的擴充功能，請移至**工具 / 擴充功能和更新**，尋找擴充功能，然後按一下**解除安裝**。  
  
 如果基於某些原因，這些方法都不成功在解除安裝延伸模組，您可以取消註冊 VSPackage 組件，從命令列如下︰  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage](../extensibility/internals/vspackages.md)
