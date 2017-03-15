---
title: "設定圖表上的背景影像 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# 設定圖表上的背景影像
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK 中，您可以使用自訂程式碼，為產生的設計工具設定背景影像。  
  
## 設定背景影像  
  
#### 為產生的設計工具設定背景影像  
  
1.  將您要用來做為圖表背景的影像檔複製到目前專案的 Dsl\\Resources 目錄中。  
  
2.  在 \[方案總管\] 中，以滑鼠右鍵按一下 Dsl\\Resources 資料夾，指向 \[加入\]，然後按一下 \[現有項目\]。  
  
3.  在 \[加入現有項目\] 對話方塊中，瀏覽至 Dsl\\Resources 資料夾。  
  
4.  在 \[檔案類型\] 清單中，按一下 \[影像檔\]。  
  
5.  按一下要複製到目錄的影像檔，然後按一下 \[加入\]。  
  
6.  以滑鼠右鍵按一下 Dsl，然後按一下 \[屬性\] 開啟 Dsl 專案的屬性。  
  
7.  在 \[資源\] 索引標籤上，按一下 \[此專案不包含預設資源檔。請按一下這裡以建立預設資源檔\]。  
  
8.  將圖片從 \[方案總管\] 拖曳到資源視窗，即可將影像檔加入資源檔。  
  
9. 開啟 \[檔案\] 功能表，然後按一下選項以儲存專案屬性。  
  
10. 確認檔案 Dsl\\Properties\\Resources.resx 存在且其下有檔案 Resources.Designer.cs。  
  
11. 如果遺漏了 Resources.Designer.cs，請按一下 \[方案總管\] 中的檔案 Resources.resx。  
  
12. 在 \[屬性\] 視窗中，將 `Custom Tool` 屬性設為 `ResXFileCodeGenerator`。  
  
13. 在 \[方案總管\] 中，以滑鼠右鍵按一下 Dsl 專案，指向 \[加入\]，然後按一下 \[新增資料夾\]。  
  
14. 將資料夾命名為 Custom。  
  
15. 以滑鼠右鍵按一下 Custom 資料夾，指向 \[加入\]，然後按一下 \[新增項目\]。  
  
16. 在 \[加入新項目\] 對話方塊中，按一下 \[範本\] 清單中的 \[程式碼檔案\]。  
  
17. 在 \[名稱\] 方塊中，輸入 `BackgroundImage.cs`，然後按一下 \[加入\]。  
  
18. 將下列程式碼複製到 BackgroundImage.cs 檔，調整的命名空間、圖表類別名稱和影像檔資源名稱。  
  
     將 "MyDiagramClass" 取代為 Dsl\\GeneratedCode\\Diagrams.cs 中所定義的圖表部分類別名稱。  您也可以從檔案 Dsl\\GeneratedCode\\Diagrams.cs 中擷取正確的命名空間。  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     如需自訂內附程式碼之模型的詳細資訊，請參閱 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
## 請參閱  
 [定義圖案和連接器](../modeling/defining-shapes-and-connectors.md)   
 [自訂文字和影像欄位](../modeling/customizing-text-and-image-fields.md)   
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [撰寫程式碼來自訂定義域專屬語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)