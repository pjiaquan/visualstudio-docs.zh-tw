---
title: "精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
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
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>精靈
建立精靈之後，您通常想要將它加入至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE)，好讓其他人可以使用它。 加入的精靈接著會出現在**加入新的專案**或**加入新項目**對話方塊。 若要查看**加入新的專案**或**加入新項目**對話方塊方塊中，開啟方案中的以滑鼠右鍵按一下**方案總管] 中**，指向**新增**，然後按一下 [**新的專案**或**新項目**。  
  
 精靈可以實作在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，讓使用者選取樹狀結構檢視中開啟時的可用值**加入新的專案**對話方塊或**加入新項目**對話方塊中，當它們以滑鼠右鍵按一下中的項目或**方案總管 中**。  
  
 在精靈中，您可以提供當地語系化的新專案或輕鬆，名稱的選項，您可以決定當使用者選取精靈時，會看到的圖示。 您也可以控制相對於其他可用的項目; 新的項目出現的順序項目沒有依照字母順序排列。  
  
 您也可以提供一個精靈，以不同的方式，開始根據開啟時傳遞給精靈的自訂參數。  
  
 本章節的主題將討論，讓您實作的檔案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**加入新的專案**和**加入新項目**對話方塊中，若要列出您的精靈之間可用的精靈和範本，與您的精靈必須符合在 IDE 中正常運作的需求。  
  
## <a name="in-this-section"></a>本章節內容  
 [範本目錄描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 提供概觀，哪一個範本目錄描述檔案，並說明在 IDE 中顯示資料夾、 精靈.vsz 檔案和相關聯的專案 對話方塊中的範本檔案如何函式。  
  
 [精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)  
 說明如何在 IDE 啟動精靈，並列出.vsz 檔案中的三個部分。  
  
 [精靈介面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 描述`IDTWizard`精靈必須在 IDE 中工作實作的介面。  
  
 [內容參數](../../extensibility/internals/context-parameters.md)  
 說明如何實作精靈以及時發生 IDE 會將內容參數傳遞的實作。  
  
 [自訂參數](../../extensibility/internals/custom-parameters.md)  
 說明如何使用自訂參數來控制精靈的作業之後則會啟動精靈。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供額外的主題提供有關如何設計新的專案類型的資訊連結。  
  
 [逐步解說︰ 建立精靈](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 說明如何建立精靈。  
  
 [擴充專案](../../extensibility/extending-projects.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案和方案來組織程式碼檔案和資源檔案，以及如何實作原始檔控制。
