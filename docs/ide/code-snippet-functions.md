---
title: "程式碼片段函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼片段 [Visual Studio], 函式"
  - "IntelliSense 程式碼片段, 函式"
  - "片段 [Visual Studio], 函式"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 程式碼片段函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有三個函式可與 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 程式碼片段一起使用。  函式是在程式碼片段的 [Function](http://msdn.microsoft.com/zh-tw/572c5549-5821-4e15-8ecd-0fa86c1c65df) 項目中指定。  如需建立程式碼片段的詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。  
  
## 功能  
 下表將描述可與程式碼片段中的 `Function` 項目一起使用的函式。  
  
|Function|描述|Language|  
|--------------|--------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|會針對 `EnumerationLiteral` 參數所指定的列舉型別成員，產生一個 switch 陳述式以及一組 case 陳述式。  `EnumerationLiteral` 參數必須是列舉型別常值的參考或是列舉型別的參考。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|傳回其中包含插入的程式碼片段的類別名稱。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|將位於叫用程式碼片段之內容中的 *TypeName* 參數縮減為最簡單的形式。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## 範例  
 下列範例將說明如何使用 `GenerateSwitchCases` 函式。  如果插入此程式碼片段並且將列舉型別輸入至 `$switch_on$` 常值中，`$cases$` 常值將會針對列舉型別中的每一個值，產生一個 `case` 陳述式。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 範例  
 下列範例將說明如何使用 `ClassName` 函式。  插入這個程式碼片段時，`$classname$` 常值會由程式碼檔中您所在的封入類別 \(Enclosing Class\) 名稱取代。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 範例  
 這個範例將說明如何使用 `SimpleTypeName` 函式。  如果在程式碼檔中插入此程式碼片段，便會以叫用程式碼片段的內容中的 <xref:System.Console> 型別之最簡單形式取代 `$SystemConsole$` 常值。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 請參閱  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/zh-tw/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)