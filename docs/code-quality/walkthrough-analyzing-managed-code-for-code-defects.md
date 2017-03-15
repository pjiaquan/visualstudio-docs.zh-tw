---
title: "逐步解說：分析 Managed 程式碼中的程式碼缺失 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析，逐步解說"
  - "Managed 程式碼，分析"
  - "程式碼分析工具，逐步解說"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 逐步解說：分析 Managed 程式碼中的程式碼缺失
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本逐步解說中，您會使用程式碼分析工具分析 managed 的專案的程式碼缺失。  
  
 本逐步解說將引導您逐步引導您使用程式碼分析來分析您的.NET managed 程式碼組件符合 Microsoft.NET Framework 設計方針。  
  
 在本逐步解說中，您︰  
  
-   分析和修正程式碼缺失警告。  
  
## <a name="prerequisites"></a>必要條件  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>建立類別庫  
  
#### <a name="to-create-a-class-library"></a>若要建立類別庫  
  
1.  在 **檔案** 功能表 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], ，按一下 [ **新增** ，然後按一下 **專案**。  
  
2.  在 **新的專案** 對話方塊的 [ **專案類型**, ，按一下 [ **Visual C#**。  
  
3.  在 **範本**, ，請選取 **類別庫**。  
  
4.  在 **名稱** 文字方塊中，輸入 **CodeAnalysisManagedDemo** 然後按一下 [ **確定**。  
  
5.  在建立專案之後，開啟 Class1.cs 檔。  
  
6.  下列程式碼取代 Class1.cs 中的現有文字︰  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  將 Class1.cs 檔案儲存。  
  
## <a name="analyze-the-project"></a>分析專案  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析 managed 的專案的程式碼缺失  
  
1.  CodeAnalysisManagedDemo 中選取專案 **方案總管] 中**。  
  
2.  在 **專案** ] 功能表上，按一下 **屬性**。  
  
     CodeAnalysisManagedDemo 屬性頁面隨即出現。  
  
3.  按一下 [ **CodeAnalysis**。  
  
4.  請確定  **建置時啟用程式碼分析 (定義 CODE_ANALYSIS 常數**) 會檢查。  
  
5.  從 **執行此規則集** 下拉式清單中，選取 **Microsoft 所有規則**。  
  
6.  在 **檔案** ] 功能表上，按一下 [ **儲存選取項目**, ，然後關閉 ManagedDemo 屬性頁。  
  
7.  在 **建置** ] 功能表上，按一下 [ **建置 ManagedDemo**。  
  
     CodeAnalysisManagedDemo 專案建置警告會報告 **程式碼分析** 和 **輸出** windows。  
  
     如果 **程式碼分析** 視窗沒有出現，在 **分析** ] 功能表上，選擇 [ **Windows** 然後 **選擇程式碼分析**。  
  
## <a name="correct-the-code-analysis-issues"></a>修正程式碼分析問題  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>若要修正程式碼分析規則違規  
  
1.  在 **檢視** ] 功能表上，按一下 [ **錯誤清單**。  
  
     根據您所選擇的開發人員設定檔，您可能必須設定為指向 **其他視窗** 上 **檢視** 功能表，然後再按一下 **錯誤清單**。  
  
2.  在 **方案總管] 中**, ，按一下 [ **顯示所有檔案**。  
  
3.  接下來，依序展開 [屬性] 節點，然後再開啟 AssemblyInfo.cs 檔案。  
  
4.  使用下列方式更正警告︰  
  
-   [CA1014︰ 以 CLSCompliantAttribute 的組件的標記](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 「 示範 」 應該以 CLSCompliantAttribute 標記和其值應為 true。  
  
    -   加入程式碼 `using``System;` 至 AssemblyInfo.cs 檔。  
  
         接下來，加入程式碼 `[assembly: CLSCompliant(true)]` 至 AssemblyInfo.cs 檔的結尾。  
  
         重建專案。  
  
-   [Ca1032︰ 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 將下列建構函式加入至這個類別︰ 公用 demo(String)  
  
    -   加入建構函式 `public demo (String s) : base(s) { }` 類別 `demo`。  
  
-   [Ca1032︰ 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 將下列建構函式加入至這個類別︰ 公用示範 （字串、 例外狀況）  
  
    -   加入建構函式 `public demo (String s, Exception e) : base(s, e) { }` 類別 `demo`。  
  
-   [Ca1032︰ 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 將下列建構函式加入至這個類別︰ 保護示範 （SerializationInfo、 StreamingContext）  
  
    -   加入程式碼 `using System.Runtime.Serialization;` Class1.cs 檔的開頭。  
  
         接下來，加入建構函式 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         重建專案。  
  
-   [Ca1032︰ 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design︰ 將下列建構函式加入至這個類別︰ 公用 demo()  
  
    -   加入建構函式 `public demo () : base() { }` 類別 `demo`**。**  
  
         重建專案。  
  
-   [CA1709︰ 識別項應該正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 將它變更為 'TestCode' 來修正命名空間名稱 'testCode' 的大小寫。  
  
    -   變更命名空間的大小寫 `testCode` 到 `TestCode`。  
  
-   [CA1709︰ 識別項應該正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 將它變更為 「 示範 」 以更正大小寫的型別名稱 「 示範 」。  
  
    -   變更之成員的名稱 `Demo`。  
  
-   [CA1709︰ 識別項應該正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming︰ 更正大小寫的成員名稱 'item' 將它變更為 「 項目 」。  
  
    -   變更之成員的名稱 `Item`。  
  
-   [CA1710︰ 識別項名稱應該使用正確的後置詞](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming︰ 重新命名 'testCode.demo' '的例外狀況' 結束。  
  
    -   變更的類別和其建構函式名稱 `DemoException`。  
  
-   [CA2210︰ 組件應包含有效的強式名稱](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)︰ 使用強式名稱金鑰簽署 'ManagedDemo'。  
  
    -   在 **專案** ] 功能表上，按一下 [ **ManagedDemo 屬性**。  
  
         專案屬性會出現。  
  
         按一下 [ **簽署**。  
  
         選取 **簽署組件** 核取方塊。  
  
         在 **選擇強式名稱金鑰檔** 清單中，選取 **\< 新增...>**。  
  
          **建立強式名稱金鑰** ] 對話方塊隨即出現。  
  
         在 **金鑰檔名稱**, ，輸入為 TestKey。  
  
         輸入密碼，然後按一下 **確定**。  
  
         在 **檔案** ] 功能表上，按一下 [ **儲存選取項目**, ，然後關閉 [屬性頁。  
  
         重建專案。  
  
-   [Ca2237︰ 必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage︰ 加入輸入為此型別實作 ISerializable '示範' [Serializable] 屬性。  
  
    -   新增 `[Serializable ()]` 屬性至類別 `demo`。  
  
         重建專案。  
  
 完成變更之後，將 Class1.cs 檔案看起來應該如下所示︰  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>排除的程式碼分析警告  
  
#### <a name="to-exclude-code-defect-warnings"></a>若要排除的程式碼缺失警告  
  
1.  針對每個剩餘的警告，執行下列作業︰  
  
    1.  在 [程式碼分析] 視窗中，選取警告。  
  
    2.  選擇 **動作**, ，然後選擇 [ **隱藏訊息**, ，然後選擇 [ **專案隱藏項目檔中**。  
  
     如需詳細資訊，請參閱 [How to︰ 使用功能表項目隱藏的警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  重建專案。  
  
     專案建置時沒有任何警告或錯誤訊息。