---
title: "自動化模型概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>自動化模型概觀
Automation 模型包含一組您可以依據撰寫的 Visual Studio 增益集或延伸的物件。 增益集是應用程式會可以使用 Visual Studio 環境並自動化一般工作。 Visual Studio 擴充功能可以建立自訂的 Visual Studio 元件，或加入至標準元件，例如文字編輯器的功能。  
  
## <a name="objects-in-the-automation-model"></a>自動化模型中的物件  
 Automation 模型所組成之物件的控制主要面向，常見的環境的相關群組。 以下是圖表顯示一組更周延的撰寫 automation 模型的物件。  
  
 ![Visual Studio Automation 物件圖表](~/docs/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio automation 物件  
  
 如需詳細資訊，請參閱[擴充 Visual Studio 環境](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 環境提供不同功能區域的模型。 比方說，是各種項目，您可能會發現程式碼中的程式碼模型。 沒有文件模型的各種文件項目。 尤其 VSPackage 提供者是一個區域中，[專案] 區域中。 您可能會想要 automation 模型造成相同的方式為您新專案類型[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]變為 automation 模型。 處理序述[VSPackages 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)。  
  
 您可以考慮擴充自動化模型的環境的地方︰  
  
-   專案  
  
-   文件  
  
-   程式碼  
  
-   組建  
  
 如需自動化的詳細資訊，請參閱[自動化和擴充性 Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)。 這份文件和文件它提供連結，幫助您做出有關您應該在如何提供自動化的 VSPackage。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 建立增益集](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
