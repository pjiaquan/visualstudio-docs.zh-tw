---
title: "XslTransformation 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d240cca44bf389f97eaa7f4709690c0dc89cacc1
ms.lasthandoff: 02/22/2017

---
# <a name="xsltransformation-task"></a>XslTransformation 工作
使用 XSLT 或已編譯的 XSLT 來轉換 XML 輸入，並輸出到輸出裝置或檔案。  
  
## <a name="parameters"></a>參數  
 下表說明 `XslTransformation` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`OutputPaths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 轉換的輸出檔案。|  
|`Parameters`|選擇性的 `String` 參數。<br /><br /> 指定「XSLT 輸入」文件的參數。|  
|`XmlContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XML 輸入。|  
|`XmlInputPaths`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 輸入檔案。|  
|`XslCompiledDllPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定已編譯的 XSLT。|  
|`XslContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XSLT 輸入。|  
|`XslInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定 XSLT 輸入檔案。|  
  
## <a name="remarks"></a>備註  
 此工作除了有表格中所列的參數之外，還會從 <xref:Microsoft.Build.Tasks.TaskExtension> 類別繼承參數，而此類別本身則是從 <xref:Microsoft.Build.Utilities.Task> 類別繼承。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
