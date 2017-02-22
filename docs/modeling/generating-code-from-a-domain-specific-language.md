---
title: "從網域指定的語言產生程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 從網域指定的語言產生程式碼
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]提供了強大的方法，來從資料模型中表示產生程式碼、 文件、組態檔和其他成品。  使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，您可以建立一組類別，表示您的資料，您可以撰寫文字範本中的類別名稱和屬性反映該資料。  
  
 比方說，連結至 Fabrikam 有XML檔的客戶名稱和電子郵件地址。  他們開發人員建立在哪位客戶的模型是一種類別，屬性名稱與電子郵件。  寫入數個文字範本至流程的資訊，包括這個片段產生的HTML網頁的一部分的所有客戶資料表：  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 處理客戶資料庫時，會將XML檔案讀入模型存放區。  A *指示詞處理器*、 藉由建立[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，讓文字範本中的程式碼可以使用 「 客戶 」類別。可以針對相同的存放區中執行許多文字範本。  
  
 文字範本是為了[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。  它們用來產生來源程式碼，以領域模型也為 VSPackage 和控制項整合與工具所使用之項目的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 本章節將告訴您幾種方法來建立、 修改和偵錯文字範本中使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。  
  
## 在本節中  
 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)  
  
 提供有關指的文字範本中的網域指定的語言的基本資訊。  
  
 [逐步解說：偵錯存取模型的文字範本](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 說明如何進行疑難排解，以及 \[網域指定的語言是指某文字範本中的 \[偵錯。  
  
 [逐步解說：將主機連接至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 說明如何連線產生的指示詞處理器到自訂主機。  
  
 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)  
  
 描述在 TextTransform可執行檔執行命令列文字範本該參考定義域專屬語言指令檔。  
  
## 參考  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
  
 提供文字範本指示詞及控制區塊的語法。  
  
## 相關章節  
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 說明文字範本轉換流程。  
  
 [建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)  
  
 若要從 DSL組建伺服器上產生的檔案，請閱讀本主題。