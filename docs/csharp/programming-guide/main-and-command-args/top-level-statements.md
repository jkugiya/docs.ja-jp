---
title: 最上位レベルのステートメント - C# プログラミング ガイド
description: C# 9 以降の最上位レベルのステートメントについて説明します。
ms.date: 03/08/2021
helpviewer_keywords:
- C# language, top-level statements
- C# language, Main method
ms.openlocfilehash: 31a9d3bba302823015058d59ca79da45754b761f
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881055"
---
# <a name="top-level-statements-c-programming-guide"></a><span data-ttu-id="7a2c7-103">最上位レベルのステートメント (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7a2c7-103">Top-level statements (C# Programming Guide)</span></span>

<span data-ttu-id="7a2c7-104">C# 9 以降は、コンソール アプリケーション プロジェクトに `Main` メソッドを明示的に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-104">Starting in C# 9, you don't have to explicitly include a `Main` method in a console application project.</span></span> <span data-ttu-id="7a2c7-105">代わりに、"*最上位レベルのステートメント*" 機能を使用し、記述しなければならないコードを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-105">Instead, you can use the *top-level statements* feature to minimize the code you have to write.</span></span> <span data-ttu-id="7a2c7-106">その場合、コンパイラによってアプリケーションに対し、クラスと `Main` メソッド エントリ ポイントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-106">In this case, the compiler generates a class and `Main` method entry point for the application.</span></span>

<span data-ttu-id="7a2c7-107">次の *Program.cs* ファイルは、C# 9 の完全な C# プログラムです。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-107">Here's a *Program.cs* file that is a complete C# program in C# 9:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

<span data-ttu-id="7a2c7-108">最上位レベルのステートメントでは、Azure Functions や GitHub Actions など、小さなユーティリティのために簡単なプログラムを記述できます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-108">Top-level statements let you write simple programs for small utilities such as Azure Functions and GitHub Actions.</span></span> <span data-ttu-id="7a2c7-109">また、C# プログラムを始めたばかりの方にとってコードを習い、書くことがもっと簡単になります。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-109">They also make it simpler for new C# programmers to get started learning and writing code.</span></span>

<span data-ttu-id="7a2c7-110">次のセクションでは、最上位レベルのステートメントでできることとできないことに関する規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-110">The following sections explain the rules on what you can and can't do with top-level statements.</span></span>

## <a name="only-one-top-level-file"></a><span data-ttu-id="7a2c7-111">最上位レベルのファイルは 1 つだけ</span><span class="sxs-lookup"><span data-stu-id="7a2c7-111">Only one top-level file</span></span>

<span data-ttu-id="7a2c7-112">アプリケーションにつき、エントリ ポイントは 1 つだけになります。そのため、プロジェクトには、最上位レベルのステートメントのファイルを 1 つだけ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-112">An application must have only one entry point, so a project can have only one file with top-level statements.</span></span> <span data-ttu-id="7a2c7-113">1 つのプロジェクトで複数のファイルに最上位レベルのステートメントを置くと、次のコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-113">Putting top-level statements in more than one file in a project results in the following compiler error:</span></span>

> <span data-ttu-id="7a2c7-114">CS8802 トップレベルのステートメントを持つことができるのは、1 つのコンパイル ユニットのみです。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-114">CS8802 Only one compilation unit can have top-level statements.</span></span>

<span data-ttu-id="7a2c7-115">1 つのプロジェクトには、最上位レベルのステートメントが含まれていない追加のソース コード ファイルをいくらでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-115">A project can have any number of additional source code files that don't have top-level statements.</span></span>

## <a name="no-other-entry-points"></a><span data-ttu-id="7a2c7-116">エントリ ポイントは他に用意しない</span><span class="sxs-lookup"><span data-stu-id="7a2c7-116">No other entry points</span></span>

<span data-ttu-id="7a2c7-117">`Main` メソッドは明示的に記述できますが、エントリ ポイントとして機能させることができません。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-117">You can write a `Main` method explicitly, but it can't function as an entry point.</span></span> <span data-ttu-id="7a2c7-118">コンパイラから次の警告が出ます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-118">The compiler issues the following warning:</span></span>

> <span data-ttu-id="7a2c7-119">CS7022 プログラムのエントリ ポイントは、グローバル コードです。エントリ ポイント 'Main()' を無視します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-119">CS7022 The entry point of the program is global code; ignoring 'Main()' entry point.</span></span>

<span data-ttu-id="7a2c7-120">最上位レベルのステートメントが含まれるプロジェクトでは、そのプロジェクトに `Main` メソッドが複数含まれる場合でも、[-main](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject) コンパイラ オプションを使用してエントリ ポイントを選択することができません。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-120">In a project with top-level statements, you can't use the [-main](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject) compiler option to select the entry point, even if the project has one or more `Main` methods.</span></span>

## <a name="using-directives"></a><span data-ttu-id="7a2c7-121">`using` ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="7a2c7-121">`using` directives</span></span>

<span data-ttu-id="7a2c7-122">using ディレクティブを含める場合、次の例のように、ファイルの先頭に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-122">If you include using directives, they must come first in the file, as in this example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

## <a name="global-namespace"></a><span data-ttu-id="7a2c7-123">グローバル名前空間</span><span class="sxs-lookup"><span data-stu-id="7a2c7-123">Global namespace</span></span>

