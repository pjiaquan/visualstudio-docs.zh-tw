---
title: "逐步解說︰ 將自訂的 XAML 加入至 [開始] 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c19658e44daf96b6db96c503de1b59127b673111
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>逐步解說︰ 將自訂的 XAML 加入至 [開始] 頁面
本逐步解說示範如何建立自訂 Visual Studio 起始頁，其中包含 Web 瀏覽器。  
  
## <a name="adding-custom-xaml"></a>新增自訂的 XAML  
  
1.  依照下列中的指示來建立起始頁面[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在 MainWindow.xaml 檔案中，尋找\<方格 > 一節。  
  
3.  新增\<TabControl > 項目和\<TabItem > 內\<方格 > 項目，如下列範例所示。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  新增第二個\<TabItem >，以\<按鈕 > 會開啟新專案的項目︰  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>測試自訂起始頁  
  
1.  按 F5。  
  
     Visual Studio 的實驗執行個體隨即開啟，並自訂起始頁安裝但未選取。  
  
2.  在 Visual Studio 的實驗執行個體，開啟**工具 /Options / 環境**頁面。  
  
3.  選取**啟動**。 在**自訂起始頁**清單中，選取您.xaml 檔案，然後按一下**確定**。  
  
4.  在 [檢視]  功能表上，按一下 [起始頁] 。  
  
5.  按一下 [ **Bing** ] 索引標籤。  
  
     您應該會看到 Bing 網頁。  
  
6.  按一下 [ **MyButton** ] 索引標籤。  
  
     您應該會看到**MyProject**  按鈕，這會開啟**新的專案** 對話方塊。  
  
7.  關閉此實驗執行個體。  
  
## <a name="applying-the-custom-start-page"></a>套用自訂起始頁  
  
#### <a name="to-test-the-custom-start-page"></a>若要測試自訂起始頁  
  
1.  在**工具 / 選項 / 環境**，請選取**啟動**。 在**自訂起始頁**清單中，選取您.xaml 檔案，然後按一下**確定**。  
  
## <a name="next-steps"></a>後續步驟  
 Visual Studio 起始頁現在包含 Web 瀏覽器索引標籤和 MyButton 索引標籤會顯示索引標籤。 您可以建立自訂頁面起始位置，讓其他功能使用*程式碼後置*模型中所示，新增自訂.dll [[入門] 頁面將使用者控制項](../extensibility/adding-user-control-to-the-start-page.md)。 您也可以發佈結果.vsix 檔，以與其他使用者共用自訂頁面起始[Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，或另一個網站或網路共用。 如需詳細資訊，請參閱[部署自訂頁面起始位置](../extensibility/deploying-custom-start-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF 容器控制項](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
