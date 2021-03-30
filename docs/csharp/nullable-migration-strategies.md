---
title: null 許容参照型を使用するようにコードベースを更新する
description: null 許容参照型を使用するようにコードベースをアップグレードするための最適な方法を選択します。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: fff9ce4d053cc2543b0148d70435bdc793ecccd7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637161"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="e9013-103">null 許容参照型を使用するようにライブラリを更新し、null 許容規則を呼び出し元に伝える</span><span class="sxs-lookup"><span data-stu-id="e9013-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="e9013-104">[null 許容参照型](nullable-references.md)を追加するということは、すべての変数で `null` 値が許可または要求されるかどうかを宣言できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e9013-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="e9013-105">さらに、いくつかの属性 (`AllowNull`、`DisallowNull`、`MaybeNull`、`NotNull`、`NotNullWhen`、`MaybeNullWhen`、`NotNullIfNotNull`) を適用して、引数と戻り値の null 状態を完全に記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="e9013-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="e9013-106">それにより、コードを記述するときに優れたエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="e9013-107">null 非許容変数が `null` に設定される可能性がある場合は、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="e9013-108">null 許容変数が逆参照される前に null チェックが行われていない場合、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="e9013-109">ライブラリの更新には時間がかかることがありますが、メリットにはそれだけの価値があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="e9013-110">"*どのようなときに*" `null` 値が許可または禁止されるかについて、コンパイラに提供する情報が多いほど、より適切な警告が API のユーザーに示されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="e9013-111">よくある例から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="e9013-111">Let's start with a familiar example.</span></span> <span data-ttu-id="e9013-112">ライブラリに、リソース文字列を取得するための次の API があるとします。</span><span class="sxs-lookup"><span data-stu-id="e9013-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="e9013-113">前述の例では、.NET のよくある `Try*` パターンに従っています。</span><span class="sxs-lookup"><span data-stu-id="e9013-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="e9013-114">この API には、2 つの参照引数 (`key` および `message` パラメーター) があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="e9013-115">この API には、これらの引数の null 性に関連する次の規則があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="e9013-116">呼び出し元では、`key` の引数として `null` を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e9013-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="e9013-117">呼び出し元では、`message` の引数として、値が `null` の変数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e9013-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="e9013-118">`TryGetMessage` メソッドから `true` が返された場合、`message` の値は null ではありません。</span><span class="sxs-lookup"><span data-stu-id="e9013-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="e9013-119">戻り値が `false,` である場合、`message` (およびその null 状態) の値は null です。</span><span class="sxs-lookup"><span data-stu-id="e9013-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="e9013-120">`key` の規則は、変数型によって完全に表すことができます。`key` は null 非許容参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="e9013-121">`message` パラメーターはより複雑です。</span><span class="sxs-lookup"><span data-stu-id="e9013-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="e9013-122">引数として `null` が許可されますが、成功した場合、`out` 引数が null でないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="e9013-123">これらのシナリオでは、予測を記述するために、より豊富なボキャブラリが必要です。</span><span class="sxs-lookup"><span data-stu-id="e9013-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="e9013-124">null 許容参照用にライブラリを更新すると、一部の変数や型名に `?` を指定する以上のことが必要になります。</span><span class="sxs-lookup"><span data-stu-id="e9013-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="e9013-125">前の例では、API を調べて、各入力引数について想定されることを検討する必要があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="e9013-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="e9013-126">戻り値の保証と、メソッドから戻るときの `out` または `ref` 引数について検討します。</span><span class="sxs-lookup"><span data-stu-id="e9013-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="e9013-127">次に、それらの規則をコンパイラに通知します。呼び出し元がそれらの規則を守らないと、コンパイラによって警告が示されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="e9013-128">この作業には時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="e9013-128">This work takes time.</span></span> <span data-ttu-id="e9013-129">他の要件とバランスを取りながら、ライブラリまたはアプリケーションを null 許容対応にするための戦略から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="e9013-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements.</span></span> <span data-ttu-id="e9013-130">実行中の開発で null 許容参照型を有効にするときにバランスを取る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9013-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="e9013-131">ジェネリック型定義の課題について学習します。</span><span class="sxs-lookup"><span data-stu-id="e9013-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="e9013-132">属性を適用して、個々の API の事前条件と事後条件を記述する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="e9013-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="e9013-133">null 許容参照型に関する戦略を選択する</span><span class="sxs-lookup"><span data-stu-id="e9013-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="e9013-134">最初に選択することは、null 許容参照型を既定でオンまたはオフにするかどうかです。</span><span class="sxs-lookup"><span data-stu-id="e9013-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="e9013-135">次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-135">You have two strategies:</span></span>

