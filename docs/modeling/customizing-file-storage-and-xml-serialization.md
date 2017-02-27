---
title: "自訂檔案儲存體和 XML 序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.xmlbehavior"
helpviewer_keywords: 
  - "定義域專屬語言序列化"
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# 自訂檔案儲存體和 XML 序列化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當使用者儲存工作執行個體，或 *模型*, ，定義域專屬語言 (DSL) 中的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，建立或更新的 XML 檔案。 重新建立存放區的模型，可以重新載入檔案。  
  
 您可以藉由調整下的設定自訂的序列化配置 **Xml 序列化行為** DSL 總管] 中。 沒有下的節點 **Xml 序列化行為** 的每個網域類別、 屬性和關聯性。 關聯性位於其來源類別。 也沒有對應到圖形、 連接器和圖表類別的節點。  
  
 您也可以撰寫更進階的自訂程式碼。  
  
> [!NOTE]
>  如果您想要儲存模型中特定的格式，但您不需要重新載入該表單，請考慮使用文字範本來產生輸出從模型中，而不是一種自訂的序列化配置。 如需詳細資訊，請參閱 [定義域專屬語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
## <a name="model-and-diagram-files"></a>模型和圖表檔  
 每個模型通常會儲存在兩個檔案︰  
  
-   模型檔案名稱程式例如 **Model1.mydsl**。 它會儲存模型項目和關聯性和其屬性。 檔案副檔名，例如 **.mydsl** 取決於 **FileExtension** 屬性 **編輯器** DSL 定義中的節點。  
  
-   圖表檔案這類具有名稱 **Model1.mydsl.diagram**。 它會儲存圖形、 連接器和它們的位置、 色彩、 線條寬度和圖表的外觀的其他詳細資料。 如果使用者刪除 **.diagram** 檔案中，模型中的重要資訊不會遺失。 只有圖表的版面配置會遺失。 開啟模型檔案時，一組預設圖形和連接器將會建立。  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>若要變更之 DSL 的副檔名  
  
1.  開啟 DSL 定義中。 在 [DSL 總管] 中，按一下 [編輯器] 節點。  
  
2.  在 [屬性] 視窗中，編輯 **FileExtension** 屬性。 不包含初始 「。 」 的檔案名稱的副檔名。  
  
3.  在方案總管] 中，兩個項目範本中的檔案名稱變更 **DslPackage\ProjectItemTemplates**。 這些檔案必須遵循以下格式的名稱︰  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>預設序列化配置  
 若要建立本主題的範例，請使用下列的 DSL 定義。  
  
 ![DSL 定義圖 & #45。家譜模型](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 此 DSL 用來建立具有下列外觀在螢幕的模型。  
  
 ![家譜圖表、工具箱和總管](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 此模型已儲存，然後再重新開啟 XML 文字編輯器中︰  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 請注意下列有關序列化的模型的重點︰  
  
-   每個 XML 節點具有網域類別名稱相同的名稱，不同之處在於的第一個字母是小寫。 例如， `familyTreeModel` 和 `person`。  
  
-   網域屬性，例如名稱和生日年份會序列化為 XML 節點中的屬性。 同樣地，屬性名稱的起始字元會轉換成小寫。  
  
-   每個關聯性會序列化為 XML 節點巢狀關聯性的來源末端。 節點有相同的名稱作為來源角色屬性中，但大小寫的起始字元。  
  
     例如，在 DSL 定義中，名為角色 **人** 源自 **FamilyTree** 類別。  在 XML 中，這由名為的節點代表 `people` 巢狀於 `familyTreeModel` 節點。  
  
-   每個內嵌關聯性的目標末端會序列化為巢狀結構下的關聯性的節點。 例如， `people` 節點包含數個 `person` 節點。  
  
-   每個參考關聯性目標端已序列化為 *moniker*, ，這會編碼目標項目的參考。  
  
     例如，在 `person` 節點，可以有 `children` 關聯性。 這個節點包含 moniker，例如︰  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>了解 Moniker  
 Moniker 的使用，用於代表的模型和圖表檔案的不同部分之間的交互參考。 它們也可以用在 `.diagram` 檔案，以參考的模型檔案中的節點。 有兩種形式的 moniker:  
  
-   *識別碼 moniker* 加上引號的目標項目 GUID。 例如：  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *限定金鑰 moniker* 名為的 moniker 索引鍵的指定的網域屬性的值所識別的目標項目。 內嵌關聯性的樹狀目錄中其父項目的 moniker 的前置詞的目標項目 moniker。  
  
     下列範例取自 DSL 中的有是名為具有內嵌關聯性的網域類別具名的歌曲的專輯的網域類別︰  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     如果目標類別有一個網域屬性，就會使用限定的索引鍵 moniker 選項 **是 Moniker 索引鍵** 設為 `true` 中 **Xml 序列化行為**。 在範例中，「 專輯 」 和 「 歌曲 」 的網域類別中名為"Title"的網域屬性會設定這個選項。  
  
 完整的索引鍵 moniker 是比識別碼 moniker 閱讀。 如果您想要的人讀取模型檔案的 XML，請考慮使用限定的索引鍵 moniker。 但是，它可能是使用者設定多個具有相同的 moniker 索引鍵的項目。 重複的索引鍵可能導致檔案未正確載入。 因此，如果您定義網域類別，使用完整的索引鍵 moniker 參考時，您應該考慮方式防止使用者儲存檔案具有重複的 moniker。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>若要設定網域類別識別碼 moniker 所要參考  
  
1.  請確定 **是 Moniker 索引鍵** 是 `false` 類別和其基底類別中的每個網域屬性。  
  
    1.  在 [DSL 總管] 中，展開 **Xml 序列化 Behavior\Class 資料\\***\< 網域類別>***\Element 資料**。  
  
    2.  確認 **是 Moniker 索引鍵** 是 `false` 的每個網域屬性。  
  
    3.  如果網域類別的基底類別，重複該類別中的程序。  
  
2.  設定 **序列化 Id** = `true` 網域類別。  
  
     這個屬性可以在下找到 **Xml 序列化行為**。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>若要設定網域類別所限定的索引鍵 moniker 參考  
  
-   設定 **是 Moniker 索引鍵** 針對現有的網域類別的網域屬性。 屬性的型別必須是 `string`。  
  
    1.  在 [DSL 總管] 中，展開 **Xml 序列化 Behavior\Class 資料\\***\< 網域類別>***\Element 資料**, ，然後選取 [網域屬性。  
  
    2.  在 [屬性] 視窗中，設定 **是 Moniker 索引鍵** 到 `true`。  
  
-   \- 或-  
  
     建立新的網域類別使用 **具名網域類別** 工具。  
  
     此工具會建立新的類別具有名為 Name 的網域屬性。  **Is Element Name** 和 **是 Moniker 索引鍵** 此網域屬性的屬性會初始化為 `true`。  
  
-   \- 或-  
  
     為具有 moniker 索引鍵屬性的另一個類別，從網域類別建立繼承關聯性。  
  
### <a name="avoiding-duplicate-monikers"></a>避免重複的 Moniker  
 如果您使用完整的索引鍵 moniker，就可以在使用者的模型中的兩個項目，可以擁有相同的值中的索引鍵屬性。 例如，如果您的 DSL 有類別都有屬性名稱的人員，使用者可以設定相同的兩個項目名稱。 雖然模型可能會儲存至檔案，它會重新載入正確。  
  
 有數種方法，協助避免這種情況︰  
  
-   設定 **Is Element Name** = `true` 關鍵的網域屬性。 選取網域屬性在 DSL 定義圖上的，然後在 [屬性] 視窗中設定的值。  
  
     當使用者建立之類別的新執行個體時，這個值會導致網域屬性，以自動指派不同的值。 預設行為會將數字加入至類別名稱的結尾。 這不會防止使用者從將名稱變更為重複項目，但時使用者不會設定的值，然後再儲存模型的案例中很有用。  
  
-   啟用 DSL 的驗證。 在 [DSL 總管] 中，選取 [編輯器 \ 驗證，並設定 **...使用** 屬性 `true`。  
  
     沒有自動產生的驗證方法，會檢查模稜兩可。 該方法是位於 `Load` 驗證類別。 如此可確保它可能無法重新開啟檔案會警告使用者。  
  
     如需詳細資訊，請參閱 [驗證定義域專屬語言](../modeling/validation-in-a-domain-specific-language.md)。  
  
### <a name="moniker-paths-and-qualifiers"></a>Moniker 路徑和辨識符號  
 完整的索引鍵 moniker 的 moniker 索引鍵，結束，且加上內嵌的樹狀目錄中其父系的 moniker。 例如，如果 moniker 的相簿的︰  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 然後該專輯中的歌曲的其中一個可能是︰  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 不過，如果專輯改為參考的識別碼，則 moniker 會，如下所示︰  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 請注意，GUID 是唯一的因為它永遠不會加上其父系的 moniker。  
  
 如果您知道特定網域屬性永遠會在模型內的唯一值，您可以設定 **是 Moniker 限定詞** 到 `true` 該屬性。 這會導致要做為辨識符號，而不使用父代的 moniker。 例如，如果您同時設定 **是 Moniker 限定詞** 和 **是 Moniker 索引鍵** 專輯類別的 Title 網域屬性，模型的名稱或識別碼不是在 moniker 專輯和內嵌的子︰  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>自訂 XML 的結構  
 若要進行下列自訂，展開 **Xml 序列化行為** DSL 總管] 中的節點。 在網域類別，展開項目資料節點，若要查看的內容和關聯性在這個類別是來源清單。 選取關聯性，並調整其 [屬性] 視窗中的選項。  
  
-   設定 **省略項目** 為 true，表示要省略來源角色節點，而保留的目標項目清單。 如果來源和目標類別之間有一個以上的關聯性，您不應該設定這個選項。  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   設定 **使用完整形式** 代表關聯性執行個體的節點中內嵌之目標節點。 當您將網域屬性加入至網域關聯性時，會自動設定這個選項。  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   設定 **表示** = **元素** 具有另存為元素，而不是做為屬性值的網域屬性。  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   若要變更序列化屬性和關聯性的順序，以滑鼠右鍵按一下項目資料下的項目，並使用 **移** 或 **下移** 功能表命令。  
  
## <a name="major-customization-using-program-code"></a>使用程式碼的主要自訂  
 您可以取代部分或全部的序列化演算法。  
  
 我們建議您先研究中的程式碼 **Dsl\Generated Code\Serializer.cs** 和 **SerializationHelper.cs**。  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>若要自訂特定類別的序列化  
  
1.  設定 **是自訂** 中該類別，其下的節點 **Xml 序列化行為**。  
  
2.  轉換所有範本，建置方案，並調查產生編譯錯誤。 幾乎每個錯誤的註解說明您必須提供何種程式碼。  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>若要提供您自己的整個模型的序列化  
  
1.  覆寫中 Dsl\GeneratedCode\SerializationHelper.cs 方法  
  
## <a name="options-in-xml-serialization-behavior"></a>在 Xml 序列化行為的選項  
 在 [DSL 總管] 中，Xml 序列化行為節點會包含每個網域類別、 關聯性、 圖形、 連接器和圖表類別的子節點。 在每個節點是內容和關聯性源自該元素的清單。 表示關聯性本身和其來源類別之下。  
  
 下表摘要說明您可以在 DSL 定義中的這一節中設定的選項。 在每個案例中，在 [DSL 總管] 中，選取元件，並設定 [屬性] 視窗中的選項。  
  
### <a name="xml-class-data"></a>Xml 類別資料  
 這些項目底下的 DSL 總管] 中找到 **Xml 序列化 Behavior\Class 資料**。  
  
|||  
|-|-|  
|屬性|描述|  
|具有自訂項目結構描述|如果為 True，表示網域類別具有自訂項目結構描述|  
|為自訂|請設為 **True** 如果您想要撰寫您自己這個網域類別的序列化和還原序列化程式碼。<br /><br /> 建置方案，並調查錯誤來探索詳細的指示。|  
|網域類別|這個類別的資料節點適用於網域類別。 唯讀。|  
|項目名稱|這個類別的項目 Xml 節點名稱。 預設值是網域類別名稱的小寫版本。|  
|Moniker 屬性名稱|Moniker 元素中用來包含參考的屬性名稱。 如果空白，則會使用識別碼或索引鍵屬性的名稱。<br /><br /> 在此範例中，這是"name":  `<personMoniker name="/Mike Nash"/>`|  
|Moniker 項目名稱|用來參考此類別的項目之 moniker 的 xml 項目名稱。<br /><br /> 預設值是類別名稱加上 「 Moniker"的小寫版本。 例如，`personMoniker`。|  
|Moniker 的型別名稱|產生的項目，這個類別的 moniker 的 xsd 型別的名稱。 XSD 處於 **Dsl\Generated 程式碼\\\*Schema.xsd**|  
|序列化識別碼|如果為 True，在檔案中包含的項目 GUID。 這必須為 true，如果沒有屬性標示為 **是 Moniker 索引鍵** 和 DSL 定義這個類別的參考關聯性。|  
|類型名稱|從指定的網域類別 xsd 中產生的 xml 類型的名稱。|  
|備註|這個項目相關聯的非正式附註|  
  
### <a name="xml-property-data"></a>Xml 屬性的資料  
 [類別] 節點下找到 Xml 屬性節點。  
  
|||  
|-|-|  
|屬性|描述|  
|網域屬性|要套用 xml 序列化組態資料的屬性。 唯讀。|  
|Moniker 索引鍵|如果為 True，此屬性是做為建立參考這個網域類別的執行個體的 moniker 索引鍵。|  
|是 Moniker 限定詞|如果為 True，此屬性用來建立 moniker 限定詞。 如果為 false，而且 SerializeId 不適用於這個網域類別，moniker 會限定之 moniker 的父項目中內嵌的樹狀結構。|  
|表示法|如果屬性，屬性會序列化為 xml 屬性。如果項目，它會序列化為元素。如果略過，就不序列化。|  
|Xml 名稱|用於 xml 屬性或項目代表屬性名稱。 根據預設，這是網域屬性名稱的小寫版本。|  
|備註|這個項目相關聯的非正式附註|  
  
### <a name="xml-role-data"></a>角色 Xml 資料  
 來源類別節點下找到角色的資料節點。  
  
|屬性|描述|  
|--------------|-----------------|  
|具有自訂 Moniker|將此設為 true，如果您想要提供自己的程式碼產生及解決周遊此關聯性的 moniker。<br /><br /> 詳細說明，以建置此方案，然後連按兩下錯誤訊息。|  
|網域關聯性|指定要套用這些選項的關係。 唯讀。|  
|省略項目|如果為 true，XML 節點對應至來源角色會省略結構描述。<br /><br /> 如果來源和目標類別之間有一個以上的關聯性，此角色的節點會區分屬於兩個關聯性的連結。 因此，建議您不要設定此選項在此情況下。|  
|角色項目名稱|指定的 XML 項目衍生自來源角色名稱。 預設值是角色的屬性名稱。|  
|使用完整的表單|如果為 true，每個目標項目或 moniker 住代表關聯性的 XML 節點。 這應該設定為 true，如果此關聯性具有自己的網域屬性。|  
  
## <a name="see-also"></a>請參閱  
 [巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [從定義域專屬語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)