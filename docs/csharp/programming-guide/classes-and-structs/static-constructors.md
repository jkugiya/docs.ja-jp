---
title: 静的コンストラクター - C# プログラミング ガイド
description: C# の静的コンストラクターは、静的データを初期化するか、または 1 回だけ実行されるアクションを実行します。 それは、最初のインスタンスが作成される前、または静的メンバーが参照される前に実行されます。
ms.date: 03/30/2021
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.openlocfilehash: f7ab97c3723c04b9d442daabb85f8d16967eb0e4
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123003"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="02df9-104">静的コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="02df9-104">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="02df9-105">静的コンストラクターは、任意の[静的](../../language-reference/keywords/static.md)データを初期化するため、または 1 回だけ実行する必要がある特定のアクションを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-105">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed only once.</span></span> <span data-ttu-id="02df9-106">最初のインスタンスが作成され前、または静的メンバーが参照される前に、自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-106">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[SimpleClass#1](snippets/static-constructors/Program.cs#1)]

## <a name="remarks"></a><span data-ttu-id="02df9-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="02df9-107">Remarks</span></span>

<span data-ttu-id="02df9-108">静的コンストラクターには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="02df9-108">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="02df9-109">静的コンストラクターにはアクセス修飾子が指定されず、パラメーターもありません。</span><span class="sxs-lookup"><span data-stu-id="02df9-109">A static constructor doesn't take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="02df9-110">クラスまたは構造体は、静的コンストラクターを 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="02df9-110">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="02df9-111">静的コンストラクターを継承またはオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="02df9-111">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="02df9-112">静的コンストラクターは、直接呼び出すことはできず、共通言語ランタイム (CLR) によって呼び出されることだけが意図されています。</span><span class="sxs-lookup"><span data-stu-id="02df9-112">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="02df9-113">自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-113">It is invoked automatically.</span></span>