- <span data-ttu-id="e9013-136">プロジェクト全体について null 許容参照型を有効にし、準備ができていないものをコードで無効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="e9013-137">null 許容参照型の注釈が付けられたコードについてのみ、null 許容参照型を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="e9013-138">最初の方法は、null 許容参照型対応に更新するときに、他の機能をライブラリに追加する場合に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e9013-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="e9013-139">すべての新規開発は null 許容対応です。</span><span class="sxs-lookup"><span data-stu-id="e9013-139">All new development is nullable aware.</span></span> <span data-ttu-id="e9013-140">既存のコードを更新するときに、それらのクラスで null 許容参照型を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="e9013-141">この最初の戦略に従う場合は、次の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="e9013-141">Following this first strategy, you do the following steps:</span></span>

1. <span data-ttu-id="e9013-142">*csproj* ファイルに `<Nullable>enable</Nullable>` 要素を追加することにより、プロジェクト全体で null 許容参照型を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="e9013-143">プロジェクト内のすべてのソース ファイルに `#nullable disable` プラグマを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9013-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="e9013-144">各ファイルの作業を行うときに、プラグマを削除し、警告が発生したら対処します。</span><span class="sxs-lookup"><span data-stu-id="e9013-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="e9013-145">この最初の戦略の場合、すべてのファイルにプラグマを追加するための事前作業が多くなります。</span><span class="sxs-lookup"><span data-stu-id="e9013-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="e9013-146">利点は、プロジェクトに追加されるすべての新しいコード ファイルで null 許容が有効になることです。</span><span class="sxs-lookup"><span data-stu-id="e9013-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="e9013-147">新しい作業はすべて null 許容対応になります。既存のコードのみを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="e9013-148">2 番目の戦略は、ライブラリが安定している場合に適しており、開発の主な目的は null 許容参照型を導入することになります。</span><span class="sxs-lookup"><span data-stu-id="e9013-148">The second strategy works better if the library is stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="e9013-149">API に注釈を付けるときに、null 許容参照型を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="e9013-150">終了した時点で、プロジェクト全体について null 許容参照型が有効になります。</span><span class="sxs-lookup"><span data-stu-id="e9013-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="e9013-151">この 2 番目の戦略に従う場合は、次の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="e9013-151">Following this second strategy you do the following steps:</span></span>

