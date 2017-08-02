---
title: "XML 結構描述總管 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# XML 結構描述總管
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 結構描述總管整合於 Microsoft Visual Studio 和 XML 編輯器，可讓您使用 XML 結構定義語言 \(XSD\) 結構描述。當您開啟 XML 結構描述檔時，\[**結構描述集**\] 節點會出現在 XML 結構描述總管中。所有包含的、匯入的或重新定義的目標檔結構描述，以及透過 `include` 或 `import` 陳述式參考的所有檔案，也會出現在 XML 結構描述總管中。  
  
 XML 結構描述總管可讓您進行下列作業：  
  
-   取得結構描述設定的快速概觀。  
  
-   瀏覽和巡覽樹狀結構。  
  
-   執行關鍵字和結構描述特有的搜尋。如需詳細資訊，請參閱[搜尋結構描述集](../xml-tools/searching-the-schema-set.md)。  
  
-   將搜尋結果加入至圖表檢視或內容模型檢視  
  
-   依據文件順序、類型或名稱排序樹狀結構。如需詳細資訊，請參閱[排序、篩選與群組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)。  
  
-   開啟 XML 編輯器並跳到 XSD 檔中的程式碼位置。如需詳細資訊，請參閱[與 XML 編輯器整合](../xml-tools/integration-with-xml-editor.md)。  
  
-   針對全域項目產生範例 XML。  
  
 XML 結構描述總管會透過樹狀檢視提供結構描述設定的階層式檢視。XML 結構描述總管也會提供搜尋、篩選、導覽和排序功能。若要存取 XML 結構描述總管，請執行下列其中一項：  
  
-   如果您在[開始檢視](../xml-tools/start-view.md)中，請按一下 \[**XML 結構描述總管**\] 連結。  
  
-   如果您在[圖表檢視](../xml-tools/graph-view.md)或[內容模型檢視](../xml-tools/content-model-view.md)中，且工作空間中具有節點，請使用內容功能表選取 XML 結構描述總管。  
  
-   您也可以選取 \[**檢視**\] 功能表中的 \[**XML 結構描述總管**\]。  
  
-   您可以透過 .vb 檔案存取 XML 結構描述總管，此檔案必須具有與 .xsd 檔案相關的 Visual Basic XML 常值。若要在 XML 結構描述總管中查看結構描述集，請以滑鼠右鍵按一下 XML 常值或 XML 命名空間匯入中的 XML 節點，然後選取 \[**在結構描述總管中顯示**\] 命令。如需詳細資訊，請參閱[整合 XML 常值與 XML 結構描述總管](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)。  
  
## 樹狀檢視  
 XML 結構描述總管會在樹狀結構中顯示預先編譯的結構描述設定資訊。此樹狀結構會依照下列方式組織：  
  
-   最上層是結構描述設定節點。  
  
-   第二層包含命名空間。  
  
-   第三層包含檔案。  
  
-   第四層包含全域節點。這可能包括項目、群組、複雜型別、簡單型別、屬性、屬性群組，以及 `include`、`import` 和 `redefine` 陳述式。  
  
 以下是樹狀結構的範例：  
  
 ![XML 結構描述總管](~/xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## 選取和啟動  
 若要反白顯示並選取節點，請在結構描述總管中按一下。  
  
 若要啟動節點，請先選取節點再於節點上按兩下，或按 **Enter** 鍵。  
  
-   啟動節點會開啟定義該節點的檔案 \(如果該檔案尚未開啟\)，並且在該檔案中選取此節點。  
  
-   啟動檔案節點會開啟所選的檔案 \(若該檔案尚未開啟\)，並且反白顯示 `<schema>` 節點。  
  
-   啟動 SchemaSet 或命名空間節點不會有任何反應。  
  
## 拖放節點  
 您可以將全域節點、檔案節點以及命名空間節點拖放至 XSD 設計工具檢視中。如果目前的檢視是[開始檢視](../xml-tools/start-view.md)，將節點拖曳到該檢視上就會開啟[圖表檢視](../xml-tools/graph-view.md)。如果目前的檢視是[內容模型檢視](../xml-tools/content-model-view.md)或圖表檢視，當您將節點拖曳到檢視中時，檢視不會發生任何變化。  
  
 將檔案置於檢視上會將檔案中的所有全域節點加入至 [XSD 設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)。將命名空間置於檢視上則會將命名空間中的所有全域節點加入至該工作空間。工作空間在所有檢視之間共用。  
  
 您無法拖放本機節點或匯入。  
  
## 本章節內容  
  
-   [搜尋結構描述集](../xml-tools/searching-the-schema-set.md)  
  
-   [排序、篩檢與群組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [內容功能表](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [整合 XML 常值與 XML 結構描述總管](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## 請參閱  
 [HOW TO：將節點從 XML 結構描述總管加入至工作空間](../Topic/How%20to:%20Add%20Nodes%20to%20the%20Workspace%20from%20the%20XML%20Schema%20Explorer.md)