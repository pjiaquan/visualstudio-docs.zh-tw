---
title: "編碼與分行符號 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "編輯器, 分行"
  - "編碼"
  - "分行符號字元"
  - "分行"
  - "Visual Studio, 編碼"
  - "Visual Studio, 分行符號字元"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# 編碼與分行符號
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中，您可以使用**檔案\/進階儲存選項**設定，決定自動換行的型別字元您要的。  您也可以變更檔案的編碼方式與相同的設定。  
  
> [!NOTE]
>  如果您有特定類型的開發設定 \(Visual Basic，F\# 中，Web 程式開發\) 您可能看不到**進階儲存選項**在功能表上。  若要變更您的設定 \(例如一般\)，請開啟**工具 \/ 匯入和匯出設定**。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 在 Visual Studio 中的下列的字元會被解譯為換行：  
  
-   CRLF：歸位字元 \+ 換行字元，即 Unicode 字元 000 D \+ 000A  
  
-   LF：換行字元，即 Unicode 字元 000A  
  
-   NEL：次行字元 \(下一步直線\)，即 Unicode 字元 0085  
  
-   LS：行分隔符號，即 Unicode 字元 2028年  
  
-   PS：段落分隔符號，即 Unicode 字元 2029年  
  
 從其他應用程式複製的文字會保留原始編碼和分行符號字元。  例如，當您從記事本複製文字，並將它貼到文字檔案，在 Visual Studio 中，文字會有相同原先 「 記事本 」 中的設定。  
  
 當您開啟具有不同的線條分行符號字元的檔案時，您可能會看到一個對話方塊，詢問是否應該正規化不一致的行分行符號字元和分行符號，若要選擇哪一種。