---
title: 非同期ストリームの生成と使用
description: この上級チュートリアルでは、非同期ストリームを生成し、使用する方法について説明します。 非同期ストリームでは、非同期で生成される可能性があるデータのシーケンスを自然な方法で処理できます。
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 4e2264e88b0df9fe8c4e1ebf9bd154dddb390e4e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497425"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a><span data-ttu-id="73fb2-104">チュートリアル: C#8.0 および .NET Core 3.0 を使用して非同期ストリームを生成および使用する</span><span class="sxs-lookup"><span data-stu-id="73fb2-104">Tutorial: Generate and consume async streams using C# 8.0 and .NET Core 3.0</span></span>

<span data-ttu-id="73fb2-105">C# 8.0 では、データのストリーミング元をモデル化する **非同期ストリーム** が導入されました。</span><span class="sxs-lookup"><span data-stu-id="73fb2-105">C# 8.0 introduces **async streams**, which model a streaming source of data.</span></span> <span data-ttu-id="73fb2-106">データ ストリームでは、多くの場合、要素を非同期で取得または生成します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-106">Data streams often retrieve or generate elements asynchronously.</span></span> <span data-ttu-id="73fb2-107">非同期ストリームは .NET Standard 2.1 で導入された新しいインターフェイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-107">Async streams rely on new interfaces introduced in .NET Standard 2.1.</span></span> <span data-ttu-id="73fb2-108">このインターフェイスは .NET Core 3.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="73fb2-108">These interfaces are supported in .NET Core 3.0 and later.</span></span> <span data-ttu-id="73fb2-109">非同期でストリーミングするデータ ソースにとって自然なプログラミング モデルが与えられます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-109">They provide a natural programming model for asynchronous streaming data sources.</span></span>

<span data-ttu-id="73fb2-110">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-110">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="73fb2-111">データ要素のシーケンスを非同期で生成するデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-111">Create a data source that generates a sequence of data elements asynchronously.</span></span>
> - <span data-ttu-id="73fb2-112">そのデータ ソースを非同期で使用します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-112">Consume that data source asynchronously.</span></span>
> - <span data-ttu-id="73fb2-113">非同期ストリームのキャンセルとキャプチャされたコンテキストをサポートします。</span><span class="sxs-lookup"><span data-stu-id="73fb2-113">Support cancellation and captured contexts for asynchronous streams.</span></span>
> - <span data-ttu-id="73fb2-114">新しいインターフェイスとデータ ソースが以前の同期データ シーケンスより優先される場合を認識します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-114">Recognize when the new interface and data source are preferred to earlier synchronous data sequences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73fb2-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="73fb2-115">Prerequisites</span></span>

<span data-ttu-id="73fb2-116">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。C# 8.0 コンパイラも実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="73fb2-116">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="73fb2-117">C# 8 コンパイラは [Visual Studio 2019 バージョン 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) または [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-117">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="73fb2-118">[GitHub アクセス トークン](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)を作成して、GitHub GraphQL エンドポイントにアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-118">You'll need to create a [GitHub access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) so that you can access the GitHub GraphQL endpoint.</span></span> <span data-ttu-id="73fb2-119">GitHub アクセス トークンに対して次のアクセス許可を選択します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-119">Select the following permissions for your GitHub Access Token:</span></span>

- <span data-ttu-id="73fb2-120">repo:status</span><span class="sxs-lookup"><span data-stu-id="73fb2-120">repo:status</span></span>
- <span data-ttu-id="73fb2-121">public_repo</span><span class="sxs-lookup"><span data-stu-id="73fb2-121">public_repo</span></span>

<span data-ttu-id="73fb2-122">アクセス トークンを安全な場所に保存して、GitHub API エンドポイントへのアクセス権を得るために使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="73fb2-122">Save the access token in a safe place so you can use it to gain access to the GitHub API endpoint.</span></span>

> [!WARNING]
> <span data-ttu-id="73fb2-123">自分の個人用アクセス トークンをセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-123">Keep your personal access token secure.</span></span> <span data-ttu-id="73fb2-124">個人用アクセス トークンを使用するソフトウェアでは、ユーザーのアクセス権を使用して GitHub API 呼び出しが行われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-124">Any software with your personal access token could make GitHub API calls using your access rights.</span></span>

<span data-ttu-id="73fb2-125">このチュートリアルでは、.NET と、C# と Visual Studio または .NET Core CLI のいずれかに精通していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="73fb2-125">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="run-the-starter-application"></a><span data-ttu-id="73fb2-126">初期アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="73fb2-126">Run the starter application</span></span>

