---
title: "專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
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
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>專案
在 Visual Studio 中，專案是開發人員用來組織原始程式碼檔和其他資源，會出現在容器**方案總管 中**。 一般而言，專案是檔案 （例如，C# 專案的.csproj 檔案） 儲存到原始程式碼檔案和資源，例如點陣圖檔案的參考。 專案可讓您組織、 建置、 偵錯及部署程式碼，請參考 Web 服務和資料庫，而且其他資源。 VSPackages 可以擴充 Visual Studio 專案系統以三種主要方式︰*專案類型*，*專案子類型*，和*自訂工具*。  
  
## <a name="in-this-section"></a>本章節內容  
 [專案類型](../../extensibility/internals/project-types.md)  
 *專案類型*加入新種類的專案，例如的程式設計語言的支援。 例如，Visual Studio 支援每種語言有它自己的專案類型，以及 IronPython 整合範例 IronPython 語言的專案類型。 您必須建立的專案類型以外的 C# 或 Visual Basic 自訂如何項目會建置、 偵錯、 部署，並顯示在其他語言**方案總管 中**。 如需詳細資訊，請參閱[專案類型](../../extensibility/internals/project-types.md)。  
  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 *專案的子型別*專案類型為基礎，而且可用以自訂建置、 偵錯和部署專案的方式。 Visual Studio 專案子類型使用智慧型裝置專案的專案。他們藉由將新建立的程式從開發電腦複製到目標裝置自訂部署。 C# 和 Visual Basic 專案類型可用來當做基礎的專案子類型。C + + 專案類型不能。 您自己的專案類型也可用做為基礎的專案子類型。 如需詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
 [Web 專案](../../extensibility/internals/web-projects.md)  
 說明 Web 專案，依序建立 Web 應用程式。  
  
 [新產生的專案︰ 在幕後，第一部](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)和[產生新的專案︰ 在幕後，第二部](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 說明實際發生的狀況時建立新的專案。  
  
 [VSSDK 範例](../../misc/vssdk-samples.md)  
 描述處理專案和方案中的 VSSDK 範例。  
  
## <a name="related-sections"></a>相關章節  
 [在 Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 說明 Visual Studio 擴充性的不同層面。
