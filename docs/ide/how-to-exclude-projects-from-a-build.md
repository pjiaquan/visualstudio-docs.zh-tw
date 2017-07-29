---
title: "如何：從組建中排除專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: ab5283e92c8ab4bee74f9d6e3c7ae66e67b7a1e8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-exclude-projects-from-a-build"></a>如何：從組建中排除專案
您可以建置方案，而不建置它所包含的所有專案。 例如，您可能會排除會中斷組建的專案。 然後您可以在調查和處理這些問題之後才建置專案。  
  
 您可以利用下列方式排除專案：  
  
-   從作用中的方案組態暫時將其移除。  
  
-   建立不包含專案的方案組態。  
  
 如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>從作用中的方案組態暫時將專案移除  
  
1.  在功能表列上，選擇 [ **建置**]、[ **組態管理員**]。  
  
2.  在 [專案內容] 資料表中，找出您想要從組建排除的專案。  
  
3.  在專案的 [組建] 資料行中，清除核取方塊。  
  
4.  選擇 [關閉] 按鈕，然後重新建置方案。  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>建立排除專案的方案組態  
  
1.  在功能表列上，選擇 [ **建置**]、[ **組態管理員**]。  
  
2.  在 [使用中的方案組態] 清單中，選擇 [\<新增>]。  
  
3.  在 [名稱] 方塊中，輸入方案組態的名稱。  
  
4.  在 [複製設定來源] 清單中，選擇您要以其為新組態根據的方案組態 (例如，偵錯)，然後選擇 [確定] 按鈕。  
  
5.  在 [組態管理員] 對話方塊中，清除 [建置] 資料行中您想要排除之專案的核取方塊，然後選擇 [關閉] 按鈕。  
  
6.  在 [標準] 工具列上，確認新的方案組態是 [方案組態] 方塊中的使用中組態。  
  
7.  在功能表列上，依序選擇 [建置] 和 [重建方案]。  
  
## <a name="see-also"></a>另請參閱  
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [如何：同時建置多個組態](../ide/how-to-build-multiple-configurations-simultaneously.md)
