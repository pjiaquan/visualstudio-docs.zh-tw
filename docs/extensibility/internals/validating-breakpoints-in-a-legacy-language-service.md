---
title: "驗證舊版語言服務中的中斷點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
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
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>驗證舊版語言服務中的中斷點
中斷點會指出偵錯工具正在執行時，應該特定時間點停止程式執行。 使用者可以在原始程式檔中的任一行上放置中斷點，因為編輯器並不知道何者構成有效的位置中斷點。 啟動偵錯工具時，所有標記 （稱為暫止中斷點） 的中斷點繫結至執行中的程式中的適當位置。 同時驗證中斷點，以確保它們可以將有效的程式碼位置來標示。 例如，註解上的中斷點無效，因為沒有程式碼的原始程式碼中該位置。 偵錯工具停用無效的中斷點。  
  
 語言服務知道所顯示的原始碼，因為它可以在偵錯工具啟動前驗證中斷點。 您可以覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法來傳回指定中斷點的有效位置的範圍。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 啟動偵錯工具時，但不需等到偵錯工具載入通知使用者的無效的中斷點時，仍會進行驗證中斷點的位置。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>實作支援驗證的中斷點  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法指定之中斷點的位置。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 您的實作必須決定位置有效，以及指出這是傳回識別程式碼的文字範圍相關聯的行位置中斷點。  
  
-   傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>是否有效、 位置或<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>如果不正確。</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   如果中斷點是有效的文字範圍會反白顯示中斷點以及。  
  
-   如果中斷點是無效的則會在狀態列中顯示錯誤訊息。  
  
### <a name="example"></a>範例  
 這個範例會示範實作<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>方法呼叫 （如果有的話），取得一段程式碼剖析器在指定的位置。</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 這個範例假設您已新增`GetCodeSpan`方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別所驗證的文字範圍和傳回`true`如果它是有效的中斷點位置。</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
