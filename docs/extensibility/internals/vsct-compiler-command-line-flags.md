---
title: "VSCT 編譯器命令列的旗標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 檔案編譯"
  - "編譯命令對應表檔案 （VSCT 檔案）"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VSCT 編譯器命令列的旗標
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 命令資料表 (VSCT) 編譯器會提供命令列參數，以確保成功編譯的.vsct 檔案。  
  
## <a name="command-line-parameters"></a>命令列參數  
 若要檢視從基本 VSCT 說明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **命令** ] 視窗中，瀏覽至 *Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Tools\Bin\ 資料夾，然後輸入︰  
  
```  
vsct /?  
```  
  
 這會傳回︰  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  字元-（虛線） 和 / （斜線） 會同時接受的標記法來表示命令列參數。  
  
 可接受的旗標，這些代表什麼意思是，如下所示。  
  
|參數|描述|  
|------------|-----------------|  
|-D|指定任何其他已定義的符號。|  
|-I|表示其他的 include 解析檔案參考時，應使用的路徑。|  
|-L|指定 <xref:System.Globalization.CultureInfo> 文化特性名稱，例如"EN-US"。|  
|-E|發出命令的項目，後面接著 [&#124; 指定的命名空間中的 C# 物件H &#124;N]:*filename*，C = C# 中，H = c + + 標頭，N = 命名空間。 需要 C# 命名空間。|  
|-v|詳細資訊輸出。|  
  
 -L 參數會指示編譯器選取字串，以產生二進位.cto 檔案對應至一組給定 <xref:System.Globalization.CultureInfo> 文化特性名稱。 指定的文化特性名稱應該符合一或多個語言屬性 [字串項目](../../extensibility/strings-element.md) .vsct 檔案中。 如果字串項目不有任何語言屬性時，它會繼承包含 [CommandTable 項目](../../extensibility/commandtable-element.md)。  
  
 .Vsct 檔可能有多個字串的項目，以及每個可能有不同的語言屬性。 全球化是多次執行 VSCT 編譯器，變更每個文化特性名稱-L 參數來達成。  
  
 如果-L 參數所指定的文化特性名稱不相符的任何字串項目 [語言] 屬性，編譯器會嘗試比對語言，並不是地區。 例如，如果找不到"EN-US"，編譯器會改用"en"。 如果無法做到，它會嘗試目前的文化特性的作業系統。 如果無法做到，它會編譯它找到的第一個字串項目。  
  
 -E 參數可用來發出 C 樣式的標頭檔，其中包含 [命令] 資料表中，所使用的符號，或發出 C# 檔案，其中包含物件的命令符號。  
  
 -D 和-I 參數具有 Cl.exe C 前置處理器旗標具有相同名稱的語法。 -D X = Y 格式的定義用於擴充的 XML 架構 \< 定義> 測試 `Condition` 屬性。 – 包含路徑用來解析 \< 包含>, ，\< Extern> 和 \< 點陣圖> 檔案參考。 如需詳細資訊，請參閱 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 VSCT 編譯器也可以進行先前建置的二進位檔案。 若要這樣做，請提供 [二進位檔案的 \< infile>。   如果 VSCT 編譯器所產生的二進位檔案，它都已內嵌其符號，且會產生輸出中的符號名稱 \< 符號> 輸出的區段。 如果 CTC 編譯器所產生的二進位檔，則輸出會包含實際的 Guid 和 Id。 產生目前版本的 Ctc.exe *.ctsym 檔案是否為二進位的輸入檔相同的資料夾中，會從該檔案載入符號，並用於輸出。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令資料表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)