<span data-ttu-id="7a2c7-124">最上位レベルのステートメントは暗黙的にグローバル名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-124">Top-level statements are implicitly in the global namespace.</span></span>

## <a name="namespaces-and-type-definitions"></a><span data-ttu-id="7a2c7-125">名前空間と型の定義</span><span class="sxs-lookup"><span data-stu-id="7a2c7-125">Namespaces and type definitions</span></span>

<span data-ttu-id="7a2c7-126">最上位レベルのステートメントが含まれるファイルには、名前空間と型の定義を含めることもできますが、最上位レベルのステートメントの後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-126">A file with top-level statements can also contain namespaces and type definitions, but they must come after the top-level statements.</span></span> <span data-ttu-id="7a2c7-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-127">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-2/Program.cs":::

## `args`

<span data-ttu-id="7a2c7-128">最上位レベルのステートメントでは、コマンドライン引数が入力された場合、`args` 変数を参照してそれにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-128">Top-level statements can reference the `args` variable to access any command-line arguments that were entered.</span></span> <span data-ttu-id="7a2c7-129">`args` 変数が null 値になることはありませんが、その `Length` は、コマンドライン引数が指定されなかった場合、ゼロになります。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-129">The `args` variable is never null but its `Length` is zero if no command-line arguments were provided.</span></span> <span data-ttu-id="7a2c7-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-130">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-3/Program.cs":::

## `await`

<span data-ttu-id="7a2c7-131">`await` を使用して非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-131">You can call an async method by using `await`.</span></span> <span data-ttu-id="7a2c7-132">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-132">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-4/Program.cs":::

## <a name="exit-code-for-the-process"></a><span data-ttu-id="7a2c7-133">プロセスの終了コード</span><span class="sxs-lookup"><span data-stu-id="7a2c7-133">Exit code for the process</span></span>

<span data-ttu-id="7a2c7-134">アプリケーションの終了時に `int` 値を返すには、`int` を返す `Main` メソッドの場合と同じように、`return` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-134">To return an `int` value when the application ends, use the `return` statement as you would in a `Main` method that returns an `int`.</span></span> <span data-ttu-id="7a2c7-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-135">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-5/Program.cs":::

## <a name="implicit-entry-point-method"></a><span data-ttu-id="7a2c7-136">暗黙的なエントリ ポイント メソッド</span><span class="sxs-lookup"><span data-stu-id="7a2c7-136">Implicit entry point method</span></span>

<span data-ttu-id="7a2c7-137">最上位レベルのステートメントが含まれるプロジェクトに対して、プログラムのエントリ ポイントとして機能するメソッドがコンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-137">The compiler generates a method to serve as the program entry point for a project with top-level statements.</span></span> <span data-ttu-id="7a2c7-138">このメソッドの名前は実際のところ `Main` ではありません。コードで直接参照できない実装の詳細です。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-138">The name of this method isn't actually `Main`, it's an implementation detail that your code can't reference directly.</span></span> <span data-ttu-id="7a2c7-139">メソッドのシグネチャは、最上位レベルのステートメントに `await` キーワードか `return` ステートメントが含まれるかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-139">The signature of the method depends on whether the top-level statements contain the `await` keyword or the `return` statement.</span></span> <span data-ttu-id="7a2c7-140">メソッド シグネチャがどのように表現されるかを次の表にまとめてあります。便宜上、表ではメソッド名に `Main` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-140">The following table shows what the method signature would look like, using the method name `Main` in the table for convenience.</span></span>

| <span data-ttu-id="7a2c7-141">最上位レベルのコードに含まれる</span><span class="sxs-lookup"><span data-stu-id="7a2c7-141">Top-level code contains</span></span>| <span data-ttu-id="7a2c7-142">暗黙的 `Main` シグネチャ</span><span class="sxs-lookup"><span data-stu-id="7a2c7-142">Implicit `Main` signature</span></span>                    |
|------------------------|----------------------------------------------|
| <span data-ttu-id="7a2c7-143">`await` および `return`</span><span class="sxs-lookup"><span data-stu-id="7a2c7-143">`await` and `return`</span></span>   | `static async Task<int> Main(string[] args)` |
| `await`                | `static async Task Main(string[] args)`      |
| `return`               | `static int Main(string[] args)`             |
| <span data-ttu-id="7a2c7-144">`await` も `return` もない</span><span class="sxs-lookup"><span data-stu-id="7a2c7-144">No `await` or `return`</span></span> | `static void Main(string[] args)`            |

## <a name="c-language-specification"></a><span data-ttu-id="7a2c7-145">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="7a2c7-145">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
[<span data-ttu-id="7a2c7-146">最上位レベルのステートメント</span><span class="sxs-lookup"><span data-stu-id="7a2c7-146">Top-level statements</span></span>](~/_csharplang/proposals/csharp-9.0/top-level-statements.md)

## <a name="see-also"></a><span data-ttu-id="7a2c7-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a2c7-147">See also</span></span>

- [<span data-ttu-id="7a2c7-148">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7a2c7-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7a2c7-149">メソッド</span><span class="sxs-lookup"><span data-stu-id="7a2c7-149">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="7a2c7-150">インサイド C# プログラム</span><span class="sxs-lookup"><span data-stu-id="7a2c7-150">Inside a C# Program</span></span>](../inside-a-program/index.md)
