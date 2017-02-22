---
title: "逐步解說: 建立自訂編輯器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，自訂-建立"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 逐步解說: 建立自訂編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage 專案範本可以在 c \+ \+ 建立簡單的自訂編輯器。  VSPackage 專案範本已不再支援 C\# 或 Visual Basic 專案。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## Visual Studio 封裝專案範本  
 Visual Studio Package 專案範本位於 **新的專案** c \+ \+ 擴充性資料夾中的對話方塊  
  
### 若要建立使用 Visual Studio 封裝範本的 VSPackage  
  
1.  使用 Visual Studio 封裝範本建立專案。  
  
2.  選取 **自訂編輯器** 選項，然後按一下 **下一步**。**編輯器選項** \] 頁面隨即顯示。  
  
3.  輸入您的編輯器名稱 **編輯器名稱** 方塊。 輸入您想要與您的編輯器相關聯的副檔名 **副檔名** 方塊。 您的編輯器可供此副檔名的檔案。 副檔名會註冊為 Visual Studio，不適用於 Windows。 輸入您的編輯器以建立新的文件的預設檔案名稱 **預設檔名** 方塊。  
  
4.  按一下 \[完成\]，在您指定的資料夾中建立 VSPackage。  
  
### 若要測試您的自訂編輯器  
  
1.  在 **檔案** 功能表上，指向 **新增** 然後按一下 \[ **檔案**。  
  
2.  在 **已安裝的範本** 窗格 **新檔案** 對話方塊中，選取 \[檔案\] 範本，則檔案輸入您剛登錄。  
  
3.  按一下 \[ **開啟** 來檢視和編輯文件。  
  
     這個編輯器支援剪下和貼上、 尋找和取代及開啟與負載的作業。  
  
## 請參閱  
 [Vspackage](../extensibility/internals/vspackages.md)