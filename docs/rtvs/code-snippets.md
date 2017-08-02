---
title: "使用 Visual Studio R 工具的程式碼片段 | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>程式碼片段

在 Visual Studio 中的程式碼片段提供捷徑，以便快速地插入任意長度的程式碼區塊，協助您避免一再重新輸入類似的程式碼。 Visual Studio R 工具 (RTVS) 將數十個有用的 R 程式碼片段新增至 Visual Studio 的集合。

若要插入程式碼片段，請輸入程式碼片段的縮寫名稱 (提供 IntelliSense)，然後按 Tab 鍵插入。

一些簡單的範例︰

- 鍵入 `=` 然後按 Tab 鍵，RTVS 會將它展開至 `<-` 指派運算子。
- 鍵入 `>` 然後按 Tab 鍵，RTVS 會將它展開至 `%>%` 管道運算子。

程式碼片段可以不單單只是字元的字元完成。 例如，它們可以讓您不必記住複雜函式呼叫中的參數名稱，例如這個用來以 `read.csv` 函式讀取 CSV 檔案的程式碼片段︰

![使用程式碼片段將呼叫插入 read.csv 的動畫](~/rtvs/media/code-snippet-expansion.gif)

在此情況下，當您輸入 `readc` 時，IntelliSense 會顯示完成清單。 在下拉式清單中選取該完成，然後按 Tab 鍵即可選取 `readc`，再次按 Tab 鍵則會展開程式碼片段。 (基於這個理由，程式碼片段展開經常被視為「鍵入程式碼片段，並按 TAB 鍵兩次」)。 在大部分情況下，第一次按 Tab 鍵會完成 IntelliSense 選取範圍，而第二次按 Tab 鍵則會觸發展開。

若要查看所有可用的片段，請開啟 [工具] > [程式碼片段管理員] 對話方塊 (Ctrl + K、B)，然後針對 [語言] 選取 [R]。 展開群組，然後選取個別的程式碼片段，即可看到描述和快顯文字︰

![R 的 [程式碼片段] 對話方塊](~/rtvs/media/code-snippet-dialog.png)

若要建立自訂程式碼片段，並遵循[逐步解說︰建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)上的指示。 最後，程式碼片段只是一個 XML 檔案。 例如，以下是管道作業的程式碼片段 (捷徑 `>`)

請注意，程式碼片段只是一個 XML 檔案。以下是管道運算子的程式碼片段︰

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

所有程式碼片段的 XML 檔案會與 RTVS 一起安裝，[程式碼片段管理員] 的 [位置] 欄位中提供了路徑。 您也可以在 GitHub 之 [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets) 下的 RTVS 原始程式碼中找到它們。

