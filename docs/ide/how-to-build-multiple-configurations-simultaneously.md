---
title: "如何：同時建置多個組態 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：同時建置多個組態
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 \[**批次建置**\] 對話方塊同時建置具有多個甚至全部組建組態的多數類型的專案。  不過，您無法同時在多個組建組態中組建下列類型的專案：  
  
1.  [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式是使用 JavaScript 針對 Windows 建置。  
  
2.  所有 Visual Basic 專案。  
  
 如需建置組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
### 在多個組建組態中建置專案  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**批次建置**\]。  
  
2.  在 \[**建置**\] 欄中，選取您要建置專案的組態核取方塊。  
  
    > [!TIP]
    >  若要編輯或建立方案的建置組態，請選擇功能表列上的 \[**建置**\]、\[**組態管理員**\] 以開啟 \[**組態管理員**\] 對話方塊。  在您編輯方案的建置組態之後，請在 \[**批次建置**\] 對話方塊中選擇 \[**重建**\] 按鈕，來更新方案中專案的所有建置組態。  
  
3.  選擇 \[**建置**\] 或 \[**重建**\] 按鈕，以使用您指定的組態建置專案。  
  
## 請參閱  
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)