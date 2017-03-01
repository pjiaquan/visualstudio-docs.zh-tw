---
title: "在舊版語言服務中的導覽列的支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>在舊版語言服務中的導覽列的支援
在編輯器檢視頂端的導覽列會顯示檔案中的類型和成員。 在左側下拉式清單，會顯示類型和成員會顯示在右側下拉式清單。 當使用者選取型別時，插入號會放在第一行的型別。 當使用者選取成員時，會將插入號放在成員的定義。 下拉式清單方塊會更新以反映目前插入號位置。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>顯示和更新的巡覽列  
 若要支援的瀏覽列，您必須衍生自<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，並實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 語言服務提供程式碼視窗中，基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別具現化<xref:Microsoft.VisualStudio.Package.CodeWindowManager>，其中包含<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>物件，表示程式碼視窗。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CodeWindowManager>物件接著會提供一個新的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法取得<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 如果傳回的執行個體您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼叫您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法填入的內部清單，並傳遞您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件傳遞給[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下拉式清單列 manager。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 下拉式清單列管理員 中，接著呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>方法您<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件來建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>保存兩個下拉式清單列的物件。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 當插入號移時，<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法。</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>方法會呼叫<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>您的<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別來更新導覽列的狀態</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>中的方法</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A></xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>基底 通過一系列<xref:Microsoft.VisualStudio.Package.DropDownMember>這個方法的物件。</xref:Microsoft.VisualStudio.Package.DropDownMember> 每個物件都代表下拉式清單中的項目。  
  
## <a name="the-contents-of-the-navigation-bar"></a>導覽列的內容  
 巡覽列通常包含一份類型和成員的清單。 型別的清單目前的原始程式檔中包含所有可用的類型。 型別名稱中包含完整的命名空間資訊。 兩種類型的 C# 程式碼範例如下︰  
  
```c#  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 [類型] 清單會顯示`TestLanguagePackage.TestLanguageService`和`TestLanguagePackage.TestLanguageService.Tokens`。  
  
 成員清單會顯示在 [類型] 清單中選取的型別可用的成員。 如果使用上述程式碼範例`TestLanguagePackage.TestLanguageService`是已選取的型別成員的清單會包含私用成員`tokens`和`serviceName`。 內部結構`Token`不顯示。  
  
 您可以實作成員清單插入號放置於它時讓成員的名稱變成粗體。 成員可以也會顯示在文字呈現灰色，表示它們不目前位置插入號範圍內。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>啟用支援的瀏覽列  
 若要啟用瀏覽列的支援，您必須設定`ShowDropdownBarOption`參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性設定為`true`。</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 這個參數會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>屬性。</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 若要支援的瀏覽列，您必須實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars><xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類別</xref:Microsoft.VisualStudio.Package.LanguageService>方法</xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>中的物件</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 在您<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>方法中，如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>屬性設定為`true`，您可以傳回<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>物件。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 如果您不會傳回物件，不會顯示導覽列。  
  
 使用者可以設定選項，以顯示瀏覽列，因此很可能對這個控制項，開啟 [編輯器] 檢視時，若要重設。 使用者必須關閉並重新開啟 [編輯器] 視窗中，變更才會發生。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>實作支援導覽列  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法會採用兩個 list （一個用於每個下拉式清單） 和兩個值代表每個清單中目前的選取範圍。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 清單和選取項目值可以更新，在此情況下<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法必須傳回`true`，表示清單已變更。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 隨著選取範圍的變更類型下拉式清單中，[成員] 清單必須更新以反映新的類型。 在 [成員] 清單中顯示的內容可以是︰  
  
-   目前的型別成員的清單。  
  
-   中的所有成員提供來源檔案，但與不在目前的型別中的所有成員，以灰色文字顯示。 使用者仍然可以選取灰色的成員，因此可用於快速導覽，但是色彩表示它們不是目前所選類型的一部分。  
  
 實作<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法通常會執行下列步驟︰</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  取得原始程式檔的目前宣告的清單。  
  
     有數種方法來填入清單。 其中一個方法是在您的版本上建立的自訂方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會傳回一份所有宣告自訂剖析原因。</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> 另一種方法可能會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法直接從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法以自訂剖析原因。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 第三種方法可能會快取中的宣告<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別中的最後一個完整剖析作業所傳回<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並擷取從<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  填入或更新的類型清單。  
  
     當變更來源，或如果您已選擇要變更文字樣式，根據目前插入號位置類型的更新，可能的型別清單的內容。 請注意，這個位置會傳遞至<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法。</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  決定要在目前插入號位置為基礎的型別清單中選取類型。  
  
     您可以在步驟 1，尋找內含目前插入號位置中，型別中搜尋所取得的宣告，然後搜尋 該類型來判斷其索引類型清單中的型別清單。  
  
4.  填入或更新的成員根據選取的類型清單。  
  
     [成員] 清單會反映目前顯示的內容中**成員**下拉式清單。 [成員] 清單的內容可能需要更新來源已變更，或如果您要顯示所選類型的成員，而變更選取的類型。 如果您選擇要顯示原始程式檔中的所有成員，文字的樣式清單中的每個成員必須更新目前選取的型別已變更。  
  
5.  決定要根據目前插入號位置的 [成員] 清單中選取的成員。  
  
     搜尋的成員，其中包含目前插入號位置，在步驟 1 中所取得的宣告，然後搜尋 [成員] 清單，該成員，以判斷其索引為成員的清單。  
  
6.  傳回`true`如果任何已變更的清單或任一個清單中的選取項目。