1. <span data-ttu-id="e9013-152">null 許容対応にするファイルに `#nullable enable` プラグマを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9013-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="e9013-153">すべての警告に対処します。</span><span class="sxs-lookup"><span data-stu-id="e9013-153">Address any warnings.</span></span>
1. <span data-ttu-id="e9013-154">ライブラリ全体を null 許容対応にするまで、これら最初の 2 つの手順を続けます。</span><span class="sxs-lookup"><span data-stu-id="e9013-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="e9013-155">*csproj* ファイルに `<Nullable>enable</Nullable>` 要素を追加することにより、プロジェクト全体で null 許容型を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="e9013-156">`#nullable enable` プラグマは不要になったため、削除します。</span><span class="sxs-lookup"><span data-stu-id="e9013-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="e9013-157">この 2 番目の戦略は、事前の作業が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="e9013-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="e9013-158">トレードオフは、新しいファイルを作成するときの最初のタスクが、プラグマを追加し、それを null 許容対応にすることであるということです。</span><span class="sxs-lookup"><span data-stu-id="e9013-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="e9013-159">チームの開発者がそれを忘れた場合、その新しいコードは、すべてのコードを null 許容対応にするという作業が発生します。</span><span class="sxs-lookup"><span data-stu-id="e9013-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="e9013-160">どちらの戦略を選択するかは、プロジェクトで行われているアクティブな開発の量によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e9013-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="e9013-161">プロジェクトが成熟して安定しているほど、2 番目の戦略がふさわしくなります。</span><span class="sxs-lookup"><span data-stu-id="e9013-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="e9013-162">開発中の機能が多いほど、最初の戦略が優れています。</span><span class="sxs-lookup"><span data-stu-id="e9013-162">The more features being developed, the better the first strategy.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9013-163">グローバルな Null 許容コンテキストは、生成されたコード ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="e9013-163">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="e9013-164">いずれの方法でも、Null 許容コンテキストは、生成済みとしてマークされているすべてのソース ファイルに対して "*無効になります*"。</span><span class="sxs-lookup"><span data-stu-id="e9013-164">Under either strategy, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="e9013-165">これは、生成されたファイル内のどの API にも注釈が付けられないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e9013-165">This means any APIs in generated files are not annotated.</span></span> <span data-ttu-id="e9013-166">ファイルが生成済みとしてマークされる方法は 4 つあります。</span><span class="sxs-lookup"><span data-stu-id="e9013-166">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="e9013-167">.editorconfig で、そのファイルに適用されるセクションで `generated_code = true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9013-167">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="e9013-168">ファイルの先頭にあるコメントに `<auto-generated>` または `<auto-generated/>` を配置します。</span><span class="sxs-lookup"><span data-stu-id="e9013-168">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="e9013-169">これは、コメント内の任意の行に配置できますが、コメント ブロックはファイル内の最初の要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-169">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="e9013-170">ファイル名を *TemporaryGeneratedFile_* で開始します</span><span class="sxs-lookup"><span data-stu-id="e9013-170">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="e9013-171">ファイル名の末尾を *.designer.cs*、 *.generated.cs*、 *.g.cs*、または *.g.i.cs* にします。</span><span class="sxs-lookup"><span data-stu-id="e9013-171">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="e9013-172">ジェネレーターは、[`#nullable`](language-reference/preprocessor-directives.md#nullable-context) プリプロセッサ ディレクティブを使用してオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="e9013-172">Generators can opt-in using the [`#nullable`](language-reference/preprocessor-directives.md#nullable-context) preprocessor directive.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="e9013-173">null 許容の警告によって破壊的変更が発生するか</span><span class="sxs-lookup"><span data-stu-id="e9013-173">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="e9013-174">null 許容参照型を有効にする前は、変数は "*null 許容が認識されていない*" ものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="e9013-174">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="e9013-175">null 許容参照型を有効にすると、そのような変数はすべて "*null 非許容*" になります。</span><span class="sxs-lookup"><span data-stu-id="e9013-175">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="e9013-176">そのような変数が null 以外の値に初期化されていない場合、コンパイラで警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="e9013-176">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="e9013-177">警告が発生する可能性があるもう 1 つの原因は戻り値で、値が初期化されていない場合です。</span><span class="sxs-lookup"><span data-stu-id="e9013-177">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="e9013-178">コンパイラの警告に対処するための最初の手順は、パラメーターと戻り値の型で `?` 注釈を使用して、引数または戻り値が null になる可能性があるときを示すことです。</span><span class="sxs-lookup"><span data-stu-id="e9013-178">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="e9013-179">参照変数が null であってはならないときは、元の宣言が正しくなります。</span><span class="sxs-lookup"><span data-stu-id="e9013-179">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="e9013-180">この作業を行うときの目標は、警告を修正することだけではありません。</span><span class="sxs-lookup"><span data-stu-id="e9013-180">As you do this task, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="e9013-181">より重要な目標は、null 値の可能性があるという意図をコンパイラに理解させることです。</span><span class="sxs-lookup"><span data-stu-id="e9013-181">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="e9013-182">警告を確認すると、ライブラリに関する次の重要な決定がわかります。</span><span class="sxs-lookup"><span data-stu-id="e9013-182">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="e9013-183">設計の意図をより明確に伝えるために、API のシグネチャの変更を検討しますか。</span><span class="sxs-lookup"><span data-stu-id="e9013-183">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="e9013-184">前に調べた `TryGetMessage` メソッドのより優れた API シグネチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e9013-184">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="e9013-185">戻り値は成功または失敗を示し、値が見つかった場合は値を保持します。</span><span class="sxs-lookup"><span data-stu-id="e9013-185">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="e9013-186">多くの場合、API のシグネチャを変更すると、null 値の伝達方法が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-186">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="e9013-187">ただし、パブリック ライブラリや、ユーザー ベースの大きいライブラリでは、API のシグネチャを変更しない方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-187">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="e9013-188">そのような場合や、他の一般的なパターンでは、属性を適用することで、引数または戻り値が `null` になる可能性がある場合をより明確に定義できます。</span><span class="sxs-lookup"><span data-stu-id="e9013-188">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="e9013-189">API のサーフェイスの変更を検討するかどうかにかかわらず、型の注釈だけでは、引数または戻り値での `null` 値を記述するのに十分ではないことがわかるでしょう。</span><span class="sxs-lookup"><span data-stu-id="e9013-189">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="e9013-190">そのような場合は、属性を適用することで API をより明確に記述できます。</span><span class="sxs-lookup"><span data-stu-id="e9013-190">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="e9013-191">属性で型の注釈を拡張する</span><span class="sxs-lookup"><span data-stu-id="e9013-191">Attributes extend type annotations</span></span>

