---
title: "專案類型 Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>專案類型的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包含數種專案類型的語言，例如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]也可讓您建立自己的專案類型。  
  
 如果您只想要新增自訂命令、 編輯器或工具視窗， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您就不需要建立新的專案類型。 如需詳細資訊，請參閱下列主題：  
  
-   [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同樣地，如果您想要自訂所提供的行為[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型中，您可以使用專案子類型。 如需詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
 您必須建立新的專案類型為基礎的一種語言以外的其他專案[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]如果您想要支援一或多個項目︰  
  
-   組建  
  
-   部署  
  
-   多個組態  
  
-   原始檔控制  
  
-   偵錯  
  
-   在 [方案總管] 中的專案項目  
  
-   **開啟專案**或**新的專案**對話方塊  
  
-   專案的巢狀結構  
  
-   如需詳細的專案類型功能的相關資訊，請參閱下列各項︰  
  
-   專案類型是在 VSPackage 中實作的介面集合的物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預期。 如果您使用 C# 來開發專案類型，管理封裝架構專案類別為您實作必要的介面，並可讓您繼承該實作。 如需詳細資訊，請參閱[使用管理套件架構實作專案型別 (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)。  
  
-   對於 c + + 開發人員，HierUtil 程式庫中的類別會在類似的方式。 如需詳細資訊，請參閱[不在建置中︰ 使用 HierUtil7 專案類別以實作專案類型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
-   專案類型可支援一般的原始程式碼檔建置為.exe 或.dll 的組件以外的資料。 例如，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]資料庫專案包含儲存在磁碟上的指令碼和查詢檔案的參考，並新增命令至**方案總管 中**執行指令碼和查詢資料庫，但專案不支援建置行為。 如需詳細資訊，請參閱[開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
-   若要使用的檔案沒有專案類型。 比方說，專案類型可以儲存在資料庫中的所有資料。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案類型可讓它們如何保存專案和專案項目資料的完整控制權。 如需詳細資訊，請參閱[專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
-   必須提供專案類型*專案 factory*，這是建立專案的執行個體的物件時輸入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]告訴開啟或建立該專案類型為基礎的專案。 如需詳細資訊，請參閱[建立專案執行個體所使用的專案工廠](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
-   專案類型都必須提供專案和專案項目範本。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]當使用者建立新的專案，並加入新項目至現有專案，請使用範本。 如需詳細資訊，請參閱[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
-   專案類型可支援多個組態，例如偵錯和發行。 使用者可以使用您提供的屬性頁變更專案的不同的組態。 如需詳細資訊，請參閱[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署專案類型](../../extensibility/internals/deploying-project-types.md)
