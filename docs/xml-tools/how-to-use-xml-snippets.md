---
title: "HOW TO：使用 XML 片段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：使用 XML 片段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 XML 編輯器捷徑功能表上的下列兩個命令叫用 XML 片段。\[插入片段\] 命令可將 XML 片段插入游標位置。\[以此環繞\] 命令會以 XML 片段環繞選定文字。每個 XML 片段都具有指定的片段型別。片段型別決定是否可對片段使用 \[插入片段\] 命令或 \[以此環繞\] 命令或二者。  
  
 將 XML 片段加入編輯器後，片段中所有可編輯的欄位均會以黃色反白顯示，且游標位於第一個可編輯欄位上。  
  
## 插入片段  
 下列程序說明如何存取 \[插入片段\] 命令。  
  
> [!NOTE]
>  也可以透過鍵盤快速鍵 \(CTRL\+K 及 CTRL\+X\) 來使用 \[插入片段\] 命令。  
  
#### 透過捷徑功能表插入片段  
  
1.  將游標置於您要插入 XML 片段的位置。  
  
2.  按一下滑鼠右鍵，並選取 \[插入片段\]。  
  
     會顯示可用 XML 片段的清單。  
  
3.  使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。  
  
#### 使用 IntelliSense 功能表插入片段  
  
1.  將游標置於您要插入 XML 片段的位置。  
  
2.  從 \[編輯\] 功能表，指向 \[IntelliSense\]，並選取 \[插入片段\]。  
  
     會顯示可用 XML 片段的清單。  
  
3.  使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。  
  
#### 透過 IntelliSense 自動完成清單插入片段  
  
1.  將游標置於您要插入 XML 片段的位置。  
  
2.  開始鍵入您想要加入檔案的 XML 片段。如果自動完成已開啟，則會顯示 IntelliSense 自動完成清單。如果清單未出現，請按 CTRL\+SPACEBAR 啟動它。  
  
3.  從自動完成清單中選取 XML 片段。  
  
4.  按 TAB 鍵，以叫用 XML 片段。  
  
> [!NOTE]
>  有時可能無法叫用 XML 片段。例如，如果您嘗試在 `xs:element` 節點內插入 `xs:complexType` 項目，則編輯器不會產生 XML 片段。在 `xs:element` 節點內使用 `xs:complexType` 項目時，因為沒有必要的屬性或項目子系，所以編輯器並無任何要插入的資料。  
  
#### 使用捷徑名稱插入片段  
  
1.  將游標置於您要插入 XML 片段的位置。  
  
2.  在編輯器窗格中鍵入 `<`。  
  
3.  按 ESC 鍵關閉 IntelliSense 自動完成字組清單。  
  
4.  鍵入片段的捷徑名稱，並按 TAB 鍵以叫用 XML 片段。  
  
## 以此環繞  
 下列程序說明如何存取 \[以此環繞\] 命令。  
  
> [!NOTE]
>  也可以透過鍵盤快速鍵 \(CTRL\+K 及 CTRL\+S\) 來使用 \[以此環繞\] 命令。  
  
#### 透過內容功能表使用以此環繞  
  
1.  在 \[XML 編輯器\] 中選取要環繞的文字。  
  
2.  按一下滑鼠右鍵，並選取 \[以此環繞\]。  
  
     會顯示可用以此環繞 XML 片段的清單。  
  
3.  使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。  
  
#### 透過 Intellisense 功能表使用以此環繞  
  
1.  在 \[XML 編輯器\] 中選取要環繞的文字。  
  
2.  從 \[編輯\] 功能表，指向 \[IntelliSense\]，並選取 \[以此環繞\]。  
  
     會顯示可用以此環繞 XML 片段的清單。  
  
3.  使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。  
  
## 使用 XML 片段  
 一旦選擇了 XML 片段，程式碼片段的文字便會自動插入游標位置。會反白顯示片段中任何可編輯的欄位，並自動選取第一個可編輯的欄位。目前選取的欄位為 boxed。  
  
 選取欄位後，您可以為該欄位鍵入新值。按 TAB 鍵轉換片段的可編輯欄位；按 SHIFT\+TAB 以相反順序轉換這些欄位。按一下欄位便會將游標置於該欄位中，而按兩下欄位便會選取它。反白顯示欄位後，可能會顯示提供欄位說明的工具提示。  
  
 只有給定欄位的第一個執行個體才是可編輯的。反白顯示該欄位時，會為欄位之其他執行個體加上外框。當您變更可編輯欄位的值時，該片段中任何位置所使用的這個欄位均會變更。  
  
 按 ENTER 鍵或 ESC 鍵以取消欄位編輯，並將編輯器返回到正常狀態。  
  
 藉由在 \[選項\] 對話方塊的 \[字型和色彩\] 窗格中修改程式碼片段欄位設定，可以變更可編輯程式碼片段欄位的預設色彩。如需詳細資訊，請參閱 [如何：在編輯器中變更字型和顏色](../Topic/How%20to:%20Change%20Fonts%20and%20Colors%20in%20the%20Editor.md)。  
  
## 請參閱  
 [XML 片段](../xml-tools/xml-snippets.md)   
 [HOW TO：從 XML 結構描述產生 XML 片段](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)   
 [HOW TO：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)