- <span data-ttu-id="02df9-114">ユーザーは、プログラムで静的コンストラクターが実行されるタイミングを制御できません。</span><span class="sxs-lookup"><span data-stu-id="02df9-114">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="02df9-115">静的コンストラクターは自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-115">A static constructor is called automatically.</span></span> <span data-ttu-id="02df9-116">最初のインスタンスが作成され前、または任意の静的メンバーが参照される前に、それによって[クラス](../../language-reference/keywords/class.md)の初期化が行われます。</span><span class="sxs-lookup"><span data-stu-id="02df9-116">It initializes the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="02df9-117">静的コンストラクターは、インスタンス コンストラクターの前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-117">A static constructor runs before an instance constructor.</span></span> <span data-ttu-id="02df9-118">イベントまたはデリゲートに割り当てられている静的メソッドが呼び出されるときは型の静的コンストラクターが呼び出されますが、割り当てられるときは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="02df9-118">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="02df9-119">静的フィールド変数初期化子が静的コンストラクターのクラスに存在する場合、それらは、クラス宣言に出現するテキストの順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-119">If static field variable initializers are present in the class of the static constructor, they're executed in the textual order in which they appear in the class declaration.</span></span> <span data-ttu-id="02df9-120">初期化子は、静的コンストラクターの実行直前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-120">The initializers run immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="02df9-121">静的フィールドを初期化するための静的コンストラクターを指定しないと、すべての静的フィールドは、「[C# 型の既定値](../../language-reference/builtin-types/default-values.md)」で示されている既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-121">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="02df9-122">静的コンストラクターから例外がスローされた場合、ランタイムでそれが再度呼び出されることはなく、その型は、アプリケーション ドメインの有効期間中、初期化されないままになります。</span><span class="sxs-lookup"><span data-stu-id="02df9-122">If a static constructor throws an exception, the runtime doesn't invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain.</span></span> <span data-ttu-id="02df9-123">ほとんどの場合、静的コンストラクターで型をインスタンス化できないとき、または静的コンストラクター内でハンドルされない例外が発生したときは、<xref:System.TypeInitializationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="02df9-123">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="02df9-124">ソース コードで明示的に定義されていない静的コンストラクターでは、トラブルシューティングを行うときに中間言語 (IL) のコードを調べることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="02df9-124">For static constructors that aren't explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="02df9-125">静的コンストラクターが存在すると、<xref:System.Reflection.TypeAttributes.BeforeFieldInit> 型属性を追加できません。</span><span class="sxs-lookup"><span data-stu-id="02df9-125">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="02df9-126">これにより、ランタイムの最適化が制限されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-126">This limits runtime optimization.</span></span>

- <span data-ttu-id="02df9-127">`static readonly` として宣言されているフィールドは、その宣言の一部として、または静的コンストラクター内でのみ、割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="02df9-127">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="02df9-128">明示的な静的コンストラクターが必要ない場合は、ランタイムのより適切な最適化のため、静的コンストラクターではなく、宣言時に静的フィールドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="02df9-128">When an explicit static constructor isn't required, initialize static fields at declaration rather than through a static constructor for better runtime optimization.</span></span>

- <span data-ttu-id="02df9-129">静的コンストラクターは、ランタイムによって単一のアプリケーション ドメイン内で 1 回だけ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-129">The runtime calls a static constructor no more than once in a single application domain.</span></span> <span data-ttu-id="02df9-130">その呼び出しは、特定の型のクラスに基づいてロックされた領域で行われます。</span><span class="sxs-lookup"><span data-stu-id="02df9-130">That call is made in a locked region based on the specific type of the class.</span></span> <span data-ttu-id="02df9-131">静的コンストラクターの本体に、追加のロック メカニズムは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="02df9-131">No additional locking mechanisms are needed in the body of a static constructor.</span></span> <span data-ttu-id="02df9-132">デッドロックのリスクを回避するには、静的コンストラクターおよび初期化子内で現在のスレッドをブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="02df9-132">To avoid the risk of deadlocks, don't block the current thread in static constructors and initializers.</span></span> <span data-ttu-id="02df9-133">たとえば、タスク、スレッド、待機ハンドル、またはイベントを待機したり、ロックを取得したり、並列操作 (並列ループ、`Parallel.Invoke`、Parallel LINQ クエリなど) のブロックを実行したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="02df9-133">For example, don't wait on tasks, threads, wait handles or events, don't acquire locks, and don't execute blocking parallel operations such as parallel loops, `Parallel.Invoke` and Parallel LINQ queries.</span></span>

> [!Note]
> <span data-ttu-id="02df9-134">直接アクセスすることはできませんが、初期化の例外のトラブルシューティングを助けるため、明示的な静的コンストラクターが存在することを文書化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02df9-134">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="02df9-135">使用方法</span><span class="sxs-lookup"><span data-stu-id="02df9-135">Usage</span></span>

- <span data-ttu-id="02df9-136">静的コンストラクターの一般的な用途は、クラスがログ ファイルを使っていて、このファイルにエントリを書き込むためにコンストラクターが使われる場合です。</span><span class="sxs-lookup"><span data-stu-id="02df9-136">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="02df9-137">コンストラクターが `LoadLibrary` メソッドを呼び出すことができる場合は、アンマネージ コードのラッパー クラスを作成するときにも静的コンストラクターが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="02df9-137">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="02df9-138">静的コンストラクターは、型パラメーターの制約によりコンパイル時にチェックできない型パラメーターに対して、実行時にチェックを強制するのに適した場所でもあります。</span><span class="sxs-lookup"><span data-stu-id="02df9-138">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via type-parameter constraints.</span></span>

## <a name="example"></a><span data-ttu-id="02df9-139">例</span><span class="sxs-lookup"><span data-stu-id="02df9-139">Example</span></span>

 <span data-ttu-id="02df9-140">この例では、`Bus` クラスに静的コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="02df9-140">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="02df9-141">`Bus` の最初のインスタンスが作成されるとき (`bus1`)、静的コンストラクターが呼び出されてクラスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="02df9-141">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="02df9-142">サンプルの出力では、`Bus` のインスタンスが 2 つでも静的コンストラクターは 1 回だけ実行されること、およびインスタンス コンストラクターの実行前に静的コンストラクターが実行されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="02df9-142">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[BusSample#2](snippets/static-constructors/Program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="02df9-143">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="02df9-143">C# language specification</span></span>

<span data-ttu-id="02df9-144">詳しくは、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Static constructors (静的コンストラクター)](~/_csharplang/spec/classes.md#static-constructors)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="02df9-144">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="02df9-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="02df9-145">See also</span></span>

- [<span data-ttu-id="02df9-146">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="02df9-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="02df9-147">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="02df9-147">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="02df9-148">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="02df9-148">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="02df9-149">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="02df9-149">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="02df9-150">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="02df9-150">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="02df9-151">コンストラクターのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="02df9-151">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="02df9-152">セキュリティの警告 - CA2121: 静的コンストラクターはプライベートでなければなりません</span><span class="sxs-lookup"><span data-stu-id="02df9-152">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