<span data-ttu-id="e9013-192">変数の null 状態に関する追加情報を表すために、いくつかの属性が追加されました。</span><span class="sxs-lookup"><span data-stu-id="e9013-192">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="e9013-193">C# 8 で null 許容参照型型が導入される前に記述したすべてのコードでは、"*null が認識されません*" でした。</span><span class="sxs-lookup"><span data-stu-id="e9013-193">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="e9013-194">つまり、参照型変数は null である可能性がありますが、null チェックは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="e9013-194">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="e9013-195">コードが "*null 許容認識*" になると、それらの規則は変わります。</span><span class="sxs-lookup"><span data-stu-id="e9013-195">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="e9013-196">参照型を `null` 値にすることはできません。また、null 許容参照型は、逆参照される前に `null` に対してチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-196">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="e9013-197">API の規則は、`TryGetValue` API シナリオで見たとおり、より複雑になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-197">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="e9013-198">多くの API には、変数を `null` にできる場合やできない場合のより複雑な規則があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-198">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="e9013-199">このような場合は、属性を使用してそれらの規則を表します。</span><span class="sxs-lookup"><span data-stu-id="e9013-199">In these cases, you'll use attributes to express those rules.</span></span> <span data-ttu-id="e9013-200">API のセマンティクスを記述する属性については、[null 許容の分析に影響を与える属性](./language-reference/attributes/nullable-analysis.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9013-200">The attributes that describe the semantics of your API are found in the article on [Attributes that impact nullable analysis](./language-reference/attributes/nullable-analysis.md).</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="e9013-201">ジェネリック定義と null 値の許容</span><span class="sxs-lookup"><span data-stu-id="e9013-201">Generic definitions and nullability</span></span>

<span data-ttu-id="e9013-202">ジェネリック型とジェネリック メソッドの null 状態を正しく伝えるには、特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="e9013-202">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="e9013-203">特別な注意が必要になる原因は、null 許容値型と null 許容参照型が根本的に異なるという事実です。</span><span class="sxs-lookup"><span data-stu-id="e9013-203">The extra care stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="e9013-204">`int?` が `Nullable<int>` のシノニムであるのに対し、`string?` はコンパイラによって追加された属性を持つ `string` です。</span><span class="sxs-lookup"><span data-stu-id="e9013-204">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="e9013-205">結果として、`T` が `class` または `struct` のどちらであるかがわからないと、コンパイラで `T?` の正しいコードを生成できません。</span><span class="sxs-lookup"><span data-stu-id="e9013-205">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="e9013-206">これは、クローズ ジェネリック型の型引数として null 許容型 (値型または参照型) を使用できないという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="e9013-206">This fact doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="e9013-207">`List<string?>` と `List<int?>` はどちらも、`List<T>` の有効なインスタンス化です。</span><span class="sxs-lookup"><span data-stu-id="e9013-207">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="e9013-208">それが意味しているのは、制約なしにジェネリック クラスまたはメソッドの宣言で `T?` を使用することはできない、ということです。</span><span class="sxs-lookup"><span data-stu-id="e9013-208">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="e9013-209">たとえば、<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> は `T?` を返すように変更されません。</span><span class="sxs-lookup"><span data-stu-id="e9013-209">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="e9013-210">この制限を克服するには、`struct` または `class` のいずれかの制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9013-210">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="e9013-211">それらの制約のいずれかを指定すると、コンパイラで `T` と `T?` の両方のコードを生成する方法が認識されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-211">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="e9013-212">ジェネリック型引数に使用される型を、null 非許容型に制限することができます。</span><span class="sxs-lookup"><span data-stu-id="e9013-212">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="e9013-213">そのためには、その型引数に `notnull` 制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="e9013-213">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="e9013-214">その制約が適用されているときは、型引数を null 許容型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e9013-214">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a><span data-ttu-id="e9013-215">遅延初期化されるプロパティ、データ転送オブジェクト、および null 値の許容</span><span class="sxs-lookup"><span data-stu-id="e9013-215">Late-initialized properties, Data Transfer Objects, and nullability</span></span>

