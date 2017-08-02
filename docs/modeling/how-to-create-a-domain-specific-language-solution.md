---
title: "如何︰ 建立定義域專屬的語言方案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：建立網域指定的語言方案
定義域專屬語言 (DSL) 所使用的特定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案。  
  
## <a name="prerequisites"></a>必要條件  
 您可以啟動此程序之前，您必須先安裝這些元件︰  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>建立定義域專屬語言方案  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>若要建立定義域專屬語言方案  
  
1.  啟動 DSL 精靈。  
  
    1.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
    2.  [ **新增專案** ] 對話方塊隨即出現。  
  
    3.  在**專案類型**，依序展開**其他專案類型**節點，然後按一下 **擴充性**。  
  
    4.  按一下 **定義域專屬語言設計工具**。  
  
    5.  在**名稱**方塊中，輸入方案的名稱。 按一下 [確定]。  
  
         **定義域專屬語言設計工具精靈**隨即出現。  
  
        > [!NOTE]
        >  最好是您所輸入的名稱應該是有效的 Visual C# 識別項，因為它可能會用來產生程式碼。  
  
     ![建立 DSL 對話方塊](~/modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  選擇 DSL 範本。  
  
     在**選取定義域專屬語言選項**頁面上，選取其中一個解決方案範本，例如**最小語言**。 選擇您想要建立 DSL 類似的範本。  
  
     如需詳細的解決方案範本的詳細資訊，請參閱[選擇定義域專屬語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
3.  在輸入副檔名**副檔名**頁面。 應該是唯一的電腦，以及您要在任何電腦上安裝 DSL。 您應該會看到訊息**沒有應用程式或 Visual Studio 編輯器會使用此延伸模組**。  
  
    -   如果您使用檔案的副檔名不完整安裝的上一個實驗 Dsl 中，您可以清除它們外使用**重設實驗執行個體**工具，請參閱[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]SDK 功能表。  
  
    -   如果另一個[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組使用此副檔名的完整安裝在電腦上，請考慮解除安裝它。 在**工具**] 功能表上，按一下 [**擴充管理員**。  
  
4.  檢查，並視調整，請在精靈的其餘頁面中的欄位。 當您設定完成後，請按一下 **完成**。 如需設定的詳細資訊，請參閱[DSL 設計工具的精靈頁面](#settings)。  
  
     精靈會建立一個具有兩個專案，名為方案**Dsl**和**DslPackage**。  
  
    > [!NOTE]
    >  如果您看到訊息時產生警示不受信任來源執行的文字範本，請按一下 **確定**。 您可以設定此訊息不會再出現。  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>DSL 設計工具的精靈頁面  
 您可以將數個欄位，預設值不變。 不過，請確定您設定 [副檔名] 欄位。  
  
### <a name="solution-settings-page"></a>方案 [設定] 頁面  
 **您要根據您的網域特定語言的範本？**  
 選擇您想要建立 DSL 類似的範本。 不同的範本會提供便利的起點。 當您選取的解決方案範本時，精靈會顯示描述。 如需詳細的解決方案範本的詳細資訊，請參閱[選擇定義域專屬語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 **要命名您的網域特定語言？**  
 預設為方案名稱。 這個值會產生程式碼。 它必須是有效的 C# 類別名稱。  
  
### <a name="file-extension-page"></a>副檔名頁面  
 **何種擴充功能應該模型檔案會使用？**  
 輸入新的副檔名。  
  
 確認，這種檔案類型不已登錄在此電腦上，使用，如下所示︰  
  
 請查看**來處理此延伸模組的其他工具和應用程式註冊**。 如果您看到訊息**沒有應用程式或 Visual Studio 編輯器會使用此延伸模組**，則您可以使用這種檔案類型。  
  
 如果您看到一份工具或封裝，您應該執行下列其中一項︰  
  
-   輸入不同的副檔名。  
  
     \-或-  
  
-   重設[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實驗執行個體。 這將會取消登錄所有您先前建立的 Dsl。 在**啟動**] 功能表上，按一下 [**所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設 Microsoft Visual Studio 2010 實驗執行個體**。 您可以重建您想要再次使用的任何其他 Dsl。  
  
     \-或-  
  
-   如果[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組使用此副檔名的完整安裝在電腦上，解除安裝。 在**工具**] 功能表上，按一下 [**擴充管理員**。  
  
### <a name="product-settings-page"></a>產品 [設定] 頁面  
 **新的定義域專屬語言所屬的產品名稱是什麼？**  
 預設為 DSL 的名稱。  
  
 在 Windows 檔案總管 （或檔案總管） 來描述此副檔名的檔案會使用此值。  
  
 **產品所屬的公司名稱是什麼？**  
 您的公司名稱。  
  
 這個值會併入您的 DSL 封裝的 AssemblyInfo 屬性。  
  
 **什麼是此方案中專案的根命名空間？**  
 預設值為從您的公司所組成的名稱與產品名稱。  
  
### <a name="signing-page"></a>簽署頁  
 **建立強式名稱金鑰檔**  
 若要建立新的金鑰來簽署您的 DSL 組件是預設選項。  
  
 **使用現有的強式名稱金鑰**  
 如果您想要將您的 DSL 整合與另一個組件，請使用此選項。  
  
 如需有關強式命名的詳細資訊，請參閱[建立和使用強式名稱組件](http://go.microsoft.com/fwlink/?LinkId=186073)。  
  
## <a name="see-also"></a>另請參閱  
 [如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [定義域專屬語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

