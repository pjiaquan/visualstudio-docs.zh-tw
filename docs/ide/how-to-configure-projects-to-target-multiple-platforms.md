---
title: "如何：將專案設定成以多重平台為目標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "平台, 變更目標平台"
  - "專案 [Visual Studio], 針對平台"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：將專案設定成以多重平台為目標
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供讓方案一次以數個不同 CPU 架構或平台為目標的方式。  若要設定這些屬性透過存取**組態管理員**對話方塊。  
  
## 以平台為目標  
 \[**組態管理員**\] 對話方塊可讓您建立及設定方案等級和專案等級的組態與平台。  每一種方案等級組態與目標的組合，都可擁有一組與其相關聯的唯一屬性，讓您在例如以 [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] 平台為目標的發行組態、以 x86 平台為目標的發行組態，以及以 x86 平台為目標的偵錯組態之間輕鬆切換。  
  
#### 若要設定讓組態以不同的平台為目標  
  
1.  按一下 \[**建置**\] 功能表上的 \[**組態管理員**\]。  
  
2.  在 \[**使用中的方案平台方塊**\] 中，選取要做為方案目標的平台，或選取 \[**\<新增\>**\] 建立新平台。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]將編譯您的應用程式已設為 \[作用中的平台的平台為目標**組態管理員**對話方塊。  
  
## 移除平台  
 如果您確定不需要某個平台，可使用 \[組態管理員\] 對話方塊將它移除。  如此將移除您為該組態與目標組合設定的方案和專案設定。  
  
#### 若要移除平台  
  
1.  按一下 \[**建置**\] 功能表上的 \[**組態管理員**\]。  
  
2.  在 \[**使用中方案平台方塊**\] 中選取 \[**\<編輯\>**\]。  \[**編輯方案平台**\] 對話方塊便會開啟。  
  
3.  按一下要移除的平台，再按一下 \[**移除**\]。  
  
## 使用一個方案以多個平台為目標  
 由於您可以依據組態和平台設定的組合變更設定，因此可設定以多個平台為目標的方案。  
  
#### 若要以多個平台為目標  
  
1.  使用 \[**組態管理員**\] 針對方案至少加入兩個目標平台。  
  
2.  從 \[**使用中的方案平台**\] 清單中選取要做為目標的平台。  
  
3.  建置方案。  
  
#### 若要一次建置多個方案組態  
  
1.  使用 \[**組態管理員**\] 針對方案至少加入兩個目標平台。  
  
2.  使用 \[**批次建置**\] 視窗一次建置數個方案組態。  
  
 例如，您可以將方案等級的平台設為 [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]，且該方案中沒有以相同平台為目標的專案。  方案中也可以擁有多個專案，且各自以不同的平台為目標。  如果您的情況為上述其中一中，建議您使用描述性名稱建立新組態，以避免發生混淆。  
  
## 請參閱  
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)