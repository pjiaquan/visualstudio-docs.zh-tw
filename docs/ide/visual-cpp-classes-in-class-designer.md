---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[類別設計工具\] 支援 C\+\+ 類別 \(Class\)，並用與 Visual Basic 和 Visual C\# 類別圖案相同的方式，視覺化原生 \(Native\) C\+\+ 類別，而且 C\+\+ 類別還能擁有多重的繼承關係。  您可以展開類別圖案以顯示類別中的其他欄位和方法，或是予以摺疊以節省空間。  
  
> [!NOTE]
>  \[類別設計工具\] 不支援等位 \(一種特殊的類別，其中配置的記憶體僅為等位之最大資料成員所需要的數量\)。  
  
## 簡單繼承  
 當您將一個以上的類別拖曳到類別圖表中，而且這些類別具有類別繼承關係時，便會有箭號連接這些類別。  箭號會指向基底類別 \(Base Class\)。  例如，當下列類別在類別圖表中顯示時，箭號便會連接它們，並會從 B 指向 A。  
  
```  
class A {};  
class B : A {};  
```  
  
 您也可以只將類別 B 拖曳至類別圖表，以滑鼠右鍵按一下 B 的類別圖案，然後按一下 \[**顯示基底類別**\]。  這樣便會顯示其基底類別：A。  
  
## 多重繼承  
 \[類別設計工具\] 支援多重類別繼承關係的視覺化。  「*多重繼承*」會在衍生的類別具有一個以上基底類別的屬性 \(Attribute\) 時使用。  下列是多重繼承的範例：  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 當您將一個以上的類別拖曳到類別圖表中，而且這些類別具有多重類別繼承關係時，便會有箭號連接這些類別。  箭號會指向基底類別。  
  
 以滑鼠右鍵按一下某個類別圖案，然後按一下 \[**顯示基底類別**\]，便會顯示選取類別的基底類別。  
  
> [!NOTE]
>  \[**顯示衍生類別**\] 命令並沒有對 C\+\+ 程式碼提供支援。  您可以移至 \[類別檢視\]，展開型別節點，展開 \[**衍生型別**\] 子資料夾，然後將這些型別都拖曳到類別圖表上。  
  
 如需多重類別繼承的詳細資訊，請參閱[\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/zh-tw/3b74185e-2beb-4e29-8684-441e51d2a2ca)和[多個基底類別](/visual-cpp/cpp/multiple-base-classes)。  
  
## 抽象類別  
 \[類別設計工具\] 支援抽象類別 \(也稱為「抽象基底類別」\)。  這些是您絕對不會具現化的類別，但可以從中衍生其他類別。  使用本文件之前提及的「多重繼承」範例，就可以將 `Bird` 類別具現化為個別物件，如下所示：  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 不過，您可能不想將 `Swimmer` 類別具現化為個別物件。  而是只要從中衍生動物類別的其他型別，例如 `Penguin`、`Whale` 和 `Fish`。  在該情況下，您可以將 `Swimmer` 類別宣告為抽象基底類別。  
  
 若要將類別宣告為抽象，可以使用 `abstract` 關鍵字。  成員如果標記為抽象 \(或包含在抽象類別內\) 都是虛擬的，而且必須由衍生自此抽象類別的類別實作這些成員。  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 您也可以加入至少一個純虛擬函式 \(Pure Virtual Function\)，將類別宣告為抽象：  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 在 \[類別圖表\] 中顯示這些宣告時，類別名稱 `Swimmer` 和其純虛擬函式 `swim` 都會以斜體顯示在抽象類別圖案中，並附帶有 \[**抽象類別**\] 這個標記法。  請注意，抽象類別和一般類別的型別圖案都相同，不過抽象類別型別圖案的框線為虛線。  
  
 衍生自抽象基底類別的類別必須覆寫基底類別中的每個純虛擬函式，否則便無法具現化衍生類別。  例如，從 `Swimmer` 類別衍生 `Fish` 類別，則 `Fish` 必須覆寫 `swim` 方法：  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 在 \[類別圖表\] 中顯示此程式碼時，\[類別設計工具\] 會在 `Fish` 到 `Swimmer` 之間繪製一條繼承關聯線。  
  
## 匿名類別  
 \[類別設計工具\] 支援匿名類別 \(Anonymous Class\)。  「*匿名類別型別*」\(Anonymous Class Type\) 就是不用識別項宣告的類別。  這種類別不能具有建構函式 \(Constructor\) 或解構函式 \(Destructor\)，而且不能做為傳回值而從函式傳回。  您可以使用匿名類別來取代具有 typedef 名稱的類別名稱，如下列範例所示：  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 結構也可以是匿名的。  \[類別設計工具\] 會以顯示各自型別的相同方式，來顯示匿名類別和結構。  儘管您可以宣告及顯示匿名類別和結構，\[類別設計工具\] 卻不會使用您所指定的標記 \(Tag\) 名稱。  而是會使用 \[類別檢視\] 所產生的名稱。  類別或結構會在 \[類別檢視\] 和 \[類別設計工具\] 中顯示為稱為 \[**\_\_unnamed**\] 的項目。  
  
 如需匿名類別的詳細資訊，請參閱[匿名類別類型](/visual-cpp/cpp/anonymous-class-types)。  
  
## 樣板類別  
 \[類別設計工具\] 支援樣板類別 \(Template Class\) 的視覺化。  並且支援巢狀宣告。  下表顯示部分典型的宣告：  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> 樣板類別|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 樣板類別|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> 樣板類別|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 樣板類別|  
  
 下表顯示部分特製化的一些範例。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 樣板類別|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> 樣板類別|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> 樣板類別|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> 樣板類別|  
  
 下表顯示部分特製化中繼承的一些範例。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> 樣板類別<br /><br /> `B`<br /><br /> 類別<br /><br /> \(指向類別 A\)<br /><br /> `C`<br /><br /> 類別<br /><br /> \(指向類別 A\)|  
  
 下表顯示部分特製化樣板函式的一些範例。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U\> \(\+ 1 overload\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> 樣板類別<br /><br /> `B<T2>`<br /><br /> 樣板類別<br /><br /> \(B 包含在 \[**巢狀型別**\] 下的類別 A 內\)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> 類別<br /><br /> \-\> C\<int\><br /><br /> `C<T>`<br /><br /> 樣板類別|  
  
 下表顯示樣板繼承的一些範例。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> 類別<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> 類別<br /><br /> \(B 包含在 \[**巢狀型別**\] 下的類別 C 內\)<br /><br /> `C<T>`<br /><br /> 樣板類別|  
  
 下表顯示正式特製化類別連接的一些範例。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> 類別<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> 類別<br /><br /> `C<T>`<br /><br /> 樣板類別<br /><br /> `D`<br /><br /> 類別<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## 請參閱  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [類別和結構](/visual-cpp/cpp/classes-and-structs-cpp)   
 [匿名類別類型](/visual-cpp/cpp/anonymous-class-types)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/zh-tw/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [多個基底類別](/visual-cpp/cpp/multiple-base-classes)   
 [樣板](/visual-cpp/cpp/templates-cpp)