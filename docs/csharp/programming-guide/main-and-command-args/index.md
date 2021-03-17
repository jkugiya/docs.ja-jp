---
title: Main() とコマンドライン引数 - C# プログラミング ガイド
description: Main() とコマンドライン引数について説明します。 ' Main ' メソッドは、実行可能プログラムのエントリポイントです。
ms.date: 03/08/2021
f1_keywords:
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 35117642f38885aab08a5c0249d1f65ec76c59f3
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190204"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="be55c-104">Main() とコマンドライン引数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="be55c-104">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="be55c-105">`Main` メソッドは、C# アプリケーションのエントリ ポイントです</span><span class="sxs-lookup"><span data-stu-id="be55c-105">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="be55c-106">(ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="be55c-106">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

<span data-ttu-id="be55c-107">C# プログラムのエントリ ポイントは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="be55c-107">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="be55c-108">`Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に `-main` コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be55c-108">If you have more than one class that has a `Main` method, you must compile your program with the `-main` compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="be55c-109">詳細については、「[-main (C# コンパイラ オプション)](../../language-reference/compiler-options/main-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be55c-109">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

<span data-ttu-id="be55c-110">C# 9 以降では、次の例のように `Main` メソッドを省略し、`Main` メソッド内にあるかのように C# ステートメントを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="be55c-110">Starting in C# 9, you can omit the `Main` method, and write C# statements as if they were in the `Main` method, as in the following example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

<span data-ttu-id="be55c-111">暗黙的なエントリ ポイント メソッドを使用してアプリケーション コードを記述する方法の詳細については、「[最上位レベルのステートメント](top-level-statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be55c-111">For information about how to write application code with an implicit entry point method, see [Top-level statements](top-level-statements.md).</span></span>

## <a name="overview"></a><span data-ttu-id="be55c-112">概要</span><span class="sxs-lookup"><span data-stu-id="be55c-112">Overview</span></span>

- <span data-ttu-id="be55c-113">`Main` メソッドは実行可能プログラムのエントリ ポイントであり、ここでプログラムの制御を開始および終了します。</span><span class="sxs-lookup"><span data-stu-id="be55c-113">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="be55c-114">`Main` は、クラスまたは構造体の内部で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="be55c-114">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="be55c-115">`Main` は [static](../../language-reference/keywords/static.md) である必要がありますが、[public](../../language-reference/keywords/public.md) である必要はありません</span><span class="sxs-lookup"><span data-stu-id="be55c-115">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="be55c-116">(先ほどの例では、既定の [private](../../language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="be55c-116">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="be55c-117">`Main` の戻り値の型は、`void` または `int` のいずれかになります。C# 7.1 以降では `Task` または `Task<int>` になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="be55c-117">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="be55c-118">`Main` で `Task` または `Task<int>` が返される場合に限り、`Main` の宣言に [`async`](../../language-reference/keywords/async.md) 修飾子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="be55c-118">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="be55c-119">この条件により、`async void Main` メソッドが明確に除外されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="be55c-119">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="be55c-120">`Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="be55c-120">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="be55c-121">Visual Studio を使用して Windows アプリケーションを作成する場合、このパラメーターを手動で追加するか <xref:System.Environment.GetCommandLineArgs> メソッドを使用して、[コマンドライン引数](command-line-arguments.md)を取得できます。</span><span class="sxs-lookup"><span data-stu-id="be55c-121">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="be55c-122">パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。</span><span class="sxs-lookup"><span data-stu-id="be55c-122">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="be55c-123">C や C++ とは異なり、プログラムの名前は、<xref:System.Environment.GetCommandLineArgs> の最初の要素です。`args` 配列の最初のコマンドライン引数として扱われることはありません。</span><span class="sxs-lookup"><span data-stu-id="be55c-123">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="be55c-124">有効な `Main` の署名の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be55c-124">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="be55c-125">前の例ではすべて、public アクセサー修飾子を使用しています。</span><span class="sxs-lookup"><span data-stu-id="be55c-125">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="be55c-126">これは一般的ですが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="be55c-126">That is typical, but not required.</span></span>

<span data-ttu-id="be55c-127">コンソール アプリケーションの `Main` で `await` を使用して非同期操作を開始する必要がある場合、戻り値の型 `async`、`Task`、`Task<int>` を追加することでプログラム コードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="be55c-127">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="be55c-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="be55c-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="be55c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="be55c-129">See also</span></span>

- [<span data-ttu-id="be55c-130">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="be55c-130">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="be55c-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="be55c-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="be55c-132">メソッド</span><span class="sxs-lookup"><span data-stu-id="be55c-132">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="be55c-133">インサイド C# プログラム</span><span class="sxs-lookup"><span data-stu-id="be55c-133">Inside a C# Program</span></span>](../inside-a-program/index.md)