<span data-ttu-id="73fb2-127">このチュートリアルで使用される初期アプリケーションのコードは、[csharp/whats-new/tutorials](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/start) フォルダー内の [dotnet/docs](https://github.com/dotnet/docs) リポジトリから取得できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-127">You can get the code for the starter application used in this tutorial from the [dotnet/docs](https://github.com/dotnet/docs) repository in the [csharp/whats-new/tutorials](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/start) folder.</span></span>

<span data-ttu-id="73fb2-128">初期アプリケーションは、[GitHub GraphQL](https://developer.github.com/v4/) インターフェイスを使用して、[dotnet/docs](https://github.com/dotnet/docs) リポジトリに書き込まれた最近の問題を取得するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="73fb2-128">The starter application is a console application that uses the [GitHub GraphQL](https://developer.github.com/v4/) interface to retrieve recent issues written in the [dotnet/docs](https://github.com/dotnet/docs) repository.</span></span> <span data-ttu-id="73fb2-129">まず、初期アプリの `Main` メソッドについて次のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-129">Start by looking at the following code for the starter app `Main` method:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

<span data-ttu-id="73fb2-130">`GitHubKey` 環境変数を自分の個人用アクセス トークンに設定するか、`GetEnvVariable` への呼び出しの最後の引数を自分の個人用アクセス トークンで置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-130">You can either set a `GitHubKey` environment variable to your personal access token, or you can replace the last argument in the call to `GetEnvVariable` with your personal access token.</span></span> <span data-ttu-id="73fb2-131">ソースを他人と共有する場合、自分のアクセス コードをソース コードに置かないでください。</span><span class="sxs-lookup"><span data-stu-id="73fb2-131">Don't put your access code in source code if you'll be sharing the source with others.</span></span> <span data-ttu-id="73fb2-132">共有ソース リポジトリにアクセス コードをアップロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="73fb2-132">Never upload access codes to a shared source repository.</span></span>

<span data-ttu-id="73fb2-133">GitHub クライアントの作成後に、`Main` 内のコードによって進行状況レポート オブジェクトとキャンセル トークンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-133">After creating the GitHub client, the code in `Main` creates a progress reporting object and a cancellation token.</span></span> <span data-ttu-id="73fb2-134">これらのオブジェクトが作成されると、`Main` によって `runPagedQueryAsync` が呼び出されて、作成された直近 250 件の問題が取得されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-134">Once those objects are created, `Main` calls `runPagedQueryAsync` to retrieve the most recent 250 created issues.</span></span> <span data-ttu-id="73fb2-135">そのタスクが完了すると、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-135">After that task has finished, the results are displayed.</span></span>

<span data-ttu-id="73fb2-136">初期アプリケーションを実行するときに、このアプリケーションの実行方法についていくつかの重要な観察を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-136">When you run the starter application, you can make some important observations about how this application runs.</span></span>  <span data-ttu-id="73fb2-137">GitHub から返される各ページについてレポートされる進行状況を確認します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-137">You'll see progress reported for each page returned from GitHub.</span></span> <span data-ttu-id="73fb2-138">問題の新しい各ページが GitHub から返される前に、注目すべき一時停止を観察できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-138">You can observe a noticeable pause before GitHub returns each new page of issues.</span></span> <span data-ttu-id="73fb2-139">最後に、問題は GitHub から 10 ページすべてが取得された後にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-139">Finally, the issues are displayed only after all 10 pages have been retrieved from GitHub.</span></span>

## <a name="examine-the-implementation"></a><span data-ttu-id="73fb2-140">実装を調べる</span><span class="sxs-lookup"><span data-stu-id="73fb2-140">Examine the implementation</span></span>

<span data-ttu-id="73fb2-141">実装では、前のセクションで説明した動作を観察した理由が明らかになります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-141">The implementation reveals why you observed the behavior discussed in the previous section.</span></span> <span data-ttu-id="73fb2-142">`runPagedQueryAsync` のコードを調べます:</span><span class="sxs-lookup"><span data-stu-id="73fb2-142">Examine the code for `runPagedQueryAsync`:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

<span data-ttu-id="73fb2-143">上記のコードのページング アルゴリズムと非同期構造体に注目してみましょう。</span><span class="sxs-lookup"><span data-stu-id="73fb2-143">Let's concentrate on the paging algorithm and async structure of the preceding code.</span></span> <span data-ttu-id="73fb2-144">(GitHub GraphQL API について詳しくは、[GitHub GraphQL のドキュメント](https://developer.github.com/v4/guides/)をご覧ください。)`runPagedQueryAsync` メソッドでは、問題が新しい順に列挙されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-144">(You can consult the [GitHub GraphQL documentation](https://developer.github.com/v4/guides/) for details on the GitHub GraphQL API.) The `runPagedQueryAsync` method enumerates the issues from most recent to oldest.</span></span> <span data-ttu-id="73fb2-145">1 ページあたり 25 件の問題を要求し、応答の `pageInfo` 構造体を調べて前のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-145">It requests 25 issues per page and examines the `pageInfo` structure of the response to continue with the previous page.</span></span> <span data-ttu-id="73fb2-146">次の GraphQL の標準的なページングでは、複数ページの応答がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-146">That follows GraphQL's standard paging support for multi-page responses.</span></span> <span data-ttu-id="73fb2-147">応答には、前のページを要求するために使用される `hasPreviousPages` 値と `startCursor` 値を含む `pageInfo` オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="73fb2-147">The response includes a `pageInfo` object that includes a `hasPreviousPages` value and a `startCursor` value used to request the previous page.</span></span> <span data-ttu-id="73fb2-148">問題は `nodes` 配列内にあります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-148">The issues are in the `nodes` array.</span></span> <span data-ttu-id="73fb2-149">`runPagedQueryAsync` メソッドでは、すべてのページからのすべての結果を格納する配列にこれらのノードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-149">The `runPagedQueryAsync` method appends these nodes to an array that contains all the results from all pages.</span></span>

<span data-ttu-id="73fb2-150">結果のページを取得し、復元した後、`runPagedQueryAsync` によって進行状況がレポートされ、キャンセルがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-150">After retrieving and restoring a page of results, `runPagedQueryAsync` reports progress and checks for cancellation.</span></span> <span data-ttu-id="73fb2-151">キャンセルが要求されている場合は、`runPagedQueryAsync` によって <xref:System.OperationCanceledException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-151">If cancellation has been requested, `runPagedQueryAsync` throws an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="73fb2-152">このコードには、改善できる要素がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-152">There are several elements in this code that can be improved.</span></span> <span data-ttu-id="73fb2-153">最も重要なものとして、`runPagedQueryAsync` では返されるすべての問題に記憶域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-153">Most importantly, `runPagedQueryAsync` must allocate storage for all the issues returned.</span></span> <span data-ttu-id="73fb2-154">未解決の問題をすべて取得するには、取得したすべての問題を格納するためにはるかに多くのメモリが必要になるので、このサンプルは 250 件の問題で停止します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-154">This sample stops at 250 issues because retrieving all open issues would require much more memory to store all the retrieved issues.</span></span> <span data-ttu-id="73fb2-155">進行状況レポートとキャンセルをサポートするためのプロトコルが原因で、アルゴリズムを初読で理解することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-155">The protocols for supporting progress reports and cancellation make the algorithm harder to understand on its first reading.</span></span> <span data-ttu-id="73fb2-156">関連する型や API の数が増えます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-156">More types and APIs are involved.</span></span> <span data-ttu-id="73fb2-157"><xref:System.Threading.CancellationTokenSource> とそれに関連付けられた <xref:System.Threading.CancellationToken> を通じた通信をトレースして、キャンセルが要求されている場所と、付与されている場所を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-157">You must trace the communications through the <xref:System.Threading.CancellationTokenSource> and its associated <xref:System.Threading.CancellationToken> to understand where cancellation is requested and where it's granted.</span></span>

## <a name="async-streams-provide-a-better-way"></a><span data-ttu-id="73fb2-158">非同期ストリームではより優れた方法が提供される</span><span class="sxs-lookup"><span data-stu-id="73fb2-158">Async streams provide a better way</span></span>

<span data-ttu-id="73fb2-159">非同期ストリームおよび関連付けられている言語サポートは、これらすべての問題に対処します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-159">Async streams and the associated language support address all those concerns.</span></span> <span data-ttu-id="73fb2-160">シーケンスを生成するコードでは、`yield return` を使用して、`async` 修飾子で宣言されたメソッド内で要素を返せるようになりました。</span><span class="sxs-lookup"><span data-stu-id="73fb2-160">The code that generates the sequence can now use `yield return` to return elements in a method that was declared with the `async` modifier.</span></span> <span data-ttu-id="73fb2-161">`foreach` ループを使用してシーケンスを使用する場合と同様に、`await foreach` ループを使用して非同期ストリームを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-161">You can consume an async stream using an `await foreach` loop just as you consume any sequence using a `foreach` loop.</span></span>

<span data-ttu-id="73fb2-162">これらの新しい言語機能は、.NET Standard 2.1 に追加され、.NET Core 3.0 で実装された 3 つの新しいインターフェイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-162">These new language features depend on three new interfaces added to .NET Standard 2.1 and implemented in .NET Core 3.0:</span></span>

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

<span data-ttu-id="73fb2-163">この 3 つのインターフェイスは、ほとんどの C# 開発者にとって見慣れたものです。</span><span class="sxs-lookup"><span data-stu-id="73fb2-163">These three interfaces should be familiar to most C# developers.</span></span> <span data-ttu-id="73fb2-164">これらは、同期版と同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-164">They behave in a manner similar to their synchronous counterparts:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

<span data-ttu-id="73fb2-165">見慣れない可能性のある 1 つの型は <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="73fb2-165">One type that may be unfamiliar is <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73fb2-166">`ValueTask` 構造体では、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスと同様の API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-166">The `ValueTask` struct provides a similar API to the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="73fb2-167">パフォーマンス上の理由から、これらのインターフェイスでは `ValueTask` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-167">`ValueTask` is used in these interfaces for performance reasons.</span></span>

## <a name="convert-to-async-streams"></a><span data-ttu-id="73fb2-168">非同期ストリームに変換する</span><span class="sxs-lookup"><span data-stu-id="73fb2-168">Convert to async streams</span></span>

<span data-ttu-id="73fb2-169">次に、`runPagedQueryAsync` メソッドを変換して非同期ストリームを生成します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-169">Next, convert the `runPagedQueryAsync` method to generate an async stream.</span></span> <span data-ttu-id="73fb2-170">まず、`IAsyncEnumerable<JToken>` を返すように `runPagedQueryAsync` のシグネチャを変更し、次のコードに示すように、パラメーター リストからキャンセル トークンと進行状況オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-170">First, change the signature of `runPagedQueryAsync` to return an `IAsyncEnumerable<JToken>`, and remove the cancellation token and progress objects from the parameter list as shown in the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

<span data-ttu-id="73fb2-171">次のコードに示すように、初期コードではページが取得されると各ページが処理されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-171">The starter code processes each page as the page is retrieved, as shown in the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

<span data-ttu-id="73fb2-172">この 3 行を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-172">Replace those three lines with the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

<span data-ttu-id="73fb2-173">このメソッドの前の方にある `finalResults` の宣言と、変更したループに続く `return` ステートメントを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-173">You can also remove the declaration of `finalResults` earlier in this method and the `return` statement that follows the loop you modified.</span></span>

<span data-ttu-id="73fb2-174">非同期ストリームを生成するための変更が完了しました。</span><span class="sxs-lookup"><span data-stu-id="73fb2-174">You've finished the changes to generate an async stream.</span></span> <span data-ttu-id="73fb2-175">完了したメソッドは次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-175">The finished method should resemble the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

<span data-ttu-id="73fb2-176">次に、コレクションを使用するコードを変更して、非同期ストリームを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="73fb2-176">Next, you change the code that consumes the collection to consume the async stream.</span></span> <span data-ttu-id="73fb2-177">`Main` 内で、問題のコレクションを処理する次のコードを探します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-177">Find the following code in `Main` that processes the collection of issues:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

<span data-ttu-id="73fb2-178">このコードを次の `await foreach` ループに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-178">Replace that code with the following `await foreach` loop:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

<span data-ttu-id="73fb2-179">新しいインターフェイス <xref:System.Collections.Generic.IAsyncEnumerator%601> は <xref:System.IAsyncDisposable> から派生します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-179">The new interface <xref:System.Collections.Generic.IAsyncEnumerator%601> derives from <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="73fb2-180">つまり、前のループは、ループの完了時、ストリームを非同期で破棄します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-180">That means the preceding loop will asynchronously dispose the stream when the loop finishes.</span></span> <span data-ttu-id="73fb2-181">ループは次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-181">You can imagine the loop looks like the following code:</span></span>

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

<span data-ttu-id="73fb2-182">既定では、ストリーム要素はキャプチャされたコンテキストで処理されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-182">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="73fb2-183">コンテキストのキャプチャを無効にする場合は、<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-183">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="73fb2-184">同期コンテキストについて、および現在のコンテキストのキャプチャについての詳細は、「[タスク ベースの非同期パターンの利用](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73fb2-184">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="73fb2-185">非同期ストリームでは、他の `async` メソッドと同じプロトコルを利用してキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-185">Async streams support cancellation using the same protocol as other `async` methods.</span></span> <span data-ttu-id="73fb2-186">キャンセルをサポートするよう、非同期反復子メソッドのシグネチャを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-186">You would modify the signature for the async iterator method as follows to support cancellation:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

<span data-ttu-id="73fb2-187"><xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> 属性によってコンパイラは <xref:System.Collections.Generic.IAsyncEnumerator%601> のコードを生成します。このコードは、`GetAsyncEnumerator` に渡されたトークンを非同期反復子の本文にその引数として表示します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-187">The <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> attribute causes the compiler to generate code for the <xref:System.Collections.Generic.IAsyncEnumerator%601> that makes the token passed to `GetAsyncEnumerator` visible to the body of the async iterator as that argument.</span></span> <span data-ttu-id="73fb2-188">`runQueryAsync` の中では、トークンの状態を調べたり、要求されたら、後続の処理をキャンセルしたりできます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-188">Inside `runQueryAsync`, you could examine the state of the token and cancel further work if requested.</span></span>

<span data-ttu-id="73fb2-189">キャンセル トークンを非同期ストリームに渡すには、別の拡張メソッド <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-189">You use another extension method, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>, to pass the cancellation token to the async stream.</span></span> <span data-ttu-id="73fb2-190">問題を列挙するループを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-190">You would modify the loop enumerating the issues as follows:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

<span data-ttu-id="73fb2-191">完了したチュートリアルのコードは、[csharp/whats-new/tutorials](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/finished) フォルダー内の [dotnet/docs](https://github.com/dotnet/docs) リポジトリから取得できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-191">You can get the code for the finished tutorial from the [dotnet/docs](https://github.com/dotnet/docs) repository in the [csharp/whats-new/tutorials](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/finished) folder.</span></span>

## <a name="run-the-finished-application"></a><span data-ttu-id="73fb2-192">完成したアプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="73fb2-192">Run the finished application</span></span>

<span data-ttu-id="73fb2-193">アプリケーションをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-193">Run the application again.</span></span> <span data-ttu-id="73fb2-194">その動作を初期アプリケーションの動作と比較します。</span><span class="sxs-lookup"><span data-stu-id="73fb2-194">Contrast its behavior with the behavior of the starter application.</span></span> <span data-ttu-id="73fb2-195">結果の最初のページは、使用可能になるとすぐに列挙されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-195">The first page of results is enumerated as soon as it's available.</span></span> <span data-ttu-id="73fb2-196">新しい各ページが要求され、取得されるときに観測可能な一時停止があり、次のページの結果がすぐに列挙されます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-196">There's an observable pause as each new page is requested and retrieved, then the next page's results are quickly enumerated.</span></span> <span data-ttu-id="73fb2-197">`try` / `catch` ブロックではキャンセルを処理する必要はありません。呼び出し元がコレクションの列挙を停止できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-197">The `try` / `catch` block isn't needed to handle cancellation: the caller can stop enumerating the collection.</span></span> <span data-ttu-id="73fb2-198">各ページがダウンロードされるときに非同期ストリームによって結果が生成されるので、進行状況が明確にレポートされます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-198">Progress is clearly reported because the async stream generates results as each page is downloaded.</span></span> <span data-ttu-id="73fb2-199">返される各問題の状態は、`await foreach` ループにシームレスに含まれます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-199">The status for each issue returned is seamlessly included in the `await foreach` loop.</span></span> <span data-ttu-id="73fb2-200">進行状況を追跡するためにコールバック オブジェクトは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="73fb2-200">You don't need a callback object to track progress.</span></span>

<span data-ttu-id="73fb2-201">コードを調べることで、メモリの改善を確認できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-201">You can see improvements in memory use by examining the code.</span></span> <span data-ttu-id="73fb2-202">すべての結果が列挙される前にそれらを格納するコレクションを割り当てる必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="73fb2-202">You no longer need to allocate a collection to store all the results before they're enumerated.</span></span> <span data-ttu-id="73fb2-203">呼び出し元では、結果を使用する方法、および記憶域のコレクションが必要かどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-203">The caller can determine how to consume the results and if a storage collection is needed.</span></span>

<span data-ttu-id="73fb2-204">初期アプリケーションと完成したアプリケーションの両方を実行し、実装間の違いを自分で確認できます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-204">Run both the starter and finished applications and you can observe the differences between the implementations for yourself.</span></span> <span data-ttu-id="73fb2-205">完了後に、このチュートリアルの開始時に作成した GitHub アクセス トークンを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-205">You can delete the GitHub access token you created when you started this tutorial after you've finished.</span></span> <span data-ttu-id="73fb2-206">攻撃者は、そのトークンへのアクセス権を獲得すると、ユーザーの資格情報を使用して GitHub API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="73fb2-206">If an attacker gained access to that token, they could access GitHub APIs using your credentials.</span></span>
