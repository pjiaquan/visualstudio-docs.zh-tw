---
title: "Visual Basic 特定的 IntelliSense | Microsoft Docs"
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
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual Basic 特定的 IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Basic 原始程式碼編輯器提供下列的 IntelliSense 功能：  
  
-   語法提示  
  
     語法提示會顯示您目前所輸入的陳述式的語法，  這一點對於 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) 之類的陳述式相當實用。  
  
## 自動完成  
  
-   完成各種的關鍵字  
  
     例如，若是輸入 `goto` 和一個空格，IntelliSense 會在下拉式功能表中顯示已定義標籤的清單。  其他支援的關鍵字包括 `Exit`、`Implements`、`Option` 和 `Declare`。  
  
-   完成 `Enum` 和 `Boolean`  
  
     當陳述式會參考到列舉型別的成員時，IntelliSense 會顯示 `Enum` 成員的清單。  陳述式會參考到 `Boolean` 時，IntelliSense 會顯示 True\-false 下拉式功能表。  
  
 在 \[**Visual Basic**\] 資料夾的 \[**一般**\] 屬性頁中取消選取 \[**自動列出成員**\]，可以預設關閉完成。  
  
 您可以叫用列出成員、自動完成文字或按 ALT\+向右鍵，以手動叫用完成。  如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。  
  
## IntelliSense in Zone  
 IntelliSense in Zone 可以協助需要透過 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署應用程式的 Visual Basic 開發人員，並可限制為部分信任設定。  此功能：  
  
-   可讓您選擇應用程式執行時所用的權限。  
  
-   將選擇區域中的 API 顯示為在 \[列出成員\] 中可用，並將需要其他權限的 API 顯示為不可用。  
  
 如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
## 請參閱  
 [使用 IntelliSense](../ide/using-intellisense.md)