---
title: "Shell （獨立或整合） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
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
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell （獨立或整合）
您可以建立自己的 Visual Studio 為基礎應用程式中整合或隔離模式。 在整合模式中，Visual Studio 使用的許多功能除了您的應用程式。 在隔離模式中，您可以選擇您想要發佈，以及您自己的擴充功能的 Visual Studio 功能的子集。  
  
## <a name="integrated-mode"></a>整合的模式  
 整合式的模式可讓使用者在使用標準的 Visual Studio 功能，以及您的自訂工具。 整合式的 shell 主要被供主控的程式設計語言和軟體開發工具。  
  
 整合式 shell 所自動建立的自訂工具合併與任何其他版本的 Visual Studio 安裝在同一部電腦上。 如果尚未安裝 Visual Studio，您可以提供 Visual Studio 整合式 shell 可轉散發版本。  
  
 Visual Studio 整合式 shell 可轉散發套件版本不包含程式設計語言和支援個別專案系統的功能。  
  
> [!NOTE]
>  Visual Studio shell 整合的模式可以與 Visual Studio Express 版本以外的所有版本一起安裝。  
  
 如需詳細資訊，請參閱[Visual Studio Shell （整合模式）](../extensibility/visual-studio-shell-integrated.md)。  
  
## <a name="isolated-mode"></a>獨立的模式  
 獨立的模式可讓您建立自訂工具執行的並行與其他版本的 Visual Studio。 它主要被供可存取 Visual Studio 服務，而根據標準的 Visual Studio 功能的工具。 您可以自訂 Visual Studio 隔離 shell 建置的應用程式的外觀。 您可以輕鬆地關閉不想要顯示與您的應用程式的功能表命令群組的功能。  
  
 如需詳細資訊，請參閱[Visual Studio 隔離 Shell](../extensibility/visual-studio-isolated-shell.md)。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>散發應用程式整合或隔離 Shell  
 若要散發應用程式整合或 「 外掛式介面，您必須包括您的應用程式、 特殊整合或隔離 shell 可轉散發套件，以及安裝程式。 如需有關散發與安裝的詳細資訊，請參閱[散發隔離 Shell 應用程式](../extensibility/distributing-isolated-shell-applications.md)。  
  
> [!IMPORTANT]
>  [使用者授權合約 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) shell 的 Visual Studio 整合並隔離包括資料集合上的一節 (**區段 3。Data**).  它會描述可能會由 Microsoft 的整合式或外掛式主控殼層軟體，您建置到您的應用程式的使用者收集的客戶使用量資料。 如需詳細資訊，請參閱[Microsoft Visual Studio 產品系列隱私權聲明](https://www.visualstudio.com/en-us/dn948229)。  
>   
>  如果您的應用程式透過個別的使用量資料收集客戶中，您必須提供適當通知您的應用程式收集對象的使用者。  當您發佈隔離或整合式 shell 軟體做為應用程式的一部分，根據 Visual Studio 軟體開發套件授權，您必須包含下列其中一項︰  
>   
>  -   使用者授權合約，做為您的應用程式授權的一部分  
> -   需要您的客戶同意保護 Visual Studio 中的條款自己 EULA 整合 或 Microsoft 使用者授權條款，殼層以軟體為隔離 shell 程度  
  
## <a name="additional-resources"></a>其他資源  
 如需可轉散發套件的詳細資訊，請參閱[Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="see-also"></a>另請參閱  
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
