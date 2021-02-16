---
description: '詳細情報: 継承の基本 (Visual Basic)'
title: 継承の基本
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: facaa9a21fe3f99fc6e923ecb59dd977d72275ad
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485745"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="5bbbb-103">継承の基本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bbbb-103">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="5bbbb-104">`Inherits` ステートメントは、*基底クラス* と呼ばれる既存のクラスに基づいて、*派生クラス* と呼ばれる新しいクラスを宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-104">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="5bbbb-105">派生クラスは、基底クラスで定義されているプロパティ、メソッド、イベント、フィールド、および定数を継承し、これらを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-105">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="5bbbb-106">次のセクションでは、継承に関するいくつかの規則と、クラスが継承したり継承されたりする方法を変更するために使用できる修飾子について説明します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-106">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="5bbbb-107">既定では、`NotInheritable` キーワードでマークされていない限り、すべてのクラスが継承可能です。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-107">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="5bbbb-108">クラスは、プロジェクト内の他のクラスから、またはプロジェクトが参照する他のアセンブリのクラスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-108">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="5bbbb-109">複数の継承を許可する言語とは異なり、Visual Basic ではクラスでの単一継承のみが許可されます。つまり、派生クラスは基底クラスを 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-109">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="5bbbb-110">クラスでは複数の継承は許可されませんが、クラスは複数のインターフェイスを実装できます。これにより、同じ目的を効率的に実現できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-110">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="5bbbb-111">基底クラスで制限された項目を公開しないようにするには、派生クラスのアクセスの種類がその基底クラスと同等以上に制限されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-111">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="5bbbb-112">たとえば、`Public` クラスは、`Friend` または `Private` クラスを継承できず、`Friend` クラスは `Private` クラスを継承できません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-112">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="5bbbb-113">継承修飾子</span><span class="sxs-lookup"><span data-stu-id="5bbbb-113">Inheritance Modifiers</span></span>

<span data-ttu-id="5bbbb-114">Visual Basic では、継承をサポートするために、次のクラスレベルのステートメントと修飾子が導入されています。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-114">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="5bbbb-115">`Inherits` ステートメント - 基底クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-115">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="5bbbb-116">`NotInheritable` 修飾子 - プログラマがクラスを基底クラスとして使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-116">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="5bbbb-117">`MustInherit` 修飾子 - クラスが基底クラスとしてのみ使用されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-117">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="5bbbb-118">`MustInherit` クラスのインスタンスを直接作成することはできません。派生クラスの基底クラスのインスタンスとしてのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-118">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="5bbbb-119">(C++ や C# などの他のプログラミング言語では、このようなクラスについて説明するのに *抽象クラス* という用語を使用します。)</span><span class="sxs-lookup"><span data-stu-id="5bbbb-119">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="5bbbb-120">派生クラスのプロパティとメソッドのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="5bbbb-120">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="5bbbb-121">既定では、派生クラスは基底クラスのプロパティとメソッドを継承します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-121">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="5bbbb-122">派生クラス内の継承されたプロパティまたはメソッドの動作が異なる場合は、*オーバーライド* できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-122">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="5bbbb-123">つまり、派生クラスにメソッドの新しい実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-123">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="5bbbb-124">プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-124">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="5bbbb-125">`Overridable` - クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-125">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="5bbbb-126">`Overrides` - 基底クラスに定義された `Overridable` プロパティまたはメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-126">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="5bbbb-127">`NotOverridable` - 継承するクラスでプロパティまたはメソッドがオーバーライドされないようにします。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-127">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="5bbbb-128">既定では、`Public` メソッドは `NotOverridable` です。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-128">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="5bbbb-129">`MustOverride` - 派生クラスでプロパティまたはメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-129">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="5bbbb-130">`MustOverride` キーワードを使用する場合、メソッド定義は、`Sub`、`Function`、または `Property` ステートメントだけで構成されます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-130">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="5bbbb-131">他のステートメントは許可されません。具体的には、`End Sub` または `End Function` ステートメントはありません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-131">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="5bbbb-132">`MustOverride` メソッドは `MustInherit` クラスで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-132">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="5bbbb-133">給与支払いを処理するクラスを定義するとします。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-133">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="5bbbb-134">典型的な 1 週間の給与を計算する `RunPayroll` メソッドを含むジェネリック `Payroll` クラスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-134">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="5bbbb-135">その後、より特殊化された `BonusPayroll` クラスの基底クラスとして `Payroll` を使用できます。これは、従業員の賞与を配分するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-135">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="5bbbb-136">`BonusPayroll` クラスは、基底クラス `Payroll` で定義されている `PayEmployee` メソッドを継承し、オーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-136">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="5bbbb-137">次の例では、基底クラス `Payroll,` と、継承されたメソッド `PayEmployee` をオーバーライドする派生クラス `BonusPayroll` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-137">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="5bbbb-138">プロシージャ `RunPayroll` は、`Payroll` オブジェクトと `BonusPayroll` オブジェクトを作成してから、両方のオブジェクトの `PayEmployee` メソッドを実行する関数 `Pay` に渡します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-138">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="5bbbb-139">MyBase キーワード</span><span class="sxs-lookup"><span data-stu-id="5bbbb-139">The MyBase Keyword</span></span>

