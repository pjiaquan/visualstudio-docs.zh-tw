---
title: "在舊版語言服務中的程式碼重新格式化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
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
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>重新格式化舊版語言服務中的程式碼

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]來源程式碼可以被重新格式化的正規化使用縮排和空格。 這可以包括插入或移除空格或每一行的開頭的索引標籤、 加入新行之間的線條，或以索引標籤或索引標籤，以空格取代空格。  
  
>**注意︰**插入或刪除新行字元可能會影響標記，例如中斷點和書籤，但新增或移除空格或定位點不會影響標記。  
  
使用者可以選取啟動重新格式化作業**格式化選取範圍**或**格式化文件**從**進階**功能表**編輯**功能表。 插入程式碼片段或特殊字元時，可能也會觸發重新格式化作業。 比方說，當您鍵入右大括號在 C# 中，相符的左大括號和右大括弧之間的所有項目會自動縮排，以適當的層級。
  
當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]傳送**格式化選取範圍**或**格式化文件**命令語言服務的<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法的<xref:Microsoft.VisualStudio.Package.Source>類別。</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> 若要支援的格式設定，您必須覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法並提供您自己的格式化程式碼。</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>啟用支援重新格式化  

若要支援的格式，`EnableFormatSelection`參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>必須設為`true`當您註冊您的 VSPackage。</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 這會設定<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>屬性`true`。</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>方法會傳回這個屬性的值。</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> 如果為 true，傳回的<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會呼叫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>實作重新格式化

若要實作重新格式化，您必須衍生自<xref:Microsoft.VisualStudio.Package.Source>類別並覆寫<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>描述所要的格式和<xref:Microsoft.VisualStudio.Package.EditArray>物件會保存在範圍上進行的編輯</xref:Microsoft.VisualStudio.Package.EditArray>範圍的物件</xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 請注意，此範圍可以是整份文件。 不過，因為有可能是多個範圍的變更，所有的變更應該可在單一動作還原。 若要這樣做，換行中的所有變更<xref:Microsoft.VisualStudio.Package.CompoundAction>物件 （請參閱本主題中的 < 使用 CompoundAction 類別 > 一節）。</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>範例  

下列範例可確保有單一空格之後每個逗點中的選取項目，除非逗號後面按下 tab 鍵，或在一行的結尾。 刪除列中的最後一個逗號之後後, 端空格。 請參閱本主題，請參閱如何呼叫這個方法是從 「 使用 CompoundAction 類別 」 一節<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>方法。</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>使用 CompoundAction 類別  
 
所有重新格式化完成的程式碼區段應該可以還原以單一動作。 這可以透過<xref:Microsoft.VisualStudio.Package.CompoundAction>類別。</xref:Microsoft.VisualStudio.Package.CompoundAction> 這個類別會包裝成單一的編輯作業的編輯作業文字緩衝區上的一組。  
  
### <a name="example"></a>範例

以下是如何使用<xref:Microsoft.VisualStudio.Package.CompoundAction>類別</xref:Microsoft.VisualStudio.Package.CompoundAction>的範例 請參閱本主題的範例 「 實作支援的格式 」 一節的範例`DoFormatting`方法。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>另請參閱

[舊版的語言服務功能](legacy-language-service-features1.md)
