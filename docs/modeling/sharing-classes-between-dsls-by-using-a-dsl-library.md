---
title: "使用 DSL 程式庫共用 DSL 之間的類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# 使用 DSL 程式庫共用 DSL 之間的類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]視覺化和模型的 SDK，您可以建立不完整的 DSL 定義，您可以匯入到另一個 DSL。  這可讓您列為重要因素的常見的組件的類似的模型。  
  
## 建立和使用 DSL 文件庫  
  
#### 若要建立 DSL 文件庫  
  
1.  建立新的 DSL 專案，然後選擇 DSL 文件庫\] 方案範本。  
  
     單一的 DSL 專案將會建立空白的模型。  
  
2.  您可以加入網域類別、 關聯性、 圖形等等。  
  
     媒體櫃中的項目並沒有以形成單一的內嵌樹狀目錄中。  
  
     若要定義一種關聯，可以使用 \[匯入工具，建立兩個網域類別並建立它們之間的關聯性。  
  
     請考慮設定**繼承修飾詞**的網域類別`Abstract`。  
  
3.  您可以新增您在 DSL 的總管\] 中，例如連接產生器中定義的項目。  
  
4.  您可以新增自訂項目需要額外的程式碼，這類的驗證條件約束。  
  
5.  按一下 \[ **轉換所有範本**。  
  
6.  建置專案。  
  
7.  當您散發的其他人使用 DSL 時，您必須同時提供已編譯的組件 \(DLL\) 以及檔案`DslDefinition.dsl`。  您可以找到\] 下的資料夾中的已編譯的組件`Dsl\bin\*`  
  
#### 若要匯入 DSL 文件庫  
  
1.  在另一個 DSL 定義中，在 **DSL 總管**，DSL 的根類別上按一下滑鼠右鍵，再按 **加入新的 DslLibrary 匯入**。  
  
2.  在 \[屬性\] 視窗中，設定**檔案路徑**程式庫。  您可以使用相對或絕對路徑。  
  
     匯入程式庫會出現在 DSL 總管中，以唯讀模式。  
  
3.  您可以使用 \[匯入的類別當做基底類別。  在網域中建立類別匯入的 DSL，並在 \[屬性\] 視窗中，將**基底類別**來匯入的類別。  
  
4.  按一下 \[轉換所有的範本。  
  
5.  DSL 專案中加入 DSL 程式庫專案所建置的組件 \(DLL\) 的參考。  
  
6.  建置方案。  
  
 DSL 文件庫，就可以匯入其他程式庫。  當您匯入程式庫，也會自動出現在 DSL 總管中的匯入。  
  
## 請參閱  
 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)