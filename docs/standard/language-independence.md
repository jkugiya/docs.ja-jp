---
title: 言語への非依存性、および言語非依存コンポーネント
description: C#、C++/CLI、F#、IronPython、VB、Visual COBOL、PowerShell など、.NET でサポートされる多くの言語の中のいずれかで開発する方法を説明します。
dev_langs:
- csharp
- vb
ms.date: 07/22/2016
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 0cd8179de929ea55212d600844e658d6946861ab
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103076"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="52a9b-103">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="52a9b-103">Language independence and language-independent components</span></span>

<span data-ttu-id="52a9b-104">.NET は言語に依存しません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-104">.NET is language independent.</span></span> <span data-ttu-id="52a9b-105">つまり、開発者は、C#、F#、および Visual Basic などの .NET 実装を対象とする多くの言語の中のいずれかで開発できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="52a9b-106">.NET 実装用に開発されたクラス ライブラリの型とメンバーには、最初に記述された言語を知らなくてもアクセスできます。元の言語の規則に従う必要もありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="52a9b-107">コンポーネントを開発しているのであれば、コンポーネントの言語にかかわらず、すべての .NET アプリからそのコンポーネントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-107">If you're a component developer, your component can be accessed by any .NET app, regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9b-108">この記事の最初の部分では、言語に依存しないコンポーネント、つまり、どの言語で記述されたアプリからでも使用できるコンポーネントの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-108">This first part of this article discusses creating language-independent components, that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="52a9b-109">また、複数の言語で記述されたソース コードから 1 つのコンポーネントまたはアプリを作成することもできます。この記事の 2 番目のパートにある「[言語間の相互運用性](#cross-language-interoperability)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="52a9b-110">任意の言語で記述された他のオブジェクトと完全に対話するには、すべての言語に共通の機能だけを呼び出し側に公開するようにオブジェクトを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="52a9b-111">この共通の機能セットは、生成されたアセンブリに適用される規則のセットである、共通言語仕様 (CLS: Common Language Specification) によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="52a9b-112">共通言語仕様は、「[ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/)」(標準の ECMA-335: 共通言語基盤) の第 1 部の第 7 ～ 11 項で定義されています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span></span>

