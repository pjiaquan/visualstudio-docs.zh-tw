---
title: "如何：指定建置事件 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建置事件 [Visual Studio]"
  - "組建 [Visual Studio], 事件"
  - "事件 [Visual Studio], 組建"
  - "建置後事件"
  - "建置前事件"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：指定建置事件 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

請使用建置事件指定在開始執行建置前，或在建置結束後執行的命令。  只有在該建置成功地抵達建置程序中的這些點時，才會執行建置事件。  
  
 專案建置後，建置前事件會加入至名為 PreBuildEvent.bat 的檔案中，而建置後事件則會加入至名為 PostBuildEvent.bat 的檔案中。  如果您要確保執行錯誤檢查，請將您的錯誤檢查命令加入到建置步驟中。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 如何指定建置前和建置後事件  
  
#### 若要指定建置事件  
  
1.  在 \[**方案總管**\] 中，選取您要指定建置事件的專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
3.  選取 \[**建置事件**\] 索引標籤。  
  
4.  在 \[**建置前事件命令列**\] 方塊中，指定建置事件的語法。  
  
    > [!NOTE]
    >  如果專案是最新的且未觸發任何建置，則不會執行建置前事件。  
  
5.  在 \[**建置後事件命令列**\] 方塊中，指定建置事件的語法。  
  
    > [!NOTE]
    >  在執行 .bat 檔的所有建置後命令之前加入 `call` 陳述式。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
6.  在 \[**執行建置後事件**\] 方塊中，指定在何種情況下要執行建置後事件。  
  
    > [!NOTE]
    >  若要加入冗長的語法，或是從[建置前事件\/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)中選取任何建置巨集，請按一下省略符號按鈕 \(**...**\) 以顯示編輯方塊。  
  
     建置事件語法可包含命令提示字元上或 .bat 檔中任何有效的命令。  批次檔名稱前面應該加上 `call` 以確保所有的後續命令都會被執行。  
  
     **注意**：如果您的建置前或建置後事件未成功完成，可以用零 \(0，表示成功動作\) 以外的代碼結束事件動作來終止建置。  
  
## 範例：如何使用建置後事件變更資訊清單資訊  
 下列程序將示範如何從建置後事件 \(專案目錄中的 .exe.manifest 檔案\) 呼叫 .exe 命令，以設定應用程式資訊清單中的最小作業系統版本。  最小作業系統版本是四段式的數字，例如：4.10.0.0。  如果要這麼做，命令會變更資訊清單的 `<dependentOS>` 區段：  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### 若要建立 .exe 命令來變更應用程式資訊清單  
  
1.  建立命令的主控台應用程式 \(Console Application\)。  在 \[**檔案**\] 功能表上指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\]，按一下 \[**Windows**\]，然後再按一下 \[**主控台應用程式**\] 範本。  將專案命名為 `ChangeOSVersionCS`。  
  
3.  在 Program.cs 中，將下行加入至位於在檔案開頭的其他 `using` 陳述式：  
  
    ```  
    using System.Xml;  
    ```  
  
4.  在 `ChangeOSVersionCS` 命名空間中，以下列程式碼取代 `Program` 類別實作：  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     這個命令具有兩個引數：應用程式資訊清單的路徑 \(亦即，建置程序建立資訊清單的資料夾，通常為 Projectname.publish\) 及新的作業系統版本。  
  
5.  建置專案。  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
6.  將 .exe 檔案複製到目錄，例如：`C:\TEMP\ChangeOSVersionVB.exe`。  
  
 接著，在建置後事件中叫用這個命令，以修改應用程式資訊清單。  
  
#### 叫用建置後事件以修改應用程式資訊清單  
  
1.  針對要發行的專案建立 Windows 應用程式。  在 \[**檔案**\] 功能表上指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\]，按一下 \[**Windows**\]，然後再按一下 \[**Windows Form 應用程式**\] 範本。  將專案命名為 `CSWinApp`。  
  
3.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
4.  在 \[專案設計工具\] 中，找到 \[**發行**\] 頁，並將 \[**發行位置**\] 設定為 `C:\TEMP\`。  
  
5.  按一下 \[**立即發行**\]，發行專案。  
  
     資訊清單檔案便會建置，並放置於 `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` 中。  如果要檢視資訊清單，請以滑鼠右鍵按一下檔案，按一下 \[**開啟方式**\]，選取 \[**從清單選取程式**\]，然後再按一下 \[**記事本**\]。  
  
     在檔案中搜尋 `<osVersionInfo>` 項目。  例如，版本可能為：  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  在 \[專案設計工具\] 中，按一下 \[**建置事件**\] 索引標籤，然後再按一下 \[**建置後進行編輯**\] 按鈕。  
  
7.  在 \[**建置後事件命令列**\] 方塊中，輸入下列命令：  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     當建置專案時，這個命令會將應用程式資訊清單中的最小作業系統版本變更為 5.1.2600.0。  
  
     由於 `$(TargetPath)` 巨集表示建立可執行檔的完整路徑，因此 `$(TargetPath)`.manifest 將指定在 bin 目錄中所建立的應用程式資訊清單。  發行會將此資訊清單複製到前述所設定的發行位置。  
  
8.  重新發行專案。  移至 \[**發行**\] 頁，然後按一下 \[**立即發行**\]。  
  
     重新檢視資訊清單。  若要檢視資訊清單，請開啟發行目錄並以滑鼠右鍵按一下檔案，按一下 \[**開啟方式**\]，選取 \[**從清單選取程式**\]，然後再按一下 \[**記事本**\]。  
  
     版本資訊應該如下：  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## 請參閱  
 [專案設計工具、建置事件 \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [建置前事件\/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)