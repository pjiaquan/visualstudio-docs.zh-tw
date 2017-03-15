---
title: "專案設計工具，參考頁 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "專案設計工具中的參考頁"
  - "專案設計工具，參考頁"
  - "未使用的參考對話方塊"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 專案設計工具，參考頁 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

請使用 \[**專案設計工具**\] 的 \[**參考**\] 頁，管理專案中的參考、Web 參考以及匯入的命名空間。  專案可以包含對 COM 元件、XML Web Service、.NET Framework 類別庫 \(Class Library\) 或組件 \(Assembly\) 或是其他類別庫的參考。  如需使用參考的詳細資訊，請參閱[管理專案中的參考](../../ide/managing-references-in-a-project.md)。  
  
 若要存取 \[**參考**\] 頁，請選取專案節點 \(不是 \[**方案**\] 節點\) 在 \[**方案總管**\]。  然後選取 \[**專案**\]，請在功能表列上的 \[**屬性**\] 。  當專案設計工具出現時，按一下 \[**參考**\] 索引標籤。  
  
## UIElement 清單  
 下列選項可以讓您選取或移除專案中的參考和匯入的命名空間。  
  
 **未使用的參考**  
 按一下這個按鈕可存取 \[**未使用的參考**\] 對話方塊。  
  
 \[**未使用的參考**\] 對話方塊可以讓您移除包含在專案中但是實際上程式碼不會使用的參考。  它包含列出 \[**參考名稱**\]， \[**路徑**\]，，以及未使用的命名空間的其他資訊在專案中參考的方格。  在方格中，選取您要從專案中移除的命名空間參考，並按一下 \[**移除**\]。  
  
 **參考路徑**  
 按一下這個按鈕可存取 \[**參考路徑**\] 對話方塊。  
  
> [!NOTE]
>  當專案系統找到組件參考時，系統會以解析參考在下列位置中，依照下列順序:  
>   
>  1.  專案資料夾。  當 \[**顯示所有檔案**\] 不在作用中時，專案資料夾的檔案會出現在 \[**方案總管**\] 中。  
> 2.  在 \[**參考路徑**\] 對話方塊中指定的資料夾。  
> 3.  顯示 \[**加入參考**\] 對話方塊之檔案的資料夾。  
> 4.  專案的 obj 資料夾。  \(當您在專案中加入 COM 參考，一或多個組件可能會加入至專案的 obj 資料夾\)。  
  
 **參考**  
 這個清單會顯示專案中所有已使用和未使用的參考。  
  
 **加入**  
 按一下這個按鈕可將參考或 Web 參考加入至 \[**參考**\] 清單。  
  
 選擇 \[**參考**\] 可使用 \[加入參考\] 對話方塊將參考加入至您的專案。  
  
 選擇 \[**Web 參考**\] 則可使用 \[加入 Web 參考\] 對話方塊將 Web 參考加入至專案中。  
  
 **Remove**  
 在 \[**參考**\] 清單中選取一或多個參考，然後按一下這個按鈕即可刪除參考。  
  
 **更新 Web 參考**  
 在 \[**參考**\] 清單中選取一個 Web 參考，然後按一下這個按鈕即可更新參考。  
  
 **匯入的命名空間**  
 您可以在這個方塊中輸入自己的命名空間，然後按一下 \[**加入使用者匯入**\]，即可將它加入至命名空間清單。  
  
 您可以為使用者匯入的命名空間建立別名 \(Alias\)。  若要執行這項操作，請以 *alias*\=*namespace* 的格式輸入別名和命名空間。  如果您使用的命名空間非常長，例如，`Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` 這種做法就會很有用。  
  
 **加入使用者匯入**  
 按一下這個按鈕，即可將 \[**匯入的命名空間**\] 方塊中指定的命名空間，加入到匯入的命名空間清單中。  這個按鈕只會在清單中沒有指定的命名空間時提供使用。  
  
 **命名空間清單**  
 這個清單會顯示所有可用的命名空間。  專案中所包含的命名空間，其核取方塊都會呈現已選取。  
  
 **更新使用者匯入**  
 在命名空間清單中選取使用者指定的命名空間，並在 \[**匯入的命名空間**\] 方塊中輸入您要用來取代它的名稱，然後按一下這個按鈕，即可變更成新的命名空間。  這個按鈕只在選取的命名空間是使用 \[**加入使用者匯入**\] 按鈕加入至清單的命名空間時提供使用。  您可以加入下列項目：  
  
-   類別或命名空間，例如 <xref:System.Math?displayProperty=fullName>。  
  
-   使用別名的匯入，例如 `VB=Microsoft.VisualBasic`。  
  
-   XML 命名空間，例如 `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`。  
  
## 請參閱  
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [如何：加入或移除匯入的命名空間 \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/zh-tw/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)