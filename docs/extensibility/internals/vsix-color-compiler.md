---
title: "VSIX 色彩編譯器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX 色彩編譯器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 擴充功能色彩編譯器工具會接受代表現有的 Visual Studio 佈景主題色彩的.xml 檔案的主控台應用程式並將它.pkgdef 檔案，以便可以在 Visual Studio 中使用這些色彩。 由於很輕易地比較.xml 檔案之間的差異，這項工具可用於管理原始檔控制中的自訂色彩的。 它也可以經由連結至建置環境，讓建置輸出的有效.pkgdef 檔。  
  
 **佈景主題的 XML 結構描述**  
  
 完整的佈景主題的.xml 檔案看起來像這樣︰  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **佈景主題**  
  
 \< 佈景主題> 項目會定義整個佈景主題。 主題必須至少包含一個 \< 類別> 項目。 佈景主題的項目定義如下︰  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|名稱|[必要]主題名稱|  
|GUID|[必要]佈景主題的 GUID （必須符合 GUID 格式）|  
  
 在 Visual studio 建立自訂色彩，這些色彩必須定義下列主題。 如果沒有色彩有特定的佈景主題，Visual Studio 會嘗試從淺色佈景主題載入遺失的色彩。  
  
|||  
|-|-|  
|**佈景主題名稱**|**GUID 的佈景主題**|  
|亮色調|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|暗色調|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|藍色|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|高對比|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **類別目錄**  
  
 \< 類別> 元素佈景主題中定義的色彩集合。 分類的名稱提供邏輯群組，而且應定義為短越好。 類別必須至少包含一個 \< 色彩> 項目。 類別目錄項目定義如下︰  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|名稱|[必要]分類的名稱|  
|GUID|[必要]類別的 GUID （必須符合 GUID 格式）|  
  
 **色彩**  
  
 \< 色彩> 項目會定義元件或 UI 狀態的色彩。 一種色彩的慣用命名配置是 [UI 類型] [狀態]。 如果其為備援，請勿使用 「 色彩 」 這個字。 色彩應該清楚地指出項目型別和的情況下，或 「 狀態 」，色彩會套用。 色彩不可空的且必須包含一個或兩個 \< 背景> 和 \< 前景> 項目。 色彩的項目定義如下︰  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|名稱|[必要]色彩的名稱|  
  
 **背景及/或前景**  
  
 \< 背景> 和 \< 前景> 項目定義的色彩值和背景或前景的 UI 項目類型。 這些項目有沒有子系。  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|類型|[必要]色彩的類型。 它可以是下列其中一項︰<br /><br /> *CT_INVALID:* 色彩是無效或未設定。<br /><br /> *CT_RAW:* 未經處理的 ARGB 值。<br /><br /> *CT_COLORINDEX:* 請勿使用。<br /><br /> *CT_SYSCOLOR:* SysColor 的 Windows 系統色彩。<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX Visual Studio 中的色彩。<br /><br /> *CT_AUTOMATIC:* 自動色彩。<br /><br /> *CT_TRACK_FOREGROUND:* 請勿使用。<br /><br /> *CT_TRACK_BACKGROUND:* 請勿使用。|  
|來源|[必要]色彩十六進位表示的值|  
  
 中的型別屬性的結構描述支援 __VSCOLORTYPE 列舉型別所支援的所有值。 不過，我們建議您使用只有 CT_RAW 和 CT_SYSCOLOR。  
  
 **全面整合**  
  
 這是有效的主題.xml 檔案的簡單範例︰  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>如何使用工具  
 **語法**  
  
 VsixColorCompiler \< XML 檔案> \< PkgDef 檔案> \< 選擇性引數>  
  
 **引數**  
  
||||  
|-|-|-|  
|**參數名稱**|**備註**|**必要或選用**|  
|未命名的 （.xml 檔案）|這是第一個未命名的參數，而且是要轉換的 XML 檔的路徑。|必要|  
|未命名的 （.pkgdef 檔）|這是第二個未命名的參數，而且會產生的.pkgdef 檔的輸出路徑。<br /><br /> 預設值︰ \< XML 檔名>.pkgdef|Optional|  
|/noLogo|設定這個旗標，就會停止列印的產品和著作權資訊。|Optional|  
|/?|列印說明資訊。|Optional|  
|/help|列印說明資訊。|Optional|  
  
 **範例**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml /noLogo  
  
## <a name="notes"></a>備註  
  
-   這個工具需要安裝最新版的 VC + + 執行階段。  
  
-   可支援只有單一檔案。 不支援大量轉換透過資料夾路徑。  
  
## <a name="sample-output"></a>範例輸出  
 工具所產生.pkgdef 檔將會類似於以下機碼︰  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```