<span data-ttu-id="e9013-216">遅延初期化される (構築後に設定されるという意味です) プロパティの null 値の許容を示す場合、クラスで本来の設計意図が引き続き正しく表現されるよう、特別な配慮が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-216">Indicating the nullability of properties that are late-initialized, meaning set after construction, may require special consideration to ensure that your class continues to correctly express the original design intent.</span></span>

<span data-ttu-id="e9013-217">データ転送オブジェクト (DTO) など、遅延初期化されるプロパティを含む型は、多くの場合、データベース ORM (Object Relational Mapper) のような外部ライブラリ、逆シリアライザー、または別のソースから自動的にプロパティを設定するその他のコンポーネントによってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-217">Types that contain late-initialized properties, such as Data Transfer Objects (DTOs), are often instantiated by an external library, like a database ORM (Object Relational Mapper), a deserializer, or some other component that automatically populates properties from another source.</span></span>

<span data-ttu-id="e9013-218">null 許容参照型を有効にする前に、ある学生を表す次の DTO クラスについて考えてください。</span><span class="sxs-lookup"><span data-stu-id="e9013-218">Consider the following DTO class, prior to enabling nullable reference types, that represents a student:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

<span data-ttu-id="e9013-219">設計の意図 (この例では `Required` 属性によって示されます) として、このシステムでは、`FirstName` および `LastName` プロパティは **必須** であり、したがって null ではないことが示されています。</span><span class="sxs-lookup"><span data-stu-id="e9013-219">The design intent (indicated in this case by the `Required` attribute) suggests that in this system, the `FirstName` and `LastName` properties are **mandatory**, and therefore not null.</span></span>

<span data-ttu-id="e9013-220">`VehicleRegistration` プロパティは **必須ではない** ため、null にできます。</span><span class="sxs-lookup"><span data-stu-id="e9013-220">The `VehicleRegistration` property is **not mandatory**, so may be null.</span></span>

<span data-ttu-id="e9013-221">null 許容参照型を有効にするときは、本来の意図と一致するように、null 許容にできる DTO のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="e9013-221">When you enable nullable reference types, you want to indicate which properties on your DTO may be nullable, consistent with your original intent:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="e9013-222">この DTO の場合、null にできる唯一のプロパティは ``VehicleRegistration`` です。</span><span class="sxs-lookup"><span data-stu-id="e9013-222">For this DTO, the only property that may be null is ``VehicleRegistration``.</span></span>

<span data-ttu-id="e9013-223">ただし、`FirstName` と `LastName` の両方に対しては、null 非許容のプロパティが初期化されていないことを示す警告 `CS8618` がコンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="e9013-223">However, the compiler raises `CS8618` warnings for both `FirstName` and `LastName`, indicating the non-nullable properties are uninitialized.</span></span>

<span data-ttu-id="e9013-224">元の意図が維持されるような方法でコンパイラの警告を解決するために使用できるオプションが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="e9013-224">There are three options available to you that resolve the compiler warnings in a way that maintains the original intent.</span></span> <span data-ttu-id="e9013-225">これらのオプションはいずれも有効です。コーディング スタイルと設計要件に最も適したものを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-225">Any of these options are valid; you should choose the one that best suits your coding style and design requirements.</span></span>

### <a name="initialize-in-the-constructor"></a><span data-ttu-id="e9013-226">コンストラクター内で初期化する</span><span class="sxs-lookup"><span data-stu-id="e9013-226">Initialize in the constructor</span></span>

<span data-ttu-id="e9013-227">初期化されていないという警告を解決するための最善の方法は、プロパティをコンストラクター内で初期化することです。</span><span class="sxs-lookup"><span data-stu-id="e9013-227">The ideal way to resolve the uninitialized warnings is to initialize the properties in the constructor:</span></span>

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="e9013-228">この方法は、クラスのインスタンスを作成するために使用するライブラリで、コンストラクターにパラメーターを渡すことがサポートされている場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="e9013-228">This approach only works if the library that you use to instantiate the class supports passing parameters in the constructor.</span></span>

