---
title: "逐步解說︰ 自訂文字檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
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
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>逐步解說︰ 自訂文字檢視
您可以藉由修改其編輯器格式對應中的下列屬性的任何自訂文字檢視︰  
  
-   指標邊界  
  
-   插入號  
  
-   覆寫插入號  
  
-   選取的文字  
  
-   非作用中選取的文字 （也就是選取的文字已遺失焦點）  
  
-   顯示空白  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為`ViewPropertyTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[編輯器項目範本以建立副檔名為](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="defining-the-content-type"></a>定義內容類型  
  
1.  將類別檔案，並將它`ViewPropertyModifier`。  
  
2.  新增下列`using`指示詞︰  
  
     [!code-cs[VSSDKViewPropertyTest&#1;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  宣告類別，名為`TestViewCreationListener`繼承自<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 匯出這個類別具有下列屬性︰  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>若要指定要套用此接聽程式的內容類型。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>若要指定此接聽程式的角色。</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[VSSDKViewPropertyTest&#2;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  在此類別中，匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[VSSDKViewPropertyTest&#3;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>變更檢視屬性  
  
1.  實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>方法，讓檢視開啟時，會變更檢視內容。</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 若要進行變更，請先找<xref:System.Windows.ResourceDictionary>對應於您想要尋找之檢視的外觀。</xref:System.Windows.ResourceDictionary> 然後變更資源字典中的適當屬性，並設定屬性。 若要呼叫的批次<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>方法藉由呼叫<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>方法之前設定的屬性，然後<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>設定屬性之後。</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[VSSDKViewPropertyTest&#4;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
  
1.  建置方案。  
  
     當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
2.  建立文字檔，並輸入一些文字。  
  
    -   插入號的洋紅色應該加以覆寫插入號淺粉藍色陰影。  
  
    -   指標邊界 （文字檢視的左邊） 應該是 light 綠色。  
  
3.  選取您剛才輸入的文字。 選取文字的色彩應該 light 粉紅色。  
  
4.  選取文字時，請按一下文字視窗外的任何位置。 選取文字的色彩應該深粉紅。  
  
5.  開啟可見的空白字元。 (在**編輯**功能表上，指向**進階**然後按一下 **檢視空白區**)。 某些索引標籤中輸入的文字。 應該會顯示紅色箭號代表索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
