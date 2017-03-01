---
title: "使用修改獨立的 Shell。Pkgundef 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用修改獨立的 Shell。Pkgundef 檔案
您可以修改.pkgundef 来排除的檔案指定的登錄項目從獨立的 shell 應用程式。 一般而言，第一次的電腦，啟動應用程式的 Visual Studio shell 複製現有的 Visual Studio 登錄項目到應用程式的根登錄機碼。 這包括任何參考目前已安裝的 Vspackage。  
  
 若要排除特定的登錄項目從獨立的 shell 應用程式，新增至應用程式.pkgundef 檔案套件的金鑰後面的項目。 索引鍵和項目都一樣.pkgdef 檔。也就是做為 [$RootKey$] 或 [$RootKey$\\*子機碼*] 和 「*項目*"=*值*，其中*子機碼*影響，子機碼*項目*是要移除的項目和*值*是`""`或`dword:00000000`。  
  
 若要排除的登錄機碼中的多個項目，只列出索引鍵一次，後面接著要排除的每個項目的行。  
  
 若要從獨立的 shell 應用程式排除整個登錄機碼，將金鑰加入至應用程式.pkgundef 檔，但未指定任何登錄機碼。  
  
 您可以在.pkgundef 檔案中加入註解。 單行註解必須有兩個斜線的前兩個字元。  
  
 例如，若要移除**連接至資料庫**和**連接到提供 r**上命令的**工具** 功能表中，行取消註解︰  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 並加入這一行︰  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 應用程式的.pkgundef 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 功能的封裝 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自訂獨立的 Shell](../extensibility/customizing-the-isolated-shell.md)