<span data-ttu-id="e9013-229">ライブラリでコンストラクターに全部のプロパティではなく "*一部*" だけを渡すことがサポートされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-229">A library may support passing *some* properties in the constructor, but not all.</span></span> <span data-ttu-id="e9013-230">たとえば、EF Core では、通常の列プロパティについての[コンストラクター バインド](/ef/core/modeling/constructors)はサポートされていますが、ナビゲーション プロパティについてはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e9013-230">For example, EF Core supports [constructor binding](/ef/core/modeling/constructors) for normal column properties, but not navigation properties.</span></span>

<span data-ttu-id="e9013-231">クラスのインスタンスを作成するライブラリのドキュメントを調べて、コンストラクター バインドがサポートされている範囲を理解してください。</span><span class="sxs-lookup"><span data-stu-id="e9013-231">Check the documentation on the library that instantiates your class, to understand the extent to which it supports constructor binding.</span></span>

### <a name="property-with-nullable-backing-field"></a><span data-ttu-id="e9013-232">null 許容バッキング フィールドを持つプロパティ</span><span class="sxs-lookup"><span data-stu-id="e9013-232">Property with nullable backing field</span></span>

<span data-ttu-id="e9013-233">コンストラクター バインドが機能しない場合、この問題に対処する方法の 1 つは、null 許容バッキング フィールドを持つ null 非許容プロパティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="e9013-233">If constructor binding won't work for you, one way to deal with this problem is to have a non-nullable property with a nullable backing field:</span></span>

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

<span data-ttu-id="e9013-234">このシナリオでは、初期化される前の `FirstName` プロパティにアクセスすると、API コントラクトが正しく使用されていないため、コードで `InvalidOperationException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e9013-234">In this scenario, if the `FirstName` property is accessed before it has been initialized, then the code throws an `InvalidOperationException`, because the API contract has been used incorrectly.</span></span>

<span data-ttu-id="e9013-235">バッキング フィールドを使用するときは、一部のライブラリに特別な考慮事項があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e9013-235">Consider that some libraries may have special considerations when using backing fields.</span></span> <span data-ttu-id="e9013-236">たとえば、EF Core は[バッキング フィールド](/ef/core/modeling/backing-field)を正しく使用するように構成することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9013-236">For example, EF Core may need to be configured to use [backing fields](/ef/core/modeling/backing-field) correctly.</span></span>

### <a name="initialize-the-property-to-null"></a><span data-ttu-id="e9013-237">プロパティを null に初期化する</span><span class="sxs-lookup"><span data-stu-id="e9013-237">Initialize the property to null</span></span>

<span data-ttu-id="e9013-238">null 許容バッキング フィールドの使用に代わるさらに簡潔な方法として、またはクラスのインスタンスを作成するライブラリがその方法と互換性を持たない場合は、null 免除演算子 (`!`) を使用して、プロパティを `null` に直接初期化できます。</span><span class="sxs-lookup"><span data-stu-id="e9013-238">As a terser alternative to using a nullable backing field, or if the library that instantiates your class isn't compatible with that approach, you can initialize the property to `null` directly, with the help of the null-forgiving operator (`!`):</span></span>

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

<span data-ttu-id="e9013-239">適切に初期化される前にプロパティにアクセスするプログラミングのバグの結果の場合を除き、実行時に実際の null 値が観察されることはありません。</span><span class="sxs-lookup"><span data-stu-id="e9013-239">You'll never observe an actual null value at runtime except as a result of a programming bug, by accessing the property before it has been properly initialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9013-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9013-240">See also</span></span>

- [<span data-ttu-id="e9013-241">既存のコードベースを null 許容参照に移行する</span><span class="sxs-lookup"><span data-stu-id="e9013-241">Migrate an existing codebase to nullable references</span></span>](whats-new/tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="e9013-242">EF Core での null 許容参照型の使用</span><span class="sxs-lookup"><span data-stu-id="e9013-242">Working with Nullable Reference Types in EF Core</span></span>](/ef/core/miscellaneous/nullable-reference-types)
