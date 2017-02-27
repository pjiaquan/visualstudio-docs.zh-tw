---
title: "下拉式項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組合的項目 （VSCT XML 結構描述）"
  - "VSCT XML 結構描述項目組合"
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 下拉式項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義會出現在下拉式方塊中的命令。 有四種下拉式方塊的如下所示︰ 下拉式組合、 DynamicCombo、 IndexCombo 和 MRUCombo。  
  
## <a name="syntax"></a>語法  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要項。 GUID ID 的命令識別項的 GUID。|  
|id|必要項。 GUID ID 的命令識別項的識別碼。|  
|defaultWidth|必要項。 整數，指定像素寬度下拉式方塊。|  
|idCommandList|必要項。 這是傳送至使用中的命令目標，以擷取要顯示在下拉式方塊中的項目清單的識別碼。 識別碼會與控制項相同的 GUID 範圍中。|  
|priority|選擇項。 數值，指定的優先權。|  
|類型|選擇項。 列舉的值，指定按鈕類型。<br /><br /> 如果沒有指定，會使用按鈕。<br /><br /> 下拉式組合<br /> VSPackage 負責填入下拉式方塊的內容。 使用者無法在此下拉式清單的文字方塊中輸入任何內容。<br /><br /> DynamicCombo<br /> VSPackage 負責填入下拉式方塊的內容。 使用者可以編輯此組合，也在其中選取項目。<br /><br /> IndexCombo<br /> 只是它 DynamicCombo 相同便會產生索引的項目，而不是它的文字。<br /><br /> MRUCombo<br /> 填入 VSPackage 代表整合式的開發環境 (IDE)。  使用者可以編輯此下拉式方塊中。 IDE 會記住多達最後 16 個項目，每個下拉式方塊。<br /><br /> 當使用者在下拉式方塊中，選取項目，或輸入新的某些內容時，IDE 會通知適當的 VSPackage。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|父代|選擇項。 按鈕的父項目。|  
|CommandFlag|必要項。 請參閱 [命令旗標的項目](../extensibility/command-flag-element.md)。 CommandFlag 按鈕有效值，如下所示。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -篩選鍵<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|字串|必要項。 請參閱 [字串的項目](../extensibility/strings-element.md)。 您必須定義於子項。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|  
  
## <a name="example"></a>範例  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)