<span data-ttu-id="52a9b-113">コンポーネントが共通言語仕様に準拠している場合は、CLS に準拠することが保証され、CLS をサポートするすべてのプログラミング言語で記述されたアセンブリのコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="52a9b-114">コンパイル時にコンポーネントが共通言語仕様に準拠しているかどうかを確認するには、[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 属性をソース コードに適用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="52a9b-115">詳細については、「[CLSCompliantAttribute 属性](#the-clscompliantattribute-attribute)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-115">For more information, see [The CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

## <a name="cls-compliance-rules"></a><span data-ttu-id="52a9b-116">CLS 準拠の規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-116">CLS compliance rules</span></span>

<span data-ttu-id="52a9b-117">ここでは、CLS に準拠したコンポーネントを作成するための規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-117">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="52a9b-118">規則規則の完全な一覧については、「[ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/)」(標準の ECMA-335: 共通言語基盤) の第 1 部の第 11 項を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-118">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/).</span></span>

> [!NOTE]
> <span data-ttu-id="52a9b-119">共通言語仕様では、コンシューマー (プログラムによって CLS 準拠のコンポーネントにアクセスする開発者)、フレームワーク (言語コンパイラを使用して CLS 準拠のライブラリを作成する開発者)、およびエクステンダー (CLS 準拠のコンポーネントを作成する言語コンパイラ、コード パーサーなどのツールを作成する開発者) に適用する、CLS 準拠の各規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-119">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="52a9b-120">ここでは、フレームワークに適用するときの規則に焦点を当てます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-120">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="52a9b-121">エクステンダーに適用する一部の規則は、[Reflection.Emit](xref:System.Reflection.Emit) を使用して作成されたアセンブリに適用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-121">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="52a9b-122">言語に依存しないコンポーネントをデザインするには、コンポーネントのパブリック インターフェイスに CLS 準拠の規則を適用するだけです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-122">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="52a9b-123">プライベートな実装は仕様に準拠する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-123">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52a9b-124">CLS 準拠の規則は、コンポーネントのパブリック インターフェイスにのみ適用されます。プライベート実装には適用されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-124">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="52a9b-125">たとえば、[Byte](xref:System.Byte) 以外の符号なし整数は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-125">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="52a9b-126">次の例の `Person` クラスは型 [UInt16](xref:System.UInt16) の `Age` プロパティを公開するので、次のコードではコンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-126">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="52a9b-127">Person クラスを CLS 準拠にするには、`Age` プロパティの型を `UInt16` から、CLS 準拠の 16 ビット符号付き整数である [Int16](xref:System.Int16) に変更します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-127">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="52a9b-128">プライベート `personAge` フィールドの型を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-128">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="52a9b-129">ライブラリのパブリック インターフェイスは、次の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-129">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="52a9b-130">パブリック クラスの定義。</span><span class="sxs-lookup"><span data-stu-id="52a9b-130">Definitions of public classes.</span></span>

* <span data-ttu-id="52a9b-131">パブリック クラスのパブリック メンバーの定義、および派生クラスからアクセスできるメンバー (つまり、protected メンバー) の定義。</span><span class="sxs-lookup"><span data-stu-id="52a9b-131">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="52a9b-132">パブリック クラスのパブリック メソッドのパラメーターおよび戻り値の型、派生クラスからアクセスできるメソッドのパラメーターおよび戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="52a9b-132">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="52a9b-133">CLS 準拠の規則を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-133">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="52a9b-134">これらの規則のテキストは、「[ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/)」(標準の ECMA-335: 共通言語基盤) からの引用で、Ecma International が 2012 年の著作権を保有しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-134">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="52a9b-135">これらの規則の詳細については、以降のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-135">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="52a9b-136">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="52a9b-136">Category</span></span> | <span data-ttu-id="52a9b-137">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="52a9b-137">See</span></span> | <span data-ttu-id="52a9b-138">ルール</span><span class="sxs-lookup"><span data-stu-id="52a9b-138">Rule</span></span> | <span data-ttu-id="52a9b-139">規則番号</span><span class="sxs-lookup"><span data-stu-id="52a9b-139">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="52a9b-140">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="52a9b-140">Accessibility</span></span> | [<span data-ttu-id="52a9b-141">メンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-141">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="52a9b-142">継承されたメソッドをオーバーライドする場合、アクセシビリティは変更してはいけない。ただし、別のアセンブリから継承されたメソッドをアクセシビリティ `family-or-assembly` でオーバーライドする場合は除く。</span><span class="sxs-lookup"><span data-stu-id="52a9b-142">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="52a9b-143">この場合、オーバーライドのアクセシビリティは `family` にすること。</span><span class="sxs-lookup"><span data-stu-id="52a9b-143">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="52a9b-144">10</span><span class="sxs-lookup"><span data-stu-id="52a9b-144">10</span></span>
<span data-ttu-id="52a9b-145">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="52a9b-145">Accessibility</span></span> | [<span data-ttu-id="52a9b-146">メンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-146">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="52a9b-147">型およびメンバーの可視性およびアクセシビリティについて、メンバーのシグネチャに指定されている型は、そのメンバーが可視でアクセス可能な場合、必ず可視でアクセス可能でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-147">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="52a9b-148">たとえば、アセンブリ外部から参照できるパブリックなメソッドには、アセンブリ内部でだけ可視である型が引数として含まれていてはいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-148">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="52a9b-149">メンバーのシグネチャに使用されているジェネリック型のインスタンスを構成する型の可視性およびアクセシビリティは、メンバーが可視でアクセス可能の場合、必ず可視でアクセス可能でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-149">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="52a9b-150">たとえば、アセンブリ外部から参照できるメンバーのシグネチャに指定されているジェネリック型のインスタンスに、アセンブリ内部でだけ可視である型の汎用引数が含まれていてはいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-150">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="52a9b-151">12</span><span class="sxs-lookup"><span data-stu-id="52a9b-151">12</span></span>
<span data-ttu-id="52a9b-152">配列</span><span class="sxs-lookup"><span data-stu-id="52a9b-152">Arrays</span></span> | [<span data-ttu-id="52a9b-153">配列</span><span class="sxs-lookup"><span data-stu-id="52a9b-153">Arrays</span></span>](#arrays) | <span data-ttu-id="52a9b-154">配列は、要素が CLS 準拠型で、すべての次元でインデックス番号が 0 から始まらなければならない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-154">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="52a9b-155">項目が配列の場合、オーバーロードどうしを区別するには配列要素の型を必要とする。</span><span class="sxs-lookup"><span data-stu-id="52a9b-155">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="52a9b-156">オーバーロードが 2 つ以上の配列型に基づく場合、要素型は名前付きの型でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-156">When overloading is based on two or more array types, the element types shall be named types.</span></span> | <span data-ttu-id="52a9b-157">16</span><span class="sxs-lookup"><span data-stu-id="52a9b-157">16</span></span>
<span data-ttu-id="52a9b-158">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-158">Attributes</span></span> | [<span data-ttu-id="52a9b-159">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-159">Attributes</span></span>](#attributes) | <span data-ttu-id="52a9b-160">属性は型 [System.Attribute](xref:System.Attribute) であるか、それから継承する型である必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-160">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="52a9b-161">41</span><span class="sxs-lookup"><span data-stu-id="52a9b-161">41</span></span>
<span data-ttu-id="52a9b-162">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-162">Attributes</span></span> | [<span data-ttu-id="52a9b-163">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-163">Attributes</span></span>](#attributes) | <span data-ttu-id="52a9b-164">CLS ではカスタム属性のエンコーディングのサブセットのみ使用できる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-164">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="52a9b-165">これらのエンコーディングに表示される型 (第 4 部を参照) は、[System.Type](xref:System.Type)、[System.String](xref:System.String)、[System.Char](xref:System.Char)、[System.Boolean](xref:System.Boolean)、[System.Byte](xref:System.Byte)、[System.Int16](xref:System.Int16)、[System.Int32](xref:System.Int32)、[System.Int64](xref:System.Int64)、[System.Single](xref:System.Single)、[System.Double](xref:System.Double)、および CLS 準拠の基底の整数型に基づく任意の列挙型のみである。</span><span class="sxs-lookup"><span data-stu-id="52a9b-165">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="52a9b-166">34</span><span class="sxs-lookup"><span data-stu-id="52a9b-166">34</span></span>
<span data-ttu-id="52a9b-167">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-167">Attributes</span></span> | [<span data-ttu-id="52a9b-168">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-168">Attributes</span></span>](#attributes) | <span data-ttu-id="52a9b-169">CLS では、公開参照される必須の修飾子 (`modreq`、第 2 部を参照) は使用できない。ただし、認識しないオプションの修飾子 (`modopt`、第 2 部を参照) は使用できる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-169">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="52a9b-170">35</span><span class="sxs-lookup"><span data-stu-id="52a9b-170">35</span></span>
<span data-ttu-id="52a9b-171">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-171">Constructors</span></span> | [<span data-ttu-id="52a9b-172">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-172">Constructors</span></span>](#constructors) | <span data-ttu-id="52a9b-173">オブジェクト コンストラクターでは、継承しているインスタンス データへのアクセスが発生する前に、基底クラスのインスタンス コンストラクターを呼び出さなければいけない</span><span class="sxs-lookup"><span data-stu-id="52a9b-173">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="52a9b-174">(コンストラクターが不要である値型は除く)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-174">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="52a9b-175">21</span><span class="sxs-lookup"><span data-stu-id="52a9b-175">21</span></span>
<span data-ttu-id="52a9b-176">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-176">Constructors</span></span> | [<span data-ttu-id="52a9b-177">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-177">Constructors</span></span>](#constructors) | <span data-ttu-id="52a9b-178">オブジェクト コンストラクターがオブジェクトの作成時以外で呼び出されてはならず、またオブジェクトが 2 度初期化されてもいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-178">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="52a9b-179">22</span><span class="sxs-lookup"><span data-stu-id="52a9b-179">22</span></span>
<span data-ttu-id="52a9b-180">列挙</span><span class="sxs-lookup"><span data-stu-id="52a9b-180">Enumerations</span></span> | [<span data-ttu-id="52a9b-181">列挙型</span><span class="sxs-lookup"><span data-stu-id="52a9b-181">Enumerations</span></span>](#enumerations) | <span data-ttu-id="52a9b-182">enum の基になる型は組み込みの CLS 整数型、フィールド名は "value__" であり、そのフィールドには `RTSpecialName` のマークが付けられる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-182">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="52a9b-183">7</span><span class="sxs-lookup"><span data-stu-id="52a9b-183">7</span></span>
<span data-ttu-id="52a9b-184">列挙型</span><span class="sxs-lookup"><span data-stu-id="52a9b-184">Enumerations</span></span> | [<span data-ttu-id="52a9b-185">列挙型</span><span class="sxs-lookup"><span data-stu-id="52a9b-185">Enumerations</span></span>](#enumerations) | <span data-ttu-id="52a9b-186">enum には 2 種類あり、[System.FlagsAttribute](xref:System.FlagsAttribute) カスタム属性 (第 4 部のライブラリを参照) の有無で区別する。</span><span class="sxs-lookup"><span data-stu-id="52a9b-186">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="52a9b-187">片方は名前付き整数値を表し、もう片方は名前付きビット フラグを表す。名前付きビット フラグは、それを組み合わせて名前のない値を生成できる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-187">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="52a9b-188">`enum` の値は、指定した値に限定されない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-188">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="52a9b-189">8</span><span class="sxs-lookup"><span data-stu-id="52a9b-189">8</span></span>
<span data-ttu-id="52a9b-190">列挙</span><span class="sxs-lookup"><span data-stu-id="52a9b-190">Enumerations</span></span> | [<span data-ttu-id="52a9b-191">列挙型</span><span class="sxs-lookup"><span data-stu-id="52a9b-191">Enumerations</span></span>](#enumerations) | <span data-ttu-id="52a9b-192">enum のリテラルな静的フィールドの型は、その enum 自体の型である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-192">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="52a9b-193">9</span><span class="sxs-lookup"><span data-stu-id="52a9b-193">9</span></span>
<span data-ttu-id="52a9b-194">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-194">Events</span></span> | [<span data-ttu-id="52a9b-195">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-195">Events</span></span>](#events) | <span data-ttu-id="52a9b-196">イベントを実装するメソッドは、メタデータ内で `SpecialName` のマークが付けられる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-196">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="52a9b-197">29</span><span class="sxs-lookup"><span data-stu-id="52a9b-197">29</span></span>
<span data-ttu-id="52a9b-198">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-198">Events</span></span> | [<span data-ttu-id="52a9b-199">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-199">Events</span></span>](#events) | <span data-ttu-id="52a9b-200">イベントとイベントのアクセサーのアクセシビリティは同一である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-200">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="52a9b-201">30</span><span class="sxs-lookup"><span data-stu-id="52a9b-201">30</span></span>
<span data-ttu-id="52a9b-202">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-202">Events</span></span> | [<span data-ttu-id="52a9b-203">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-203">Events</span></span>](#events) | <span data-ttu-id="52a9b-204">イベントの `add` メソッドおよび `remove` メソッドは、どちらもあってもなくてもよい。</span><span class="sxs-lookup"><span data-stu-id="52a9b-204">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="52a9b-205">31</span><span class="sxs-lookup"><span data-stu-id="52a9b-205">31</span></span>
<span data-ttu-id="52a9b-206">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-206">Events</span></span> | [<span data-ttu-id="52a9b-207">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-207">Events</span></span>](#events) | <span data-ttu-id="52a9b-208">`add` メソッドおよび `remove` メソッドは、それぞれパラメーターを 1 つ使用する。このパラメーターの型がイベントの型を規定する。また、パラメーターの型は [System.Delegate](xref:System.Delegate) の派生でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-208">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="52a9b-209">32</span><span class="sxs-lookup"><span data-stu-id="52a9b-209">32</span></span>
<span data-ttu-id="52a9b-210">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-210">Events</span></span> | [<span data-ttu-id="52a9b-211">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-211">Events</span></span>](#events) | <span data-ttu-id="52a9b-212">イベントは、特定の名前付けパターンに従わなくてはいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-212">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="52a9b-213">CLS 規則 29 で触れられている SpecialName 属性は、適切な名前比較で無視され、識別子規則に従わなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-213">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="52a9b-214">33</span><span class="sxs-lookup"><span data-stu-id="52a9b-214">33</span></span>
<span data-ttu-id="52a9b-215">例外</span><span class="sxs-lookup"><span data-stu-id="52a9b-215">Exceptions</span></span> | [<span data-ttu-id="52a9b-216">例外</span><span class="sxs-lookup"><span data-stu-id="52a9b-216">Exceptions</span></span>](#exceptions) | <span data-ttu-id="52a9b-217">スローできるオブジェクト型は、[System.Exception](xref:System.Exception)、またはそれを継承する型である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-217">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="52a9b-218">ただし、CLS 準拠のメソッドで他の型の例外のスローをブロックする必要はない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-218">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="52a9b-219">40</span><span class="sxs-lookup"><span data-stu-id="52a9b-219">40</span></span>
<span data-ttu-id="52a9b-220">全般</span><span class="sxs-lookup"><span data-stu-id="52a9b-220">General</span></span> | [<span data-ttu-id="52a9b-221">CLS 準拠の規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-221">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="52a9b-222">CLS 規則は、型の構成部分のうち、その型を定義しているアセンブリの外部からアクセスまたは参照できる部分にのみ適用される。</span><span class="sxs-lookup"><span data-stu-id="52a9b-222">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="52a9b-223">1</span><span class="sxs-lookup"><span data-stu-id="52a9b-223">1</span></span>
<span data-ttu-id="52a9b-224">全般</span><span class="sxs-lookup"><span data-stu-id="52a9b-224">General</span></span> | [<span data-ttu-id="52a9b-225">CLS 準拠の規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-225">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="52a9b-226">CLS 非準拠型のメンバーを CLS 準拠と指定しない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-226">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="52a9b-227">2</span><span class="sxs-lookup"><span data-stu-id="52a9b-227">2</span></span>
<span data-ttu-id="52a9b-228">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-228">Generics</span></span> | [<span data-ttu-id="52a9b-229">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-229">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-230">入れ子になった型は、少なくともその外側の型と同じ数のジェネリック パラメーターを持つ。</span><span class="sxs-lookup"><span data-stu-id="52a9b-230">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="52a9b-231">入れ子にされた型のジェネリック パラメーターは、それを囲む型のジェネリック パラメーターと、位置によって対応します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-231">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="52a9b-232">42</span><span class="sxs-lookup"><span data-stu-id="52a9b-232">42</span></span>
<span data-ttu-id="52a9b-233">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-233">Generics</span></span> | [<span data-ttu-id="52a9b-234">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-234">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-235">ジェネリック型の名前は、入れ子にされない型で宣言される型パラメーターの数をエンコードする必要がある。入れ子にされる場合は、上記の規則に従って、型に新しく組み込まれる型パラメーターの数をエンコードする必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-235">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="52a9b-236">43</span><span class="sxs-lookup"><span data-stu-id="52a9b-236">43</span></span>
<span data-ttu-id="52a9b-237">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-237">Generics</span></span> | [<span data-ttu-id="52a9b-238">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-238">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-239">ジェネリック型は必要な制約を再宣言して、基本型またはインターフェイスの制約がジェネリック型の制約で確実に満たされるようにする必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-239">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="52a9b-240">44</span><span class="sxs-lookup"><span data-stu-id="52a9b-240">44</span></span>
<span data-ttu-id="52a9b-241">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-241">Generics</span></span> | [<span data-ttu-id="52a9b-242">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-242">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-243">ジェネリック パラメーターの制約として使用される型は CLS に準拠する必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-243">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="52a9b-244">45</span><span class="sxs-lookup"><span data-stu-id="52a9b-244">45</span></span>
<span data-ttu-id="52a9b-245">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-245">Generics</span></span> | [<span data-ttu-id="52a9b-246">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-246">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-247">インスタンス化されたジェネリック型のメンバー (入れ子になった型も含む) の可視性およびアクセシビリティは、ジェネリック型の全体の宣言ではなく、特定のインスタンス化に対してスコープが設定される必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-247">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="52a9b-248">この場合でも、CLS 規則 12 の可視性規則とアクセシビリティ規則は同様に適用される。</span><span class="sxs-lookup"><span data-stu-id="52a9b-248">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="52a9b-249">46</span><span class="sxs-lookup"><span data-stu-id="52a9b-249">46</span></span>
<span data-ttu-id="52a9b-250">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="52a9b-250">Generics</span></span> | [<span data-ttu-id="52a9b-251">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-251">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="52a9b-252">抽象メソッドまたは仮想ジェネリック メソッドごとに、既定の具体的な実装がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-252">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="52a9b-253">47</span><span class="sxs-lookup"><span data-stu-id="52a9b-253">47</span></span>
<span data-ttu-id="52a9b-254">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-254">Interfaces</span></span> | [<span data-ttu-id="52a9b-255">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-255">Interfaces</span></span>](#interfaces) | <span data-ttu-id="52a9b-256">CLS 準拠のインターフェイスでは、CLS に準拠しないメソッドを実装するために、これらを定義する必要はない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-256">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="52a9b-257">18</span><span class="sxs-lookup"><span data-stu-id="52a9b-257">18</span></span>
<span data-ttu-id="52a9b-258">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-258">Interfaces</span></span> | [<span data-ttu-id="52a9b-259">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-259">Interfaces</span></span>](#interfaces) | <span data-ttu-id="52a9b-260">CLS 準拠インターフェイスでは、静的メソッドを定義してはいけない。また、フィールドも定義してはいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-260">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="52a9b-261">19</span><span class="sxs-lookup"><span data-stu-id="52a9b-261">19</span></span>
<span data-ttu-id="52a9b-262">メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-262">Members</span></span> | [<span data-ttu-id="52a9b-263">一般的な型メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-263">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="52a9b-264">グローバルで静的な (static) フィールドとメソッドは CLS 準拠ではありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-264">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="52a9b-265">36</span><span class="sxs-lookup"><span data-stu-id="52a9b-265">36</span></span>
<span data-ttu-id="52a9b-266">メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-266">Members</span></span> | -- | <span data-ttu-id="52a9b-267">静的リテラル値の指定には、フィールド初期化メタデータを使用する。</span><span class="sxs-lookup"><span data-stu-id="52a9b-267">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="52a9b-268">CLS 準拠のリテラルには、そのリテラルと同じ型 (または、そのリテラルが `enum` の場合は基本型) の値がフィールド初期化メタデータに指定されている必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-268">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="52a9b-269">13</span><span class="sxs-lookup"><span data-stu-id="52a9b-269">13</span></span>
<span data-ttu-id="52a9b-270">メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-270">Members</span></span> | [<span data-ttu-id="52a9b-271">一般的な型メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-271">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="52a9b-272">vararg 制約は CLS の一部ではなく、CLS でサポートする呼び出し規則だけが標準のマネージド呼び出し規則である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-272">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="52a9b-273">15</span><span class="sxs-lookup"><span data-stu-id="52a9b-273">15</span></span>
<span data-ttu-id="52a9b-274">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-274">Naming conventions</span></span> | [<span data-ttu-id="52a9b-275">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-275">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="52a9b-276">アセンブリは、識別子の頭文字および構成文字として使用できる文字セットを規定する Unicode Standard 3.0 の『Technical Report 15』の「Annex 7」に従う必要がある。詳細については、「[Unicode Normalization Forms](https://unicode.org/reports/tr15/)」(Unicode 正規化形式) を参照。</span><span class="sxs-lookup"><span data-stu-id="52a9b-276">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="52a9b-277">識別子は、Unicode 正規形 C に定義されている標準形式で記述する必要がある。CLS で 2 つの識別子が同じと見なされるのは、小文字マッピング (Unicode のロケール非依存で 1 対 1 の小文字による対応付け) が同じ場合である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-277">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="52a9b-278">つまり、CLS で 2 つの識別子が異なる場合、大文字小文字の違いだけではない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-278">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="52a9b-279">ただし、継承された定義をオーバーライドする場合、CLI では元の宣言と厳密に同じエンコーディングの使用が求められる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-279">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="52a9b-280">4</span><span class="sxs-lookup"><span data-stu-id="52a9b-280">4</span></span>
<span data-ttu-id="52a9b-281">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="52a9b-281">Overloading</span></span> | [<span data-ttu-id="52a9b-282">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-282">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="52a9b-283">CLS 準拠のスコープに導入されるすべての名前は、完全に独立した種類である必要があります。ただし、名前が同じでオーバーロードによって解決できる場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-283">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="52a9b-284">CTS では 1 つの型でメソッドとフィールドに同じ名前を使用できるが、CLS では使用できない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-284">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="52a9b-285">5</span><span class="sxs-lookup"><span data-stu-id="52a9b-285">5</span></span>
<span data-ttu-id="52a9b-286">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="52a9b-286">Overloading</span></span> | [<span data-ttu-id="52a9b-287">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-287">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="52a9b-288">フィールドおよび入れ子になった型について、CTS ではシグネチャでの区別が可能だが、CLS では識別子の比較だけで区別できる必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-288">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="52a9b-289">CLS 規則 39 の指定を除き、(識別子の比較により) 名前が同じであるメソッド、プロパティ、およびイベントでは、相違点は戻り値の型だけに限定されない</span><span class="sxs-lookup"><span data-stu-id="52a9b-289">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type, except as specified in CLS Rule 39</span></span> | <span data-ttu-id="52a9b-290">6</span><span class="sxs-lookup"><span data-stu-id="52a9b-290">6</span></span>
<span data-ttu-id="52a9b-291">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="52a9b-291">Overloading</span></span> | [<span data-ttu-id="52a9b-292">Overloads</span><span class="sxs-lookup"><span data-stu-id="52a9b-292">Overloads</span></span>](#overloads) | <span data-ttu-id="52a9b-293">プロパティおよびメソッドのみオーバーロードできる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-293">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="52a9b-294">37</span><span class="sxs-lookup"><span data-stu-id="52a9b-294">37</span></span>
<span data-ttu-id="52a9b-295">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="52a9b-295">Overloading</span></span> | [<span data-ttu-id="52a9b-296">Overloads</span><span class="sxs-lookup"><span data-stu-id="52a9b-296">Overloads</span></span>](#overloads) |<span data-ttu-id="52a9b-297">プロパティおよびメソッドは、パラメーターの数値と型にのみ基づいてオーバーロードできる。ただし、戻り値の型に基づいてオーバーロードできる変換演算子の `op_Implicit` と o`op_Explicit` は例外である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-297">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="52a9b-298">38</span><span class="sxs-lookup"><span data-stu-id="52a9b-298">38</span></span>
<span data-ttu-id="52a9b-299">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="52a9b-299">Overloading</span></span> | -- | <span data-ttu-id="52a9b-300">型で宣言された複数の CLS 準拠のメソッドに同じ名前が指定されている場合、特定の一連の型のインスタンス化において、これらのメソッドのパラメーターと戻り値の型は同じである。また、これらの型のインスタンス化で、すべてのメソッドをセマンティクス レベルで等価にする必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-300">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="52a9b-301">48</span><span class="sxs-lookup"><span data-stu-id="52a9b-301">48</span></span>
<span data-ttu-id="52a9b-302">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-302">Properties</span></span> | [<span data-ttu-id="52a9b-303">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-303">Properties</span></span>](#properties) | <span data-ttu-id="52a9b-304">プロパティの getter メソッドおよび setter メソッドを実装するメソッドは、メタデータで `SpecialName` とマークする。</span><span class="sxs-lookup"><span data-stu-id="52a9b-304">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="52a9b-305">24</span><span class="sxs-lookup"><span data-stu-id="52a9b-305">24</span></span>
<span data-ttu-id="52a9b-306">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-306">Properties</span></span> | [<span data-ttu-id="52a9b-307">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-307">Properties</span></span>](#properties) | <span data-ttu-id="52a9b-308">プロパティのアクセサーはすべて静的、すべて仮想、またはすべてインスタンスでなければならない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-308">A property's accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="52a9b-309">26</span><span class="sxs-lookup"><span data-stu-id="52a9b-309">26</span></span>
<span data-ttu-id="52a9b-310">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-310">Properties</span></span> | [<span data-ttu-id="52a9b-311">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-311">Properties</span></span>](#properties) | <span data-ttu-id="52a9b-312">プロパティの型は、getter の戻り値の型であり、かつ setter の最後の引数の型でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-312">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="52a9b-313">プロパティのパラメーターの型は、getter へのパラメーターの型であり、かつ setter の最後のパラメーター以外のすべての型でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-313">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="52a9b-314">すべての型は CLS 準拠でなければならない。また、マネージド ポインターであってはいけない (つまり、参照渡しではいけない)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-314">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="52a9b-315">27</span><span class="sxs-lookup"><span data-stu-id="52a9b-315">27</span></span>
<span data-ttu-id="52a9b-316">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-316">Properties</span></span> | [<span data-ttu-id="52a9b-317">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-317">Properties</span></span>](#properties) | <span data-ttu-id="52a9b-318">プロパティは、特定の名前付けパターンに従わなくてはいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-318">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="52a9b-319">CLS 規則 24 で触れられている `SpecialName` 属性は、適切な名前比較で無視され、識別子規則に従わなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-319">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="52a9b-320">プロパティには getter メソッド、setter メソッド、またはこの両方が必ずなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-320">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="52a9b-321">28</span><span class="sxs-lookup"><span data-stu-id="52a9b-321">28</span></span>
<span data-ttu-id="52a9b-322">型変換</span><span class="sxs-lookup"><span data-stu-id="52a9b-322">Type conversion</span></span> | [<span data-ttu-id="52a9b-323">型変換</span><span class="sxs-lookup"><span data-stu-id="52a9b-323">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="52a9b-324">op_Implicit または op_Explicit が指定されている場合は、強制変換のための別の方法を用意する必要がある。</span><span class="sxs-lookup"><span data-stu-id="52a9b-324">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="52a9b-325">39</span><span class="sxs-lookup"><span data-stu-id="52a9b-325">39</span></span>
<span data-ttu-id="52a9b-326">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-326">Types</span></span> | [<span data-ttu-id="52a9b-327">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-327">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-328">ボックス化された値型は CLS 準拠ではない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-328">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="52a9b-329">3</span><span class="sxs-lookup"><span data-stu-id="52a9b-329">3</span></span>
<span data-ttu-id="52a9b-330">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-330">Types</span></span> | [<span data-ttu-id="52a9b-331">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-331">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-332">シグネチャに出現するすべての型は CLS 準拠でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-332">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="52a9b-333">ジェネリック型のインスタンスを構成するすべての型は CLS 準拠でなければいけない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-333">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="52a9b-334">11</span><span class="sxs-lookup"><span data-stu-id="52a9b-334">11</span></span>
<span data-ttu-id="52a9b-335">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-335">Types</span></span> | [<span data-ttu-id="52a9b-336">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-336">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-337">型指定された参照は CLS 準拠ではありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-337">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="52a9b-338">14</span><span class="sxs-lookup"><span data-stu-id="52a9b-338">14</span></span>
<span data-ttu-id="52a9b-339">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-339">Types</span></span> | [<span data-ttu-id="52a9b-340">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-340">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-341">アンマネージ ポインター型は CLS 準拠ではない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-341">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="52a9b-342">17</span><span class="sxs-lookup"><span data-stu-id="52a9b-342">17</span></span>
<span data-ttu-id="52a9b-343">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-343">Types</span></span> | [<span data-ttu-id="52a9b-344">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-344">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-345">CLS 準拠のクラス、値型、およびインターフェイスでは、CLS に準拠しないメンバーの実装は不要である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-345">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="52a9b-346">20</span><span class="sxs-lookup"><span data-stu-id="52a9b-346">20</span></span>
<span data-ttu-id="52a9b-347">型</span><span class="sxs-lookup"><span data-stu-id="52a9b-347">Types</span></span> | [<span data-ttu-id="52a9b-348">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-348">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="52a9b-349">[System.Object](xref:System.Object) は CLS 準拠である。</span><span class="sxs-lookup"><span data-stu-id="52a9b-349">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="52a9b-350">これ以外のあらゆる CLS 準拠クラスは CLS 準拠クラスの継承でなければならない。</span><span class="sxs-lookup"><span data-stu-id="52a9b-350">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="52a9b-351">23</span><span class="sxs-lookup"><span data-stu-id="52a9b-351">23</span></span>

<span data-ttu-id="52a9b-352">サブセクションのインデックス:</span><span class="sxs-lookup"><span data-stu-id="52a9b-352">Index to subsections:</span></span>

* [<span data-ttu-id="52a9b-353">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-353">Types and type member signatures</span></span>](#types-and-type-member-signatures)
* [<span data-ttu-id="52a9b-354">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-354">Naming conventions</span></span>](#naming-conventions)
* [<span data-ttu-id="52a9b-355">型変換</span><span class="sxs-lookup"><span data-stu-id="52a9b-355">Type conversion</span></span>](#type-conversion)
* [<span data-ttu-id="52a9b-356">配列</span><span class="sxs-lookup"><span data-stu-id="52a9b-356">Arrays</span></span>](#arrays)
* [<span data-ttu-id="52a9b-357">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-357">Interfaces</span></span>](#interfaces)
* [<span data-ttu-id="52a9b-358">列挙型</span><span class="sxs-lookup"><span data-stu-id="52a9b-358">Enumerations</span></span>](#enumerations)
* [<span data-ttu-id="52a9b-359">一般的な型メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-359">Type members in general</span></span>](#type-members-in-general)
* [<span data-ttu-id="52a9b-360">メンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-360">Member accessibility</span></span>](#member-accessibility)
* [<span data-ttu-id="52a9b-361">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-361">Generic types and members</span></span>](#generic-types-and-members)
* [<span data-ttu-id="52a9b-362">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-362">Constructors</span></span>](#constructors)
* [<span data-ttu-id="52a9b-363">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-363">Properties</span></span>](#properties)
* [<span data-ttu-id="52a9b-364">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-364">Events</span></span>](#events)
* [<span data-ttu-id="52a9b-365">Overloads</span><span class="sxs-lookup"><span data-stu-id="52a9b-365">Overloads</span></span>](#overloads)
* [<span data-ttu-id="52a9b-366">例外</span><span class="sxs-lookup"><span data-stu-id="52a9b-366">Exceptions</span></span>](#exceptions)
* [<span data-ttu-id="52a9b-367">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-367">Attributes</span></span>](#attributes)

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="52a9b-368">型および型メンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="52a9b-368">Types and type member signatures</span></span>

<span data-ttu-id="52a9b-369">[System.Object](xref:System.Object) 型は CLS に準拠しており、.NET 型システムのすべてのオブジェクト型の基本型です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-369">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET type system.</span></span> <span data-ttu-id="52a9b-370">.NET の継承は暗黙的また明示的に行われます。たとえば、[String](xref:System.String) クラスは `Object` クラスから暗黙的に継承します。また、[CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) クラスは、[ArgumentException](xref:System.ArgumentException) クラスから明示的に継承し、これは [Exception](xref:System.Exception) クラスから明示的に継承します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-370">Inheritance in .NET is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="52a9b-371">派生型を CLS 準拠にするには、その基本型も CLS に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-371">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="52a9b-372">次の例は、基本型が CLS に準拠していない派生型を示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-372">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="52a9b-373">これは、符号なし 32 ビット整数をカウンターとして使用する `Counter` 基底クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-373">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="52a9b-374">クラスには、符号なし整数をラップすることでカウンター機能が用意されます。このため、クラスは CLS 非準拠としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-374">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="52a9b-375">結果として、派生クラス `NonZeroCounter` も CLS に準拠しなくなります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-375">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="52a9b-376">メソッドの戻り値の型、プロパティ型を含め、メンバー シグネチャに表示されるすべての型が CLS に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-376">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="52a9b-377">さらに、ジェネリック型の場合は、次の要件もあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-377">In addition, for generic types:</span></span>

* <span data-ttu-id="52a9b-378">ジェネリック型のインスタンスを構成するすべての型が、CLS に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-378">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="52a9b-379">ジェネリック パラメーターで制約として使用されるすべての型が、CLS に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-379">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="52a9b-380">.NET [共通型システム](common-type-system.md)には、共通言語ランタイムが直接サポートする組み込み型がいくつか含まれ、アセンブリのメタデータで特別にエンコードされています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-380">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="52a9b-381">これらの組み込み型のうち、次の表に示す型は CLS に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-381">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="52a9b-382">CLS 準拠型</span><span class="sxs-lookup"><span data-stu-id="52a9b-382">CLS-compliant type</span></span> | <span data-ttu-id="52a9b-383">説明</span><span class="sxs-lookup"><span data-stu-id="52a9b-383">Description</span></span>
------------------ | -----------
[<span data-ttu-id="52a9b-384">Byte</span><span class="sxs-lookup"><span data-stu-id="52a9b-384">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="52a9b-385">8 ビット符号なし整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-385">8-bit unsigned integer</span></span>
[<span data-ttu-id="52a9b-386">Int16</span><span class="sxs-lookup"><span data-stu-id="52a9b-386">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="52a9b-387">16 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-387">16-bit signed integer</span></span>
[<span data-ttu-id="52a9b-388">Int32</span><span class="sxs-lookup"><span data-stu-id="52a9b-388">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="52a9b-389">32 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-389">32-bit signed integer</span></span>
[<span data-ttu-id="52a9b-390">Int64</span><span class="sxs-lookup"><span data-stu-id="52a9b-390">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="52a9b-391">64 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-391">64-bit signed integer</span></span>
[<span data-ttu-id="52a9b-392">Single</span><span class="sxs-lookup"><span data-stu-id="52a9b-392">Single</span></span>](xref:System.Single) | <span data-ttu-id="52a9b-393">単精度浮動小数点数値</span><span class="sxs-lookup"><span data-stu-id="52a9b-393">Single-precision floating-point value</span></span>
[<span data-ttu-id="52a9b-394">Double</span><span class="sxs-lookup"><span data-stu-id="52a9b-394">Double</span></span>](xref:System.Double) | <span data-ttu-id="52a9b-395">倍精度浮動小数点数値</span><span class="sxs-lookup"><span data-stu-id="52a9b-395">Double-precision floating-point value</span></span>
[<span data-ttu-id="52a9b-396">Boolean</span><span class="sxs-lookup"><span data-stu-id="52a9b-396">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="52a9b-397">true または false 値型</span><span class="sxs-lookup"><span data-stu-id="52a9b-397">true or false value type</span></span>
[<span data-ttu-id="52a9b-398">Char</span><span class="sxs-lookup"><span data-stu-id="52a9b-398">Char</span></span>](xref:System.Char) | <span data-ttu-id="52a9b-399">UTF-16 でエンコードされたコード単位</span><span class="sxs-lookup"><span data-stu-id="52a9b-399">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="52a9b-400">Decimal</span><span class="sxs-lookup"><span data-stu-id="52a9b-400">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="52a9b-401">10 進浮動小数点数以外</span><span class="sxs-lookup"><span data-stu-id="52a9b-401">Non-floating-point decimal number</span></span>
[<span data-ttu-id="52a9b-402">IntPtr</span><span class="sxs-lookup"><span data-stu-id="52a9b-402">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="52a9b-403">プラットフォーム定義サイズのポインターまたはハンドル</span><span class="sxs-lookup"><span data-stu-id="52a9b-403">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="52a9b-404">String</span><span class="sxs-lookup"><span data-stu-id="52a9b-404">String</span></span>](xref:System.String) | <span data-ttu-id="52a9b-405">0 個以上の Char オブジェクトのコレクション</span><span class="sxs-lookup"><span data-stu-id="52a9b-405">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="52a9b-406">次の表に示す組み込み型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-406">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="52a9b-407">非準拠型</span><span class="sxs-lookup"><span data-stu-id="52a9b-407">Non-compliant type</span></span> | <span data-ttu-id="52a9b-408">説明</span><span class="sxs-lookup"><span data-stu-id="52a9b-408">Description</span></span> | <span data-ttu-id="52a9b-409">CLS に準拠する代替</span><span class="sxs-lookup"><span data-stu-id="52a9b-409">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="52a9b-410">SByte</span><span class="sxs-lookup"><span data-stu-id="52a9b-410">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="52a9b-411">8 ビット符号付き整数データ型</span><span class="sxs-lookup"><span data-stu-id="52a9b-411">8-bit signed integer data type</span></span> | [<span data-ttu-id="52a9b-412">Int16</span><span class="sxs-lookup"><span data-stu-id="52a9b-412">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="52a9b-413">UInt16</span><span class="sxs-lookup"><span data-stu-id="52a9b-413">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="52a9b-414">16 ビット符号なし整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-414">16-bit unsigned integer</span></span> | [<span data-ttu-id="52a9b-415">Int32</span><span class="sxs-lookup"><span data-stu-id="52a9b-415">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="52a9b-416">UInt32</span><span class="sxs-lookup"><span data-stu-id="52a9b-416">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="52a9b-417">32 ビット符号なし整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-417">32-bit unsigned integer</span></span> | [<span data-ttu-id="52a9b-418">Int64</span><span class="sxs-lookup"><span data-stu-id="52a9b-418">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="52a9b-419">UInt64</span><span class="sxs-lookup"><span data-stu-id="52a9b-419">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="52a9b-420">64 ビット符号なし整数</span><span class="sxs-lookup"><span data-stu-id="52a9b-420">64-bit unsigned integer</span></span> | <span data-ttu-id="52a9b-421">[Int64](xref:System.Int64) (オーバーフローの可能性あり)、[BigInteger](xref:System.Numerics.BigInteger)、または [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="52a9b-421">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="52a9b-422">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="52a9b-422">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="52a9b-423">符号なしポインターまたはハンドル</span><span class="sxs-lookup"><span data-stu-id="52a9b-423">Unsigned pointer or handle</span></span> | [<span data-ttu-id="52a9b-424">IntPtr</span><span class="sxs-lookup"><span data-stu-id="52a9b-424">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="52a9b-425">.NET クラス ライブラリまたはその他のクラス ライブラリには、CLS に準拠していない他の型が含まれる場合があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-425">The .NET Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="52a9b-426">ボックス化された値型。</span><span class="sxs-lookup"><span data-stu-id="52a9b-426">Boxed value types.</span></span> <span data-ttu-id="52a9b-427">次の C# コード例では、`int*` という名前の型 `Value` のパブリック プロパティを持つクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-427">The following C# example creates a class that has a public property of type `int*` named `Value`.</span></span> <span data-ttu-id="52a9b-428">`int*` はボックス化された値型であるため、コンパイラは CLS 非準拠としてフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-428">Because an `int*` is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="52a9b-429">型指定された参照。オブジェクトへの参照および型への参照を含む特別なコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-429">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="52a9b-430">型が CLS に準拠していない場合は、*isCompliant* パラメータの値が `false` に指定された [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 属性をそれに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-430">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="52a9b-431">詳細については、「[CLSCompliantAttribute 属性](#the-clscompliantattribute-attribute)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-431">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="52a9b-432">次の例は、メソッド シグネチャとジェネリック型のインスタンス化で発生する CLS 準拠の問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-432">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="52a9b-433">ここでは、`InvoiceItem` クラスを、型 [UInt32](xref:System.UInt32) のプロパティ、型 [Nullable(Of UInt32)](xref:System.Nullable%601) のプロパティ、および型 `UInt32` と `Nullable(Of UInt32)` のパラメーターが指定されたコンストラクターで定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-433">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="52a9b-434">この例をコンパイルしようとすると、4 つのコンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-434">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="52a9b-435">コンパイラの警告が表示されないようにするには、`InvoiceItem` パブリック インターフェイスの CLS 非準拠型を準拠型に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-435">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="52a9b-436">ここで示した特定の型以外にも、CLS に準拠していないカテゴリはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-436">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="52a9b-437">たとえば、アンマネージ ポインター型やアンマネージ関数ポインター型などです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-437">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="52a9b-438">次の例では、整数へのポインターを使用して整数の配列を作成するので、コンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-438">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="52a9b-439">CLS 準拠の抽象クラス (つまり、C# で `abstract` とマークされたクラス) については、そのクラスのすべてのメンバーも CLS に準拠にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-439">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="52a9b-440">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="52a9b-440">Naming conventions</span></span>

<span data-ttu-id="52a9b-441">一部のプログラミング言語は大文字と小文字が区別されるので、識別子 (名前空間、型、メンバーの名前など) は、大文字と小文字が違うだけで相違します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-441">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="52a9b-442">2 つの識別子が同じと見なされるのは、小文字マッピングが同じ場合です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-442">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="52a9b-443">次の C# コード例では、2 つのパブリック クラス、`Person` および `person` を定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-443">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="52a9b-444">このクラスは大文字と小文字のみが異なるので、コンパイラは CLS 非準拠としてフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-444">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="52a9b-445">名前空間、型、およびメンバーの名前など、プログラミング言語の識別子は、[Unicode 標準](https://unicode.org/reports/tr15/)に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-445">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="52a9b-446">これによって、次のことが起こります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-446">This means that:</span></span>

* <span data-ttu-id="52a9b-447">識別子の最初の文字は Unicode の大文字と小文字、大文字と小文字の組み合わせ、修飾子文字、その他の文字、または文字数の番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-447">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="52a9b-448">Unicode 文字のカテゴリの詳細については、「[System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) 列挙体」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-448">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="52a9b-449">2 文字目以降には、最初の文字で使用できる文字のほかに、非空白記号、空白結合記号、10 進数、接続符号、書式指定コードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-449">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuation, and formatting codes.</span></span>

<span data-ttu-id="52a9b-450">識別子を比較する場合は、その前に書式設定コードを除外してから、識別子を Unicode 正規形 C に変換する必要があります。これは 1 つの文字を、UTF-16 でエンコードされた複数のコード単位で表すことができるからです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-450">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="52a9b-451">同じコード単位を Unicode 正規形 C で生成する文字シーケンスは CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-451">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="52a9b-452">次の例では、最初にオングストローム文字 (U+212B) である `Å` という名前のプロパティを定義し、次に、上に丸が付く LATIN の大文字 A (U+00C5) である `Å` という名前のプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-452">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å`, which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="52a9b-453">C# コンパイラは、ソース コードを CLS 非準拠としてフラグします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-453">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="52a9b-454">特定のスコープ内のメンバー名 (アセンブリ内の名前空間、名前空間内の型、型内のメンバーなど) は一意である必要があります。ただし、オーバーロードによって解決される名前は除きます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-454">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="52a9b-455">この要件は、共通型システムの要件よりも厳格です。共通型システムでは、スコープ内のメンバーは種類が異なっていれば、たとえば、種類がメソッドのメンバーとフィールドのメンバーは、同じ名前を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-455">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="52a9b-456">特に、型メンバーの場合は次の要件もあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-456">In particular, for type members:</span></span>

* <span data-ttu-id="52a9b-457">フィールドと入れ子になった型は名前でのみ識別されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-457">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="52a9b-458">名前が同じメソッド、プロパティ、およびイベントは、戻り値の型以外で区別できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-458">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="52a9b-459">次の例は、メンバー名がスコープ内で一意でなければならない要件を示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-459">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="52a9b-460">ここでは、`Converter` という名前の 4 つのメンバーを含む `Conversion` という名前のクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-460">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="52a9b-461">3 つがメソッドで、1 つはプロパティです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-461">Three are methods, and one is a property.</span></span> <span data-ttu-id="52a9b-462">`Int64` パラメーターを含むメソッドには一意の名前が付けられますが、`Int32` パラメーターが指定された 2 つのメソッドには一意の名前は付けられません。これは戻り値がメンバーのシグネチャの一部と見なされないからです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-462">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="52a9b-463">また、`Conversion` プロパティもこの要件に違反しています。プロパティの名前は、オーバーロードされたメソッドと同じにできないからです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-463">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="52a9b-464">個々の言語に一意のキーワードが含まれるので、共通言語ランタイムを対象にする言語も、キーワードと一致する識別子 (型名など) を参照するための機構を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-464">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="52a9b-465">たとえば、`case` は、C# と Visual Basic のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-465">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="52a9b-466">ただし、次の Visual Basic コード例では、左右の中かっこを使用して、`case` キーワードと `case` という名前のクラスを明確に区別できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-466">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="52a9b-467">それ以外の場合は、エラー メッセージ "キーワードは、識別子として有効ではありません" が表示され、コンパイルできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-467">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="52a9b-468">次の C# コード例では、@ シンボルを使用して `case` クラスをインスタンス化することで、識別子と言語キーワードを区別できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-468">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="52a9b-469">これがないと、C# コンパイラによって 2 つのエラー メッセージ "型が必要です" および "'case' は無効です" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-469">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="52a9b-470">型変換</span><span class="sxs-lookup"><span data-stu-id="52a9b-470">Type conversion</span></span>

<span data-ttu-id="52a9b-471">共通言語仕様では、次の 2 つの変換演算子が定義されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-471">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="52a9b-472">`op_Implicit`。データまたは精度の損失につながらない拡大変換に使用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-472">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="52a9b-473">たとえば、[Decimal](xref:System.Decimal) 構造体には、整数型の値と [Char](xref:System.Char) 値を `Decimal` 値に変換できるように、オーバーロードされた `op_Implicit` 演算子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-473">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="52a9b-474">`op_Explicit`。絶対値 (狭い範囲の値に変換される値) または精度の損失につながる可能性がある縮小変換に使用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-474">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="52a9b-475">たとえば、`Decimal` 構造体には、[Double](xref:System.Double) 値と [Single](xref:System.Single) 値を `Decimal` に変換し、`Decimal` 値を整数値、`Double`、`Single`、および `Char` に変換できるように、オーバーロードされた `op_Explicit` 演算子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-475">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="52a9b-476">ただし、すべての言語で、演算子のオーバーロードまたはカスタム演算子の定義がサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-476">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="52a9b-477">これらの変換演算子を実装する場合は、他の方法で変換を実行する方法も用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-477">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="52a9b-478">ここでは、`From`Xxx メソッドおよび`To`Xxx メソッドを用意することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-478">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="52a9b-479">次の例では、CLS に準拠する暗黙的な変換と明示的な変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-479">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="52a9b-480">ここでは、符号付き倍精度浮動小数点数を表す `UDouble` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-480">It creates a `UDouble` class that represents a signed double-precision, floating-point number.</span></span> <span data-ttu-id="52a9b-481">暗黙的な変換については、`UDouble` から `Double`、明示的な変換については、`UDouble` から `Single`、`Double` から `UDouble`、および `Single` から `UDouble` への例を示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-481">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="52a9b-482">また、暗黙的な変換演算子の代替として `ToDouble` メソッドを、明示的な変換演算子の代替として `ToSingle`、`FromDouble`、`FromSingle` の各メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-482">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="52a9b-483">配列</span><span class="sxs-lookup"><span data-stu-id="52a9b-483">Arrays</span></span>

<span data-ttu-id="52a9b-484">CLS 準拠の配列は、次の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="52a9b-484">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="52a9b-485">配列の次元の下限値は 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-485">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="52a9b-486">次の例では、下限が 1 の CLS 非準拠の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-486">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="52a9b-487">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 属性の有無に関係なく、コンパイラでは、`Numbers.GetTenPrimes` メソッドによって返される配列が CLS に準拠していないことは検出されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-487">Despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="52a9b-488">すべての配列の要素が、CLS 準拠の型で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-488">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="52a9b-489">次の例では、CLS 非準拠の配列を返す 2 つのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-489">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="52a9b-490">最初のメソッドは、[UInt32](xref:System.UInt32) 値の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-490">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="52a9b-491">2 番目のメソッドは [Int32](xref:System.Int32) 値と `UInt32` 値を含む[Object](xref:System.Object) 配列を返します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-491">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="52a9b-492">最初の配列は `UInt32` 型であるため、コンパイラによって非準拠として識別されますが、2 番目の配列に CLS 非準拠の要素が含まれていることは認識されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-492">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="52a9b-493">配列パラメーターを持つメソッドのオーバーロードの解決は、配列であるという事実とその要素型に基づきます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-493">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="52a9b-494">したがって、次のオーバーロードされた `GetSquares` メソッドの定義は CLS に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-494">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="52a9b-495">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a9b-495">Interfaces</span></span>

<span data-ttu-id="52a9b-496">CLS 準拠のインターフェイスでは、プロパティ、イベント、および仮想メソッド (実装のないメソッド) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-496">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="52a9b-497">次の項目は、このインターフェイスには指定できません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-497">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="52a9b-498">静的メソッドまたは静的フィールド。</span><span class="sxs-lookup"><span data-stu-id="52a9b-498">Static methods or static fields.</span></span> <span data-ttu-id="52a9b-499">インターフェイスで静的メンバーを定義すると、C# コンパイラでコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-499">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="52a9b-500">フィールド。</span><span class="sxs-lookup"><span data-stu-id="52a9b-500">Fields.</span></span> <span data-ttu-id="52a9b-501">インターフェイスでフィールドを定義すると、C# コンパイラでコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-501">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="52a9b-502">CLS に準拠していないメソッド。</span><span class="sxs-lookup"><span data-stu-id="52a9b-502">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="52a9b-503">たとえば、次のインターフェイス定義には、CLS 非準拠とマークされているメソッド、`INumber.GetUnsigned` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-503">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="52a9b-504">この例では、コンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-504">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="52a9b-505">この規則のため、CLS に準拠している型は、CLS に準拠していないメンバーを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-505">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="52a9b-506">CLS 準拠のフレームワークによって、CLS に非準拠のインターフェイスを実装するクラスが公開されている場合、そのフレームワークには、CLS 非準拠のすべてのメンバーの具象実装も用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-506">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="52a9b-507">CLS 準拠の言語コンパイラでは、クラスによって、複数のインターフェイスにある同じ名前およびシグネチャを持つメンバーを個別に実装できるようにすることも必要です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-507">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="52a9b-508">C# は明示的なインターフェイス実装をサポートしており、同じ名前を持つメソッドを別々に実装できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-508">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="52a9b-509">次の例は、明示的なインターフェイス実装として `Temperature` インターフェイスおよび `ICelsius` インターフェイスを実装する `IFahrenheit` クラスを定義することで、このシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-509">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="52a9b-510">列挙</span><span class="sxs-lookup"><span data-stu-id="52a9b-510">Enumerations</span></span>

<span data-ttu-id="52a9b-511">CLS 準拠の列挙型は、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-511">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="52a9b-512">列挙体の基になる型は、組み込みの CLS 準拠の整数 ([Byte](xref:System.Byte)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、または [Int64](xref:System.Int64)) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-512">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="52a9b-513">たとえば、次のコードでは、基になる型が [UInt32](xref:System.UInt32) の列挙体を定義しようとしますが、コンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-513">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="52a9b-514">列挙型には、`Value__` 属性でマークされた `FieldAttributes.RTSpecialName` という名前の単一インスタンス フィールドが必要です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-514">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="52a9b-515">これにより、フィールド値を暗黙的に参照できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-515">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="52a9b-516">列挙体には、その列挙体自体の型と同じ型を持つリテラルな静的フィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-516">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="52a9b-517">たとえば、`State` および `State.On` の値を持つ `State.Off` 列挙体を定義すると、`State.On` と `State.Off` は両方ともリテラルな静的フィールドで、その型は `State` です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-517">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="52a9b-518">列挙体は 2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-518">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="52a9b-519">同時に指定できない一連の名前付き整数値を表す列挙体。</span><span class="sxs-lookup"><span data-stu-id="52a9b-519">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="52a9b-520">この列挙体の型は、[System.FlagsAttribute](xref:System.FlagsAttribute) カスタム属性が存在しないことによって示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-520">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="52a9b-521">名前のない値を生成するために結合できる一連のビット フラグを表す列挙体。</span><span class="sxs-lookup"><span data-stu-id="52a9b-521">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="52a9b-522">この列挙体の型は、 [System.FlagsAttribute](xref:System.FlagsAttribute) カスタム属性が存在することによって示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-522">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="52a9b-523">詳細については、[Enum](xref:System.Enum) 構造体のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-523">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="52a9b-524">列挙体の値は、その列挙体の指定された値に限定されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-524">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="52a9b-525">つまり、列挙体の値の範囲は、その列挙体の基になる値の範囲です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-525">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="52a9b-526">`Enum.IsDefined` メソッドを使用すると、指定された値が列挙体のメンバーかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-526">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="52a9b-527">一般的な型メンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-527">Type members in general</span></span>

<span data-ttu-id="52a9b-528">共通言語仕様では、すべてのフィールドとメソッドに、特定のクラスのメンバーとしてアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-528">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="52a9b-529">したがって、グローバルな静的フィールドおよび静的メソッド (つまり、型とは別に定義された静的フィールドまたは静的メソッド) は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-529">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="52a9b-530">グローバル フィールドまたはグローバル メソッドをソース コードに追加しようとすると、C# コンパイラでコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-530">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="52a9b-531">共通言語仕様では、標準のマネージド呼び出し規約のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-531">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="52a9b-532">アンマネージ呼び出し規約と、`varargs` キーワードでマークされた可変個引数リストを持つメソッドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-532">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="52a9b-533">標準のマネージド呼び出し規則と互換性がある可変個引数リストについては、[ParamArrayAttribute](xref:System.ParamArrayAttribute) 属性、または `params` キーワード (C# の場合)、`ParamArray` キーワード (Visual Basic の場合) などの個々の言語の実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-533">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="52a9b-534">メンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-534">Member accessibility</span></span>

<span data-ttu-id="52a9b-535">継承されたメンバーをオーバーライドしても、そのメンバーのアクセシビリティは変更できません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-535">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="52a9b-536">たとえば、基底クラスのパブリック メソッドは、派生クラスのプライベート メソッドではオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-536">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="52a9b-537">ただし例外が 1 つあります。あるアセンブリ内にある、別のアセンブリの型でオーバーライドされた `protected internal` メンバー (C# の場合) または `Protected Friend` メンバー (Visual Basic の場合) です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-537">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="52a9b-538">この場合、オーバーライドのアクセシビリティは `Protected` です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-538">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="52a9b-539">次の例は、[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 属性が `true` に設定されており、`Animal` の派生クラス `Person` が、`Species` プロパティのアクセシビリティをパブリックからプライベートに変更しようとするときに発生するエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-539">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="52a9b-540">アクセシビリティがパブリックに変更されると、コンパイルが正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-540">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="52a9b-541">メンバーにアクセスできる場合は必ず、そのメンバーのシグネチャの型にアクセスできなければなりません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-541">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="52a9b-542">たとえば、これは、パブリック メンバーには、型がプライベート、プロテクト、または内部のパラメーターを含められないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-542">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="52a9b-543">次の例は、`StringWrapper` クラス コンストラクターが、文字列値のラップ方法を決定する内部 `StringOperationType` 列挙値を公開した場合に発生するコンパイラ エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-543">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="52a9b-544">ジェネリック型とメンバー</span><span class="sxs-lookup"><span data-stu-id="52a9b-544">Generic types and members</span></span>

<span data-ttu-id="52a9b-545">入れ子になった型には、少なくともその外側の型と同じ数のジェネリック パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-545">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="52a9b-546">このジェネリック パラメーターは、外側の型のジェネリック パラメーターに位置によって対応します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-546">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="52a9b-547">ジェネリック型に新しいジェネリック パラメーターを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-547">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="52a9b-548">外側の型のジェネリック型パラメーターと、その入れ子になった型の関係は、個別の言語構文によって非表示になっていることがあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-548">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="52a9b-549">次の例では、入れ子になった 2 つのクラス、`Outer<T>` および `Inner1A` が、ジェネリック型 `Inner1B<U>` に含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-549">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="52a9b-550">各クラスが `Object.ToString` から継承した `ToString` メソッドへの呼び出しは、入れ子になった各クラスに、その外側のクラスの型パラメーターが含まれていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-550">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="52a9b-551">ジェネリック型の名前は、フォーム *name*'*n* でエンコードされます。ここで、*name* は型の名前、 *\`* は文字リテラル、*n* は型で宣言されたパラメーターの数、入れ子になったジェネリック型の場合は、新しく導入された型パラメーターの数です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-551">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="52a9b-552">ジェネリック型の名前のエンコーディングは、主に、リフレクションを使用してライブラリ内の CLS 準拠のジェネリック型にアクセスする開発者が使用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-552">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="52a9b-553">制約がジェネリック型に適用される場合は、制約として使用されるすべての型も CLS に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-553">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="52a9b-554">次の例では、CLS に準拠していない `BaseClass` という名前のクラスと、型パラメーターが `BaseCollection` から派生しなければならない `BaseClass` という名前のジェネリック クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-554">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="52a9b-555">ただし、`BaseClass` が CLS に準拠していないので、コンパイラによって警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-555">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="52a9b-556">ジェネリック型がジェネリック基本型から派生している場合、そのジェネリック型は、基本型に対する制約も必ず満たすように制約を再宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-556">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="52a9b-557">次の例では、任意の数値型を表すことができる `Number<T>` を定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-557">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="52a9b-558">また、浮動小数点値を表す `FloatingPoint<T>` クラスも定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-558">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="52a9b-559">ただし、ソース コードはコンパイルされません。`Number<T>` (T は値型) の制約は `FloatingPoint<T>` に適用されないからです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-559">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="52a9b-560">制約が `FloatingPoint<T>` クラスに追加されると、コンパイルが正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-560">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="52a9b-561">共通言語仕様では、入れ子になった型とプロテクト メンバーに対して従来のインスタンス化ごとのモデルが適用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-561">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="52a9b-562">オープン ジェネリック型では、フィールドまたはメンバーのシグネチャに、入れ子になったプロテクト ジェネリック型の特定のインスタンス化が含まれている場合、これらのフィールドやメンバーは公開できません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-562">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="52a9b-563">ジェネリックの基底クラスやインターフェイスについて特定のインスタンス化を拡張する非ジェネリック型では、フィールドまたはメンバーのシグネチャに、入れ子になったプロテクト ジェネリック型の別のインスタンス化が含まれている場合、これらのフィールドやメンバーは公開できません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-563">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="52a9b-564">次の例では、ジェネリック型 `C1<T>` およびプロテクト クラス `C1<T>.N` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-564">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="52a9b-565">`C1<T>` には、2 つのメソッド `M1` と `M2` があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-565">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="52a9b-566">ただし、`M1` は、`C1<int>.N` オブジェクトを `C1<T>` から返そうとするので、CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-566">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="52a9b-567">2 番目の `C2` クラスは、`C1<long>` から派生しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-567">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="52a9b-568">これには、`M3` と `M4` の 2 つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-568">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="52a9b-569">`M3`は、`C1<int>.N` オブジェクトを `C1<long>` のサブクラスから返そうとするので、CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-569">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="52a9b-570">言語コンパイラはさらに制限されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-570">Language compilers can be even more restrictive.</span></span> <span data-ttu-id="52a9b-571">この例では、Visual Basic で `M4` をコンパイルしようとするとエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-571">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="52a9b-572">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="52a9b-572">Constructors</span></span>

<span data-ttu-id="52a9b-573">CLS 準拠のクラスと構造体のコンストラクターは、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-573">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="52a9b-574">派生クラスのコンストラクターは、継承されたインスタンス データにアクセスする前に、基底クラスのインスタンス コンストラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-574">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="52a9b-575">これは、基底クラスのコンストラクターは派生クラスには継承されないからです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-575">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="52a9b-576">この規則は、直接継承をサポートしない構造体に適用されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-576">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="52a9b-577">次の例に示すように、コンパイラは、通常、CLS 準拠とは別にこの規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-577">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="52a9b-578">これにより、`Doctor` クラスから派生した `Person` クラスが作成されますが、`Doctor` クラスでは、継承されたインスタンス フィールドを初期化するための `Person` クラス コンストラクターは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-578">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="52a9b-579">オブジェクト作成以外の目的で、オブジェクト コンストラクターを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-579">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="52a9b-580">また、オブジェクトを 2 度初期化することもできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-580">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="52a9b-581">たとえば、これは `Object.MemberwiseClone` でコンストラクターを呼び出す必要はないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-581">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="52a9b-582">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a9b-582">Properties</span></span>

<span data-ttu-id="52a9b-583">CLS 準拠型のプロパティは、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-583">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="52a9b-584">プロパティには setter、getter、またはこの両方が必ず必要です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-584">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="52a9b-585">アセンブリでは、これらは特殊なメソッドとして実装されます。つまり、アセンブリのメタデータで `SpecialName` とマークされた個別のメソッドとして (getter は `get`\_*propertyname*、setter は `set`\_*propertyname* という名前で) 表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-585">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="52a9b-586">C# コンパイラでは、<xref:System.CLSCompliantAttribute> 属性を適用しなくても、この規則が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-586">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="52a9b-587">プロパティの型は、プロパティ get アクセス操作子、および set アクセス操作子の最後の引数の戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-587">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="52a9b-588">これらの型は CLS に準拠している必要があり、引数を参照によってプロパティに割り当てることはできません (つまり、マネージド ポインターにできません)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-588">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="52a9b-589">プロパティに get アクセス操作子と set アクセス操作子の両方がある場合は、両方が仮想、両方が静的、または両方がインスタンスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-589">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="52a9b-590">C# コンパイラは、プロパティ定義構文によって、この規則を自動的に適用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-590">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="52a9b-591">イベント</span><span class="sxs-lookup"><span data-stu-id="52a9b-591">Events</span></span>

<span data-ttu-id="52a9b-592">イベントは、名前と型によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-592">An event is defined by its name and its type.</span></span> <span data-ttu-id="52a9b-593">イベントの型は、イベントの表示に使用されるデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-593">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="52a9b-594">たとえば、`DbConnection.StateChange` イベントは `StateChangeEventHandler` 型です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-594">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="52a9b-595">イベント自体のほか、イベント名に基づく名前の 3 つのメソッドがイベントの実装を提供し、アセンブリのメタデータで `SpecialName` としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-595">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="52a9b-596">イベント ハンドラーを追加するメソッド (`add`_ *EventName*)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-596">A method for adding an event handler, named `add`_ *EventName*.</span></span> <span data-ttu-id="52a9b-597">たとえば、`DbConnection.StateChange` イベントのイベント サブスクリプション メソッドの名前は `add_StateChange` です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-597">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="52a9b-598">イベント ハンドラーを削除するメソッド (`remove`_ *EventName*)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-598">A method for removing an event handler, named `remove`_ *EventName*.</span></span> <span data-ttu-id="52a9b-599">たとえば、`DbConnection.StateChange` イベントの削除メソッドの名前は `remove_StateChange` です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-599">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="52a9b-600">イベントが発生したことを示すメソッド (`raise`\_*EventName*)。</span><span class="sxs-lookup"><span data-stu-id="52a9b-600">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9b-601">イベントに関する共通言語仕様の規則は、ほとんどが言語コンパイラによって実装され、コンポーネント開発者が意識せずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-601">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="52a9b-602">イベントの追加、削除、発生の各メソッドには同じアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="52a9b-602">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="52a9b-603">また、すべてが、静的メソッド、インスタンス メソッド、仮想メソッドのいずれかでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-603">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="52a9b-604">イベントを追加および削除するメソッドには、イベント デリゲート型の型を持つパラメーターが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-604">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="52a9b-605">追加メソッドおよび削除メソッドは両方とも存在するか、両方存在しないかのいずれかでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-605">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="52a9b-606">次の例では、2 つのポイントの気温の差がしきい値と等しいか、それを超えた場合に `Temperature` イベントを発生させる、`TemperatureChanged` という名前の CLS 準拠クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-606">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="52a9b-607">`Temperature` クラスは、イベント ハンドラーを選択的に実行できるように、`raise_TemperatureChanged` メソッドを明示的に定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-607">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="52a9b-608">Overloads</span><span class="sxs-lookup"><span data-stu-id="52a9b-608">Overloads</span></span>

<span data-ttu-id="52a9b-609">共通言語仕様では、次の要件がオーバーロード メンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-609">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="52a9b-610">メンバーは、パラメーターの数および型に基づいてオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-610">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="52a9b-611">オーバーロードを区別するときに、呼び出し規約、戻り値の型、メソッドまたはそのパラメーターに適用されているカスタム修飾子、およびパラメーターが値渡しか参照渡しかは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-611">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="52a9b-612">例については、「[名前付け規則](#naming-conventions)」で、名前がスコープ内で一意であることを要求する要件のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a9b-612">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="52a9b-613">プロパティおよびメソッドのみオーバーロードできる。</span><span class="sxs-lookup"><span data-stu-id="52a9b-613">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="52a9b-614">フィールドとイベントはオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-614">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="52a9b-615">ジェネリック メソッドは、ジェネリック パラメーターの数に基づいてオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-615">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9b-616">`op_Explicit` 演算子および `op_Implicit` 演算子にはこの規則が適用されず、戻り値は、オーバーロード解決のためのメソッド シグネチャの一部として見なされません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-616">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="52a9b-617">この 2 つの演算子は、そのパラメーターと戻り値の両方に基づいてオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-617">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="52a9b-618">例外</span><span class="sxs-lookup"><span data-stu-id="52a9b-618">Exceptions</span></span>

<span data-ttu-id="52a9b-619">例外オブジェクトは [System.Exception](xref:System.Exception)、または `System.Exception` の別の派生型から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-619">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="52a9b-620">次の例は、`ErrorClass` というカスタム クラスを例外処理に使用したときに発生するコンパイラ エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-620">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="52a9b-621">このエラーを修正するには、`ErrorClass` から継承するように `System.Exception` クラスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-621">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="52a9b-622">また、Message プロパティはオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-622">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="52a9b-623">次の例では、このエラーを修正して CLS 準拠の `ErrorClass` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-623">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="52a9b-624">属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-624">Attributes</span></span>

<span data-ttu-id="52a9b-625">.NET アセンブリでは、カスタム属性を格納し、アセンブリ、型、メンバー、メソッド パラメーターなどのプログラミング オブジェクトに関するメタデータを取得するため、カスタム属性に拡張可能機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-625">In .NET assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="52a9b-626">カスタム属性は [System.Attribute](xref:System.Attribute)、または `System.Attribute` の派生型から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-626">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="52a9b-627">規則に違反する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-627">The following example violates this rule.</span></span> <span data-ttu-id="52a9b-628">この例では、`NumericAttribute` から派生していない `System.Attribute` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-628">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="52a9b-629">コンパイラ エラーは、CLS 非準拠の属性が適用されるときにのみ発生します。クラスが定義されるときではありません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-629">A compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="52a9b-630">CLS 準拠の属性のコンストラクターまたはプロパティは、次の型のみを公開できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-630">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="52a9b-631">Boolean</span><span class="sxs-lookup"><span data-stu-id="52a9b-631">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="52a9b-632">Byte</span><span class="sxs-lookup"><span data-stu-id="52a9b-632">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="52a9b-633">Char</span><span class="sxs-lookup"><span data-stu-id="52a9b-633">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="52a9b-634">Double</span><span class="sxs-lookup"><span data-stu-id="52a9b-634">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="52a9b-635">Int16</span><span class="sxs-lookup"><span data-stu-id="52a9b-635">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="52a9b-636">Int32</span><span class="sxs-lookup"><span data-stu-id="52a9b-636">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="52a9b-637">Int64</span><span class="sxs-lookup"><span data-stu-id="52a9b-637">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="52a9b-638">Single</span><span class="sxs-lookup"><span data-stu-id="52a9b-638">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="52a9b-639">String</span><span class="sxs-lookup"><span data-stu-id="52a9b-639">String</span></span>](xref:System.String)

* [<span data-ttu-id="52a9b-640">Type</span><span class="sxs-lookup"><span data-stu-id="52a9b-640">Type</span></span>](xref:System.Type)

* <span data-ttu-id="52a9b-641">基になる型が `Byte`、`Int16`、`Int32`、または `Int64` である列挙体の型。</span><span class="sxs-lookup"><span data-stu-id="52a9b-641">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="52a9b-642">次の例では、[Attribute](xref:System.Attribute) から派生する `DescriptionAttribute` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-642">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="52a9b-643">クラス コンストラクターには型 `Descriptor` のパラメーターがあるので、クラスは CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-643">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="52a9b-644">C# コンパイラから警告が出力されますが、コンパイルは成功します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-644">The C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="52a9b-645">CLSCompliantAttribute 属性</span><span class="sxs-lookup"><span data-stu-id="52a9b-645">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="52a9b-646">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) 属性は、プログラム要素が共通言語仕様でコンパイルされているかどうかを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-646">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="52a9b-647">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` コンストラクターには、プログラム要素が CLS に準拠しているかどうかを示す 1 つの必須パラメーター、*isCompliant* が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-647">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="52a9b-648">コンパイル時に、CLS 準拠が前提とされる非準拠要素が検出され、警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-648">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="52a9b-649">非準拠として明示的に宣言された型またはメンバーに対しては、警告は出力されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-649">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="52a9b-650">コンポーネント開発者は、次の 2 とおりの目的で `CLSCompliantAttribute` 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-650">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="52a9b-651">コンポーネントによって公開されたパブリック インターフェイスの CLS 準拠部分と CLS 非準拠部分を定義する。</span><span class="sxs-lookup"><span data-stu-id="52a9b-651">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="52a9b-652">この属性を使用して特定のプログラム要素を CLS 準拠としてマークすると、.NET を対象とするすべてのツールおよび言語から、これらの要素に必ずアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-652">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target .NET.</span></span>

* <span data-ttu-id="52a9b-653">コンポーネント ライブラリのパブリック インターフェイスが CLS に準拠するプログラム要素のみを公開するように保証する。</span><span class="sxs-lookup"><span data-stu-id="52a9b-653">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="52a9b-654">要素が CLS 非準拠の場合は、通常、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-654">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="52a9b-655">言語コンパイラでは、`CLSCompliantAttribute` 属性が使用されているかどうかに関係なく、CLS 準拠の規則が適用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-655">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="52a9b-656">たとえば、インターフェイスに `*static` メンバーを定義すると CLS の規則に違反します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-656">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="52a9b-657">ただし、インターフェイスに `*static` メンバーを定義した場合、C# コンパイラはエラー メッセージを表示し、アプリのコンパイルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-657">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="52a9b-658">`CLSCompliantAttribute` 属性は、値 `AttributeTargets.All` が指定された [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) 属性でマークされます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-658">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="52a9b-659">この値を使用すると、`CLSCompliantAttribute` 属性を、アセンブリ、モジュール、型 (クラス、構造体、列挙体、インターフェイス、およびデリゲート)、型パラメーター (コンストラクター、メソッド、プロパティ、フィールド、およびイベント)、パラメーター、ジェネリック パラメーター、戻り値など、すべてのプログラム要素に適用できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-659">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="52a9b-660">ただし、実際は、アセンブリ、型、および型メンバーだけに属性を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-660">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="52a9b-661">そうしないと、属性は、コンパイラによってライブラリのパブリック インターフェイスで非準拠パラメーター、ジェネリック パラメーター、または戻り値が検出されたときに必ず無視され、コンパイラ警告が引き続き生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-661">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="52a9b-662">`CLSCompliantAttribute` 属性の値は、内包型プログラム要素によって継承されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-662">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="52a9b-663">たとえば、アセンブリが CLS 準拠としてマークされている場合は、その型も CLS に準拠します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-663">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="52a9b-664">型が CLS 準拠としてマークされている場合は、その入れ子になった型とメンバーも CLS に準拠します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-664">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="52a9b-665">継承された準拠状況を明示的にオーバーライドするには、`CLSCompliantAttribute` 属性を、格納されているプログラム要素に適用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-665">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="52a9b-666">たとえば、*isCompliant* 値が `false` に指定された `CLSCompliantAttribute` 属性を使用すると、準拠アセンブリで非準拠型を定義できます。また、*isCompliant* 値が `true` に指定された属性を使用すると、非準拠アセンブリで準拠型を定義できます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-666">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="52a9b-667">準拠型で非準拠メンバーを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-667">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="52a9b-668">ただし、非準拠型は準拠メンバーを持つことができないので、*isCompliant* 値が `true` に指定された属性では非準拠型から継承をオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-668">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="52a9b-669">コンポーネントを開発するときは必ず、`CLSCompliantAttribute` 属性を使用して、アセンブリ、その型、およびそのメンバーが CLS に準拠しているかどうかを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-669">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="52a9b-670">CLS 準拠のコンポーネントを作成するには:</span><span class="sxs-lookup"><span data-stu-id="52a9b-670">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="52a9b-671">`CLSCompliantAttribute` を使用して、CLS 準拠としてアセンブリをマークします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-671">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="52a9b-672">アセンブリ内の CLS に準拠していない公開された型を、非準拠としてマークします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-672">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="52a9b-673">CLS 準拠の型の公開されたメンバーを、非準拠としてマークします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-673">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="52a9b-674">CLS 非準拠メンバーの CLS 準拠の代替を指定します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-674">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="52a9b-675">非準拠の型とメンバーすべてを正常にマークした場合、非準拠の警告は出力されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-675">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="52a9b-676">ただし、どのメンバーが CLS に準拠していないかを提示し、CLS 準拠の代替を製品ドキュメントに示すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-676">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="52a9b-677">次の例では、`CLSCompliantAttribute` 属性を使用して、CLS 準拠のアセンブリと、2 つの CLS 非準拠のメンバーを持つ型、`CharacterUtilities` を定義します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-677">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="52a9b-678">両メンバーとも `CLSCompliant(false)` 属性でタグ付けされているので、警告は生成されません。</span><span class="sxs-lookup"><span data-stu-id="52a9b-678">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="52a9b-679">また、クラスには、両方のメソッド用の CLS 準拠の代替も用意されています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-679">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="52a9b-680">通常、CLS 準拠の代替を用意するには、2 つのオーバーロードを `ToUTF16` メソッドに追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="52a9b-680">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="52a9b-681">ただし、戻り値に基づいてメソッドをオーバーロードできないので、CLS 準拠のメソッドの名前は、非準拠のメソッドの名前とは異なります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-681">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="52a9b-682">ライブラリではなくアプリを開発している場合 (つまり、他のアプリ開発者が使用できる型またはメンバーを公開しない場合)、アプリが使用するプログラム要素は、そのプログラム要素が使用する言語でサポートされていない場合に CLS に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-682">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="52a9b-683">この場合、CLS 非準拠の要素を使用しようとすると、言語コンパイラによってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-683">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="52a9b-684">言語間の相互運用性</span><span class="sxs-lookup"><span data-stu-id="52a9b-684">Cross-language interoperability</span></span>

<span data-ttu-id="52a9b-685">言語に依存しないということは、いくつか意味があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-685">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="52a9b-686">1 つには、ある言語で記述された型を、別の言語で記述されたアプリからシームレスに使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-686">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="52a9b-687">また、この記事での焦点になりますが、複数の言語で記述されたコードを 1 つの .NET アセンブリにまとめることもできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-687">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET assembly.</span></span>

<span data-ttu-id="52a9b-688">次の例では、`NumericLib` および `StringLib` という 2 つのクラスを含む Utilities.dll という名前のクラス ライブラリを作成して言語間の相互運用性を示します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-688">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="52a9b-689">`NumericLib` クラスは C# で記述され、`StringLib` クラスは Visual Basic で記述されています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-689">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="52a9b-690">以下は `StringUtil.vb` のソース コードで、`StringLib` クラスに `ToTitleCase` という単一のメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-690">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="52a9b-691">以下は NumberUtil.cs のソース コードで、`NumericLib` および `IsEven` という 2 つのメンバーを持つ `NearZero` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="52a9b-691">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="52a9b-692">単一のアセンブリに 2 つのクラスをパッケージ化するには、モジュールにコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a9b-692">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="52a9b-693">Visual Basic のソース コード ファイルをモジュールにコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-693">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="52a9b-694">C# のソース コード ファイルをモジュールにコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-694">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="52a9b-695">次に、リンク ツール (Link.exe) を使用して 2 つのモジュールをアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="52a9b-695">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="52a9b-696">次の例では、その後 `NumericLib.NearZero` メソッドおよび `StringLib.ToTitleCase` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-696">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="52a9b-697">Visual Basic コードと C# コードのどちらでも、両方のクラスのメソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="52a9b-697">Both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="52a9b-698">Visual Basic コードをコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-698">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="52a9b-699">C# でコンパイルするには、コンパイラの名前を vbc から csc に変更し、ファイル拡張子を .vb から .cs に変更します。</span><span class="sxs-lookup"><span data-stu-id="52a9b-699">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
