---
title: "執行燈泡提示的快速動作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0f2747c233e820ca978c81d7ec98e40baf6dc45c
ms.lasthandoff: 02/22/2017

---
# <a name="perform-quick-actions-with-light-bulbs"></a>執行燈泡提示的快速動作
燈泡是 Visual Studio 中的提升生產力功能。 這些圖示出現在 Visual Studio 編輯器中，您可以按一下來執行重構修正錯誤等快速動作。 燈泡會將錯誤修正和重構協助帶到單一焦點中，通常就在您正在輸入的字行上。  

 ![小燈泡圖示](../ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall")  

 在 C# 和 Visual Basic 中，如果有紅色曲線，而且 Visual Studio 有針對如何修正問題的建議，您就會看到燈泡。 例如，如果紅色曲線指出一個錯誤，當該錯誤有可用的修正時，便會出現燈泡。 在 C++ 中，當您將新函式加入標頭檔時，就會看到所提供的燈泡，可用來建立該函式的虛設常式實作。 針對任何語言，協力廠商都可以提供自訂診斷和建議，例如做為 SDK 的一部分，而 Visual Studio 燈泡會依據這些規則亮燈。  

## <a name="to-see-a-light-bulb"></a>如何看到燈泡  

1.  在許多情況下，當您將滑鼠指標停留在錯誤點上方時，會自動出現燈泡；或者當您將插入號移到含有錯誤的字行時，會在編輯器左邊界出現燈泡。 當您看到紅色曲線時，可以將滑鼠暫留在其上方，即可顯示燈泡。 當您使用滑鼠或鍵盤前往發生問題之字行中的任何地方，也可以使燈泡顯示。  

2.  在字行任何地方按 **Ctrl+.**， 可叫用燈泡，直接前往可能的修正方法清單。  

 ![當滑鼠游標暫留時的燈泡](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

## <a name="to-see-potential-fixes"></a>如何看到可能的修正方法  
 按一下向下箭號或 [顯示可能的修正方法] 連結，就會顯示燈泡可以提供給您的快速動作清單。  

 ![放大的燈泡](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")  

## <a name="to-do-a-refactoring"></a>如何進行重構  
 您還是可以按滑鼠右鍵來顯示內容功能表，以執行重構，但您也可以按 Ctrl + . 來顯示重構選項。 在下列說明中，在包含 `Math.Abs` 呼叫的字行某處按下 Ctrl +. 之後，就會提供擷取方法重構：  

 ![顯示重構選項的燈泡](../ide/media/vs2015_lightbulbs_refactor.png "VS2017_LightBulbs_refactor")

