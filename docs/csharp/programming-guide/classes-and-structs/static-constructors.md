---
title: 静的コンストラクター - C# プログラミング ガイド
description: C# の静的コンストラクターは、静的データを初期化するか、最初のインスタンスが作成される前、または静的メンバーが参照される前に 1 回だけ実行されるアクションを実行します。
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: c224f96091e8fd5c51139757002ec8a67461a508
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898737"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="a46fe-103">静的コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a46fe-103">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="a46fe-104">静的コンストラクターは、任意の [static](../../language-reference/keywords/static.md) データを初期化するため、または 1 回だけ実行する必要がある特定のアクションを実行するために使います。</span><span class="sxs-lookup"><span data-stu-id="a46fe-104">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="a46fe-105">最初のインスタンスが作成され前、または静的メンバーが参照される前に、自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-105">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[SimpleClass#1](snippets/static-constructors/Program.cs#1)]

## <a name="remarks"></a><span data-ttu-id="a46fe-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="a46fe-106">Remarks</span></span>

<span data-ttu-id="a46fe-107">静的コンストラクターには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-107">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="a46fe-108">静的コンストラクターはアクセス修飾子を取らず、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-108">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="a46fe-109">クラスまたは構造体は、静的コンストラクターを 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-109">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="a46fe-110">静的コンストラクターを継承またはオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-110">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="a46fe-111">静的コンストラクターは、直接呼び出すことはできず、共通言語ランタイム (CLR) によって呼び出されることだけが意図されています。</span><span class="sxs-lookup"><span data-stu-id="a46fe-111">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="a46fe-112">自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-112">It is invoked automatically.</span></span>

- <span data-ttu-id="a46fe-113">ユーザーは、プログラムで静的コンストラクターが実行されるタイミングを制御できません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-113">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="a46fe-114">静的コンストラクターは、最初のインスタンスが作成され前、または静的メンバーが参照される前に、[クラス](../../language-reference/keywords/class.md)を初期化するために自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-114">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="a46fe-115">静的コンストラクターは、インスタンス コンストラクターの前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-115">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="a46fe-116">イベントまたはデリゲートに割り当てられている静的メソッドが呼び出されるときは型の静的コンストラクターが呼び出されますが、割り当てられるときは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-116">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="a46fe-117">静的フィールド変数初期化子が静的コンストラクターのクラスに存在する場合、初期化子は、静的コンストラクターの実行の直前に、クラス宣言に出現するテキストの順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-117">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="a46fe-118">静的フィールドを初期化するための静的コンストラクターを指定しないと、すべての静的フィールドは、「[C# 型の既定値](../../language-reference/builtin-types/default-values.md)」で示されている既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-118">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="a46fe-119">静的コンストラクターが例外をスローした場合、ランタイムがその静的コンストラクターを再度呼び出すことはなく、その型は、プログラムが実行しているアプリケーション ドメインの有効期間中、初期化されないままになります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-119">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="a46fe-120">ほとんどの場合、静的コンストラクターで型をインスタンス化できないとき、または静的コンストラクター内でハンドルされない例外が発生したときは、<xref:System.TypeInitializationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-120">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="a46fe-121">ソース コードで明示的に定義されていない暗黙的な静的コンストラクターでは、トラブルシューティングの際に中間言語 (IL) のコードを調べることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-121">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="a46fe-122">静的コンストラクターが存在すると、<xref:System.Reflection.TypeAttributes.BeforeFieldInit> 型属性を追加できません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-122">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="a46fe-123">これにより、ランタイムの最適化が制限されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-123">This limits runtime optimization.</span></span>

- <span data-ttu-id="a46fe-124">`static readonly` として宣言されているフィールドは、その宣言の一部として、または静的コンストラクター内でのみ、割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-124">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="a46fe-125">明示的な静的コンストラクターが必要ない場合は、ランタイムのより適切な最適化のため、静的コンストラクターではなく、宣言時に静的フィールドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a46fe-125">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="a46fe-126">直接アクセスすることはできませんが、初期化の例外のトラブルシューティングを助けるため、明示的な静的コンストラクターが存在することを文書化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-126">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="a46fe-127">使用方法</span><span class="sxs-lookup"><span data-stu-id="a46fe-127">Usage</span></span>

- <span data-ttu-id="a46fe-128">静的コンストラクターの一般的な用途は、クラスがログ ファイルを使っていて、このファイルにエントリを書き込むためにコンストラクターが使われる場合です。</span><span class="sxs-lookup"><span data-stu-id="a46fe-128">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="a46fe-129">コンストラクターが `LoadLibrary` メソッドを呼び出すことができる場合は、アンマネージ コードのラッパー クラスを作成するときにも静的コンストラクターが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-129">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="a46fe-130">静的コンストラクターは、制約 (型パラメーターの制約) によりコンパイル時にチェックできない型パラメーターに対して、実行時にチェックを強制するのに適した場所でもあります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-130">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="a46fe-131">例</span><span class="sxs-lookup"><span data-stu-id="a46fe-131">Example</span></span>

 <span data-ttu-id="a46fe-132">この例では、`Bus` クラスに静的コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-132">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="a46fe-133">`Bus` の最初のインスタンスが作成されるとき (`bus1`)、静的コンストラクターが呼び出されてクラスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a46fe-133">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="a46fe-134">サンプルの出力では、`Bus` のインスタンスが 2 つでも静的コンストラクターは 1 回だけ実行されること、およびインスタンス コンストラクターの実行前に静的コンストラクターが実行されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-134">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[BusSample#2](snippets/static-constructors/Program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a46fe-135">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a46fe-135">C# language specification</span></span>

<span data-ttu-id="a46fe-136">詳しくは、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Static constructors (静的コンストラクター)](~/_csharplang/spec/classes.md#static-constructors)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a46fe-136">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a46fe-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a46fe-137">See also</span></span>

- [<span data-ttu-id="a46fe-138">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a46fe-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a46fe-139">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="a46fe-139">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a46fe-140">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a46fe-140">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a46fe-141">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="a46fe-141">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="a46fe-142">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="a46fe-142">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="a46fe-143">コンストラクターのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a46fe-143">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="a46fe-144">セキュリティの警告 - CA2121: 静的コンストラクターはプライベートでなければなりません</span><span class="sxs-lookup"><span data-stu-id="a46fe-144">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
