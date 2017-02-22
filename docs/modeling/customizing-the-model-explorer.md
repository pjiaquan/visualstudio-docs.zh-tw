---
title: "自訂模型總管 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "Domain-Specific Language Tools, 網域指定的語言總管"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 自訂模型總管
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以變更外觀和行為的瀏覽器您定義域專屬語言設計工具，如下所示：  
  
-   變更視窗標題。  
  
-   變更定位點圖示。  
  
-   變更節點的圖示。  
  
-   隱藏的節點。  
  
## 變更視窗標題  
 若要變更 \[產生的檔案總管\] 視窗標題，請選取 **總管行為** 在  **DSL 總管**，然後在 **屬性** 視窗中，設定 **標題**屬性，以您想要的標題。  
  
## 變更定位點圖示  
 若要變更定位點圖示的 \[檔案總管\] 中，使用.bmp 檔中的 16 x 16 像素圖示。  將圖示檔放在 \[\\DslPackage\\Resources\\\] 資料夾中，並變更檔名為 ModelExplorerToolWindowBitmaps.bmp。  例如，您可以將[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico 圖示.bmp 格式的檔案和它重新命名為 DSLLanguageName\\DslPackage\\Resources\\ModelExplorerToolWindowBitmaps.bmp。  產生設計工具會顯示此圖示在您的檔案總管\] 索引標籤與一起停駐時**方案總管\] 中**。  
  
## 在 \[檔案總管節點上設定自訂圖示  
 您可以使用檔案總管\] 節點的設定，在您的檔案總管\] 中自訂節點。  下列程序會示範如何將圖示加入至節點。  
  
#### 若要將圖示新增到 \[檔案總管\] 節點  
  
1.  建立[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]藉由使用 \[工作流程\] 方案範本的解決方案。  
  
2.  存放包含 16 x 16 像素圖示中的.bmp 檔案 **Dsl\\Resources** 方案中的資料夾。  
  
3.  在 **DSL 總管**，以滑鼠右鍵按一下 **總管行為** ，然後按一下 \[ **加入新的檔案總管節點設定**。  
  
     **ExplorerNodeSettings** 節點就會出現在**自訂節點設定**節點。  
  
4.  選取  **ExplorerNodeSettings**，然後在 **屬性** 視窗中，設定 **類別** 到 **動作項目**。  
  
5.  設定**圖示來顯示**圖示檔的路徑。  
  
6.  轉換所有的範本，然後建置並執行方案。  
  
7.  在產生的設計工具中，開啟範例圖表。  
  
     \[檔案總管\] 中應該會顯示三個**動作項目**有您圖示的節點。  
  
> [!NOTE]
>  如果您已設定節點的圖示會顯示在 \[產生的檔案總管\] 中的任何項目，所有的檔案總管\] 節點會顯示圖示。  如果尚未設定任何圖示，節點會顯示預設圖示。  
  
## 變更顯示在 \[檔案總管\] 節點上的名稱  
 您可以變更您的檔案總管\] 中的模型項目名稱的顯示方式。  下列程序會示範如何顯示所參考的註解節點中的註解工作的名稱。  
  
#### 若要顯示屬性  
  
1.  開啟您在先前程序中所建立的方案。  
  
2.  請確定註解參考只有單一網域類別，藉由設定屬性名稱與角色的重數**主題**到..1。  屬性名稱應該會變得**主旨**，而此關聯性名稱應該會變得  **CommentReferencesSubject**。  
  
3.  在 **DSL 總管**，以滑鼠右鍵按一下 **總管行為** ，然後按一下 \[ **加入新的檔案總管節點設定**。  
  
     **ExplorerNodeSettings** 節點就會出現在**自訂節點設定**節點。  
  
4.  選取  **ExplorerNodeSettings**，然後在 **屬性** 視窗中，設定 **類別** 到 **註解**。  
  
5.  以滑鼠右鍵按一下**註解** 節點，然後再按一下 **加入新的屬性路徑**。  
  
     新的節點就會出現名為**屬性顯示**。  
  
6.  選取**屬性顯示**，然後在 **屬性** 視窗中，按一下 \[值\] 欄位的  **To 屬性路徑**。  選取 \[ **註解**，然後  **CommentReferencesSubject**，然後  **FlowElement**。  產生的路徑應該看起來像 **CommentReferencesSubject.Subject\/\!主旨**。  
  
7.  在 \[值\] 欄位的**屬性**，請選取 **名稱**。  
  
8.  轉換所有的範本，然後建置並執行方案。  
  
9. 在產生的設計工具中，開啟範例圖表。  
  
10. 繪製**註解連接器** 的註解項目之間以及 **任務 1** 在圖表上的項目。  
  
     總管節點應該會顯示為註解**任務 1**。  
  
## 隱藏節點  
 您也可以加入它的路徑，以在您的檔案總管\] 中隱藏節點**隱藏節點** 節點的  **DSL 總管**。  下列程序會示範如何隱藏註解節點。  
  
#### 若要隱藏的檔案總管\] 節點  
  
1.  開啟您在先前程序中所建立的方案。  
  
2.  在 **DSL 總管**，以滑鼠右鍵按一下 **總管行為** ，然後按一下 \[ **加入新的網域路徑**。  
  
     A **網域路徑** 節點就會出現在 **隱藏節點**。  
  
3.  選取 **網域路徑**，然後在 **屬性** 視窗中，按一下 \[值\] 欄位的 **路徑定義**。  選取 \[  **FlowGraph**，然後  **FlowGraphHasComments**。  產生的路徑應該看起來像 **FlowGraphHasComments.Comments**  
  
4.  轉換所有的範本，然後建置並執行方案。  
  
5.  在產生的設計工具中，開啟範例圖表。  
  
     瀏覽器應該只會顯示**演員** 節點，而且不應該顯示 **註解**節點。  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)