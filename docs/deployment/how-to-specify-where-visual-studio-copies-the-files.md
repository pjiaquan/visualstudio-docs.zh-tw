---
title: "如何：指定 Visual Studio 複製檔案的位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "發行位置屬性"
  - "發行, 指定位置"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：指定 Visual Studio 複製檔案的位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您使用 ClickOnce 發行應用程式時，`Publish Location`屬性會指定放置應用程式檔案和資訊清單的位置。  這可以是檔案路徑或 FTP 伺服器的路徑。  
  
 您可以在 \[專案設計工具\]`Publish Location` 的 \[發行\] 頁面上，或使用 \[發行精靈\] 來指定**屬性。** 如需詳細資訊，請參閱[如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
> [!NOTE]
>  當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。  以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。  
  
### 指定發行位置  
  
1.  在 \[方案總管\] 中選取的專案上，請按一下 \[專案\] 功能表中 \[屬性\]。  
  
2.  按一下 \[發行\] 索引標籤。  
  
3.  在 \[發行位置\] 欄位中，使用下列其中一種格式輸入發行位置：  
  
    -   若要發行至檔案共用或磁碟路徑，請使用 UNC 路徑 \(\\\\Server\\ApplicationName\) 或檔案路徑 \(C:\\Deploy\\ApplicationName\) 來輸入路徑。  
  
    -   若要發行至 FTP 伺服器，請使用 ftp:\/\/ftp.microsoft.com\/ApplicationName 格式來輸入路徑。  
  
     請注意，文字必須出現在 \[發行位置\] 方塊中才能讓 \[瀏覽\] \(**...**\) 按鈕運作。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)