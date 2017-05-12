---
title: "使用 Windows 執行階段應用程式開發介面時的考量事項 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 執行階段應用程式開發介面"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 Windows 執行階段應用程式開發介面時的考量事項
您可以在 JavaScript 中使用 Windows 執行階段應用程式開發介面的幾乎每一個項目。  不過，Windows 執行階段項目的 JavaScript 表示的某些層面是您應該記住的。  
  
> [!IMPORTANT]
>  如需以 C\+\+、C\# 或 Visual Basic 建立 Windows 執行階段元件以及在 JavaScript 中使用這些元件的詳細資訊，請參閱[建立 Windows 執行階段元件](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133)。  
  
## Windows 執行階段型別的 JavaScript 表示的特殊案例  
  
-   字串：未初始化的字串做為 "undefined" 字串傳遞至 Windows 執行階段方法，而設定為 `null` 的字串則傳遞為字串 "null" \(每當 `null` 或 `undefined` 值強制型轉為字串，這就是 true\)。在您將字串傳遞至 Windows 執行階段方法之前，您應該將它初始化為空字串 \(""\)。  
  
-   介面：您無法在 JavaScript 中實作 Windows 執行階段介面。  
  
-   陣列：Windows 執行階段陣列無法調整大小，因此在 JavaScript 中調整陣列大小的方法無法在 Windows 執行階段陣列上運作。  
  
-   陣列：如果您將 JavaScript 陣列值傳遞至 Windows 執行階段方法，則會複製陣列。  Windows 執行階段方法無法修改陣列或其成員並將它傳回至 JavaScript 應用程式。  不過，您可以使用具型別陣列 \(例如，[Int32Array 物件](../javascript/reference/int32array-object.md)\)，不會複製它們。  
  
-   結構：Windows 執行階段結構是 JavaScript 的物件。  如果您想要將 Windows 執行階段結構傳遞至 Windows 執行階段方法，請勿使用 `new` 關鍵字執行個體化結構。  而是建立物件，並加入相關的成員和其值。  成員的名稱應該是駝峰式命名法：`SomeStruct.firstMember`。  
  
-   物件：JavaScript 物件不同於 Managed 程式碼物件 \(`System.Object`\)。  您不能將 JavaScript 物件傳遞給要求 `System.Object` 的 Windows 執行階段方法。  
  
-   物件識別：在許多情況下，在 Windows 執行階段和 JavaScript 之間來回傳遞的物件不會變更。  JavaScript 引擎會維護已知物件對應。  當物件從 Windows 執行階段傳回時，它會與對應比對，如果物件不存在，則建立新的物件。  對於表示 Windows 執行階段方法所傳回之介面的物件，會遵循相同程序。  例外狀況有兩種：  
  
    -   從 Windows 執行階段呼叫傳回，然後加入新 \(expando\) 屬性的物件，在傳回至 Windows 執行階段時不會保留其新屬性。  不過，當它們傳回至 JavaScript 應用程式時，因為它們符合現有的物件，所以傳回的物件有 expando 屬性。  
  
    -   Windows 執行階段中的結構和委派無法識別為與先前使用的結構或委派相同。  每次傳回結構或委派時，它會取得新的參考。  
  
-   名稱衝突：多個 Windows 執行階段介面可能具有相同名稱的成員。  如果在單一 JavaScript 物件 \(可以是執行階段類別或介面的表示\) 中合併，成員會以完整名稱表示。  您可以使用下列語法呼叫這些成員：`Class["MemberName"](parameter)`。  
  
     在下列程式碼，兩個介面都具有 Draw 方法，一個執行階段類別實作這兩個介面。  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     以下是如何在 JavaScript 中呼叫上述的程式碼。  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` 參數：如果 Windows 執行階段方法具有多個 `out` 參數，在 JavaScript 中此方法有一個 JavaScript 物件當做它的傳回值，而且此物件有對應至 `out` 參數的屬性。  例如，請考慮下列以 C\+\+ 撰寫的 Windows 執行階段簽章。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     這個簽章的 JavaScript 版本為：  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     在此範例中，`returnValue` 是有兩個欄位的 JavaScript 物件：`first` 和 `second`。  
  
-   靜態成員：Windows 執行階段會定義靜態成員和執行個體成員。  在 JavaScript，靜態成員加入至與 Windows 執行階段類別或介面相關聯的物件。  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 如需 Windows 執行階段基本型別的 JavaScript 表示的詳細資訊，請參閱 [以 JavaScript 表示 Windows 執行階段類型](../jswinrt/javascript-representation-of-windows-runtime-types.md)。