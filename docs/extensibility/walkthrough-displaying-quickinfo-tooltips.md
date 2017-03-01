---
title: "逐步解說︰ 顯示 QuickInfo 工具提示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
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
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>逐步解說︰ 顯示 QuickInfo 工具提示
QuickInfo 是 IntelliSense 功能，以顯示方法簽章，說明當使用者將指標移方法名稱。 您可以實作語言為基礎的功能，例如 QuickInfo 定義您要提供 QuickInfo 描述的識別碼，然後再建立要顯示的內容中的工具提示。 您可以定義 QuickInfo 中的內容語言服務，您可以定義您的檔案名稱副檔名和內容類型，並顯示只是該型別的 QuickInfo 或對於現有的內容類型 （例如 「 文字 」），您可以顯示 QuickInfo。 本逐步解說示範如何顯示 QuickInfo 「 文字 」 內容類型。  
  
 當使用者將指標移方法名稱，在這個逐步解說 QuickInfo 則會顯示工具提示。 此設計會要求您實作這些介面，四個︰  
  
-   來源介面  
  
-   來源提供者介面  
  
-   控制器介面  
  
-   控制站提供者介面  
  
 來源和控制站的提供者是 Managed Extensibility Framework (MEF) 元件組件，而且負責匯出來源和控制器類別和匯入服務，並不會如代理人<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，這樣就可以建立工具提示文字緩衝區，而<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>，而觸發 QuickInfo 工作階段。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 在此範例中，QuickInfo 來源會使用硬式編碼清單的方法名稱和描述，但在完整的實作中，語言服務和語言文件是負責提供該內容。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為`QuickInfoTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[編輯器項目範本以建立副檔名為](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="implementing-the-quickinfo-source"></a>實作 QuickInfo 來源  
 QuickInfo 來源負責收集一組識別項和其描述和內容加入工具提示文字緩衝區時遇到的其中一個識別碼。 在此範例中，識別項和其說明剛加入來源建構函式。  
  
#### <a name="to-implement-the-quickinfo-source"></a>若要實作 QuickInfo 來源  
  
1.  將類別檔案，並將它`TestQuickInfoSource`。  
  
2.  加入 Microsoft.VisualStudio.Language.IntelliSense 的參考。  
  
3.  新增下列匯入。  
  
     [!code-vb[VSSDKQuickInfoTest&#1;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  宣告類別可實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>，並將其命名`TestQuickInfoSource`。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  將欄位加入 QuickInfo 來源提供者、 文字緩衝區，和一組方法名稱和方法簽章。 在此範例中，方法名稱和簽章會在初始化`TestQuickInfoSource`建構函式。  
  
     [!code-vb[VSSDKQuickInfoTest&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  新增的建構函式設定 QuickInfo 來源提供者和文字緩衝區，並於其中填入一組方法名稱和方法簽名碼和描述。  
  
     [!code-vb[VSSDKQuickInfoTest&#4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>方法。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 在此範例中，此方法會尋找目前的文字或前一個字如果游標位於線條或文字緩衝區的結尾。 如果文字是其中一個方法名稱，該方法名稱的描述會加入 QuickInfo 內容。  
  
     [!code-vb[VSSDKQuickInfoTest&#5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  您也必須實作 dispose （） 方法，因為<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>實作<xref:System.IDisposable>::</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&#6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>實作 QuickInfo 來源提供者  
 QuickInfo 來源提供者做主要是為了做為 MEF 元件組件來匯出自己並具現化 QuickInfo 來源。 因為它是 MEF 元件組件時，它可以匯入其他 MEF 元件組件。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>若要實作 QuickInfo 來源提供者  
  
1.  宣告名為 QuickInfo 來源提供者`TestQuickInfoSourceProvider`實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 工具提示 QuickInfo 來源 」，<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的之前 = 「 預設 」，和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  匯入兩個編輯器服務，<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>和<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>，以做為屬性`TestQuickInfoSourceProvider`。</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>來傳回新`TestQuickInfoSource`。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>實作 QuickInfo 控制器  
 QuickInfo 控制站會決定何時應該顯示 QuickInfo。 在此範例中，透過對應至其中一個方法名稱的文字指標時，會顯示 QuickInfo。 QuickInfo 控制器實作觸發程序 QuickInfo 工作階段的滑鼠停留事件處理常式。  
  
#### <a name="to-implement-a-quickinfo-controller"></a>若要實作 QuickInfo 控制器  
  
1.  宣告類別可實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>，並將其命名`TestQuickInfoController`。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  加入私用欄位的 [文字] 檢視中，以表示文字檢視、 QuickInfo 工作階段，並 QuickInfo controller 提供者的文字緩衝區。  
  
     [!code-vb[VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  新增設定欄位並將滑鼠停留事件處理常式的建構函式。  
  
     [!code-vb[VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  新增觸發程序 QuickInfo 工作階段的滑鼠停留事件處理常式。  
  
     [!code-vb[VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>方法，使它當控制器中斷連結的文字檢視時，請移除滑鼠停留事件處理常式。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>方法和<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>方法，此範例中的空白方法。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>實作 QuickInfo 控制器提供者  
 QuickInfo 控制站的提供者做主要是為了做為 MEF 元件組件來匯出自己並具現化 QuickInfo 控制站。 因為它是 MEF 元件組件時，它可以匯入其他 MEF 元件組件。  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>若要實作 QuickInfo controller 提供者  
  
1.  宣告類別，名為`TestQuickInfoControllerProvider`實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的 「 工具提示 QuickInfo 控制器 」 及<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」:</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  匯入<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>做為屬性。</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[VSSDKQuickInfoTest&#17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>方法具現化 QuickInfo 控制站。</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，QuickInfoTest 方案中建置並執行它的實驗執行個體。  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>若要建置和測試 QuickInfoTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔並輸入一些文字，其中包含單字 「 加入 」 和 「 減去 」。  
  
4.  將指標放在一個 「 加入 」 的項目。 簽章和描述`add`方法應該會顯示。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