<span data-ttu-id="5bbbb-140">`MyBase` キーワードは、クラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-140">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="5bbbb-141">`MyBase` は、派生クラスでオーバーライドまたはシャドウされた基底クラスのメンバーにアクセスするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-141">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="5bbbb-142">特に、`MyBase.New` は、派生クラスのコンストラクターから基底クラスのコンストラクターを明示的に呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-142">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="5bbbb-143">たとえば、基底クラスから継承されたメソッドをオーバーライドする派生クラスを設計するとします。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-143">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="5bbbb-144">オーバーライドされたメソッドは、次のコード フラグメントに示されている、基底クラスのメソッドを呼び出して、戻り値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-144">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="5bbbb-145">`MyBase` の使用に関する制限事項を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-145">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="5bbbb-146">`MyBase` は、直接の基底クラスとその継承メンバーを参照します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-146">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="5bbbb-147">クラス内の `Private` メンバーへのアクセスには使用できません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-147">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="5bbbb-148">`MyBase` はキーワードであり、実際のオブジェクトではありません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-148">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="5bbbb-149">`MyBase` は、変数に割り当てたり、プロシージャに渡したり、`Is` の比較で使用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-149">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="5bbbb-150">`MyBase` で修飾されるメソッドは、直接の基底クラスで定義されている必要はありません。代わりに、間接的に継承された基底クラスで定義することができます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-150">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="5bbbb-151">`MyBase` によって修飾された参照を正しくコンパイルするために、一部の基底クラスには、呼び出しに存在するパラメーターの名前と型に一致するメソッドが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-151">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="5bbbb-152">`MyBase` を使用して `MustOverride` 基底クラスのメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-152">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="5bbbb-153">`MyBase` を使用してそれ自体を修飾することはできません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-153">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="5bbbb-154">したがって、次のコードは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-154">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="5bbbb-155">`MyBase` はモジュールでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-155">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="5bbbb-156">`MyBase` は、基底クラスが別のアセンブリにある場合に `Friend` としてマークされている基底クラスのメンバーにアクセスするために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-156">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="5bbbb-157">詳細ともう 1 つの例については、「[方法: 派生クラスによって非表示になっている変数にアクセスする](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-157">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="5bbbb-158">MyClass キーワード</span><span class="sxs-lookup"><span data-stu-id="5bbbb-158">The MyClass Keyword</span></span>

<span data-ttu-id="5bbbb-159">`MyClass` キーワードは、もともと実装されているクラスの現在のインスタンスを参照するオブジェクト変数と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-159">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="5bbbb-160">`MyClass` は `Me` に似ていますが、`MyClass` のすべてのメソッドとプロパティ呼び出しは、メソッドまたはプロパティが [NotOverridable](../../../language-reference/modifiers/notoverridable.md) であるかのように扱われます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-160">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="5bbbb-161">したがって、メソッドまたはプロパティは、派生クラスでのオーバーライドによる影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-161">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="5bbbb-162">`MyClass` はキーワードであり、実際のオブジェクトではありません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-162">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="5bbbb-163">`MyClass` は、変数に割り当てたり、プロシージャに渡したり、`Is` の比較で使用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-163">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="5bbbb-164">`MyClass` は、含まれているクラスとその継承メンバーを参照します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-164">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="5bbbb-165">`MyClass` は `Shared` メンバーの修飾子として使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-165">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="5bbbb-166">`MyClass` は `Shared` メソッド内では使用できませんが、インスタンス メソッド内で使用して、クラスの共有メンバーにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-166">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="5bbbb-167">`MyClass` は標準モジュールでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-167">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="5bbbb-168">`MyClass` は、基底クラスで定義されていて、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-168">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="5bbbb-169">このような参照は、`MyBase.`*メソッド* と同じ意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-169">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="5bbbb-170">次の例では、`Me` と `MyClass` を比較します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-170">The following example compares `Me` and `MyClass`.</span></span>

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

<span data-ttu-id="5bbbb-171">`derivedClass` が `testMethod` をオーバーライドしても、`useMyClass` の `MyClass` キーワードがオーバーライドの効果を無効にし、コンパイラは `testMethod` の基底クラスのバージョンの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="5bbbb-171">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bbbb-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bbbb-172">See also</span></span>

- [<span data-ttu-id="5bbbb-173">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="5bbbb-173">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="5bbbb-174">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="5bbbb-174">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
