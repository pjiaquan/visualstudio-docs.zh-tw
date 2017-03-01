---
title: "逐步解說︰ 發行 Visual Studio 擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
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
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>逐步解說︰ 發行 Visual Studio 擴充功能
本逐步解說會示範如何將 Visual Studio 擴充功能發行至 Visual Studio 組件庫。 當您將您的擴充功能加入組件庫時，開發人員可以使用**擴充功能和更新**瀏覽是否那里新的和更新的延伸模組。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="create-a-visual-studio-extension"></a>建立 Visual Studio 擴充功能  
 在此情況下，我們將使用預設 VSPackage 擴充功能，但相同的步驟都適用於所有類型的延伸模組。  
  
1.  在 C# 中名為建立 VSPackage`TestPublishing`具有功能表命令。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="test-the-extension"></a>測試擴充功能  
 發佈擴充功能之前，請建置及測試以確定已正確安裝 Visual Studio 的實驗執行個體中。  
  
1.  在 Visual Studio 中開始偵錯。 若要開啟的 Visual Studio 的實驗執行個體。  
  
2.  在實驗執行個體中，移至**工具**功能表，然後按一下**擴充管理員**。 TestPublishing 擴充功能應該會出現在中間窗格中，並啟用。  
  
3.  在**工具** 功能表上，請確定您看到測試命令。  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>發佈延伸至 Visual Studio 元件庫  
 現在您可以將擴充功能發行至 Visual Studio 組件庫。  
  
1.  請確定您已建立您的擴充功能的版本，而且它是最新狀態。  
  
2.  在網頁瀏覽器中，開啟 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=194329) 網站。  
  
3.  按一下右上角的 **登 IN**。  
  
4.  使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，您可以在此時建立一個。  
  
5.  按一下 [上傳] 。  
  
6.  在**步驟 1︰ 擴充功能類型**，請選取**工具**然後按一下 **下一步**。  
  
7.  在**步驟 2︰ 上傳**，您可以選擇直接上傳至 Visual Studio 組件庫，或只加入您自己的網站的連結。 在此情況下選取**我想要上傳我的工具**。 **選取您的控制項**方塊隨即出現。 按一下 **瀏覽**，然後選取 TestPublish.vsix \bin\Release 資料夾中的專案。 按 [下一步] 。  
  
8.  在**步驟 3︰ 基本資訊**，會顯示 source.extension.vsixmanifest 檔案的欄位。 選取適當**類別**，並新增**標記**可協助使用者尋找您的擴充功能。 若要新增更多詳細的摘要和描述 （描述必須至少 280 個字元）。 保留**延伸型別**為**不 Microsoft 擴充功能**和**成本類別**為**試用**。  
  
9. 讀取頁面的底部投稿協議，並檢查**我同意**。  
  
10. 按一下 **建立投稿文章**。 這會顯示您的擴充功能會對 Visual Studio 元件庫，以訊息尚未發行網頁的頁面。  
  
11. 按一下 [發行] 。  
  
12. 搜尋 Visual Studio 組件庫，您的擴充功能。 TestPublish 延伸模組的清單應該會出現。  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>安裝 Visual Studio 組件庫的擴充功能  
 發行延伸模組時，安裝 Visual Studio 中，並那里加以測試。  
  
1.  在 Visual Studio 中，在**工具**] 功能表上，按一下 [**擴充功能和更新**。  
  
2.  按一下 **線上**TestPublish 然後搜尋。 TestPublish 延伸模組的清單應該會出現。  
  
3.  按一下 [ **下載**]。 下載擴充功能之後，按一下 [安裝] 。  
  
4.  若要完成安裝，請重新啟動 Visual Studio。  
  
## <a name="removing-the-extension"></a>移除延伸模組  
 從 Visual Studio 組件庫和您的電腦，您可以移除擴充功能。  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>若要從 Visual Studio 組件庫中移除該擴充功能  
  
1.  開啟[Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkId=194329)網站。  
  
2.  在中心]，按一下 [ **My 擴充**。 TestPublish 清單隨即出現。  
  
3.  按一下 **刪除**。  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>若要從電腦移除擴充功能  
  
1.  在 Visual Studio 的 [工具]  功能表上，按一下 [擴充管理員] 。  
  
2.  選取 TestPublish，然後按一下**解除安裝**。  
  
3.  若要完成解除安裝，重新啟動 Visual Studio。

