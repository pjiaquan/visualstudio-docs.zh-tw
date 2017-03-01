---
title: "使用 TextTransform 公用程式產生檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>使用 TextTransform 公用程式產生檔案
TextTransform.exe 是命令列工具可讓您轉換文字範本。 當您呼叫 TextTransform.exe 時，您可以指定文字範本檔案的名稱做為引數。 TextTransform.exe 呼叫文字轉換引擎，並處理文字範本。 TextTransform.exe 通常會從指令碼呼叫。 不過，它通常是必要的因為不在 Visual Studio 或在建置流程中，您可以執行文字轉換。  
  
> [!NOTE]
>  如果您想要執行文字轉換為建置流程的一部分，請考慮使用 MSBuild 文字轉換工作。 如需詳細資訊，請參閱[建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。 中的電腦上[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安裝時，您也可以撰寫應用程式或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以轉換文字範本的副檔名。 如需詳細資訊，請參閱[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)。  
  
 TextTransform.exe 位於下列目錄︰  
  
 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>語法  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>參數  
  
|**引數**|**說明**|  
|------------------|---------------------|  
|`templateName`|識別您想要轉換的範本檔案的名稱。|  
  
|**選項**|**說明**|  
|----------------|---------------------|  
|**-out** \<filename >|轉換的輸出寫入檔案。|  
|**-r** \<組件 >|用來編譯及執行文字範本組件。|  
|**-u** \<命名空間 >|用於編譯範本命名空間。|  
|**-I** \<includedirectory >|包含指定的文字範本中所包含的文字範本的目錄。|  
|**-P** \<重新整理路徑 >|要搜尋的文字範本中指定的組件，或使用的目錄**-r**選項。<br /><br /> 例如，若要包含 Visual Studio API 所使用的組件，使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName > ！\<className > ！\<assemblyName | 程式碼基底 >|名稱、 完整的型別名稱和組件可以用來處理文字範本內的自訂指示詞的指示詞處理器。|  
|**-a** [processorName] ！ [directiveName] ！\<parameterName > ！\<parameterValue >|指定參數值，指示詞處理器。 如果您指定參數名稱和值，此參數可指示詞的所有處理器。 如果您指定指示詞處理器，參數是僅適用於指定的處理器。 如果您指定指示詞的名稱，參數只能指定指示詞在處理時，才會出現。<br /><br /> 若要存取的參數值，指示詞處理器或文字範本中，使用<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> 在文字範本中，包括`hostspecific`在範本指示詞上叫用的訊息和`this.Host`。 例如：<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 一律使用類型 '！' 標示，即使您省略選擇性的處理器和指示詞的名稱。 例如：<br /><br /> `-a !!param!value`|  
|**-h**|提供說明。|  
  
## <a name="related-topics"></a>相關主題  
  
|工作|主題|  
|----------|-----------|  
|在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|  
|撰寫文字範本化主應用程式，可讓您叫用您自己的應用程式從文字範本。|[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)|
