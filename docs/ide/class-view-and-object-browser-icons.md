---
title: "類別檢視和物件瀏覽器圖示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "圖示, 在物件瀏覽器中開啟"
  - "信號圖示"
  - "類別檢視工具, 符號"
  - "圖形符號"
  - "IntelliSense, 圖示"
  - "圖示, IntelliSense"
  - "符號, 物件瀏覽器圖示"
  - "物件瀏覽器, [類別檢視] 中的圖示"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 類別檢視和物件瀏覽器圖示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[**類別檢視**\] 和 \[**物件瀏覽器**\] 會顯示代表程式碼實體 \(Entity\) 的圖示，例如：命名空間 \(Namespace\)、類別 \(Class\)、函式和變數。  下表說明這些圖示：  
  
|圖示|描述|圖示|描述|  
|--------|--------|--------|--------|  
|![命名空間符號](../ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|命名空間|![宣告符號](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|方法或函式|  
|![類別圖示](../ide/media/vxclass_icon.png "vxClass\_Icon")|類別|![運算子符號](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|運算子|  
|![棒棒糖介面符號](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|介面|![屬性符號](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|屬性|  
|![結構符號](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|結構|![欄位圖示](../ide/media/vxfield_icon.png "vxField\_Icon")|欄位或變數|  
|![等位符號](../ide/media/vxunion_icon.png "vxUnion\_Icon")|Union|![事件符號](../ide/media/vxevent_icon.png "vxEvent\_Icon")|事件|  
|![列舉項目符號](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![常數圖示](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|常數|  
|![類型定義符號](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|TypeDef|![列舉項目符號](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|列舉項目|  
|![Visual Studio 模組符號](../ide/media/vxmodule_icon.gif "vxModule\_Icon")|模組|![對應項目符號](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|對應項目|  
|![擴充方法符號](../ide/media/extensionmethod.png "ExtensionMethod")|擴充方法|![宣告符號](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|外部宣告|  
|![委派符號](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|委派|![&#91;類別檢視&#93; 和 &#91;物件瀏覽器&#93; 的錯誤圖示](../ide/media/erroricon.png "ErrorIcon")|錯誤|  
|![例外狀況符號](../ide/media/vxexception_icon.png "vxException\_Icon")|例外狀況|![範本符號](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|範本|  
|![對應符號](../ide/media/vxmap_icon.png "vxMap\_Icon")|對應|![錯誤驚嘆號符號](../ide/media/vxerror_icon.png "vxError\_Icon")|未知|  
|![類型轉送符號](../ide/media/ob_type_forward.png "ob\_type\_forward")|型別轉送|||  
  
## 信號圖示  
 以下信號圖示適用所有先前的圖示並指出它們的存取範圍。  
  
> [!NOTE]
>  如果您的專案是包含在原始檔控制資料庫中，可能會顯示其他的信號圖示以表示原始檔控制狀態，例如簽入或簽出。  
  
|圖示|描述|  
|--------|--------|  
|\<沒有信號圖示\>|公用。  可從本元件和參照它的任何元件中進行存取。|  
|![指示 Protected 符號](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|保護。  可從包含之類別或型別，或從包含類別或型別衍生的元件中存取。|  
|![指示 Private 符號](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|私用。  只能從包含之類別或型別中存取。|  
|![指示 Sealed 符號](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|密封的。|  
|![指示 Friend&#47;Internal 符號](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|好友\/內部。  只能從專案中存取。|  
|![指示圖示箭頭](../ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|捷徑。  物件的捷徑。|  
  
## 請參閱  
 [檢視程式碼的結構](../ide/viewing-the-structure-of-code.md)