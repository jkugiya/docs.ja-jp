---
title: F# を使用した Azure Queue Storage の概要
description: Azure Queue は、アプリケーション コンポーネント間の信頼性の高い非同期メッセージングを提供します。 クラウド メッセージングにより、アプリケーション コンポーネントのスケールを個別に変更できます。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 0ab131647e37985d45073966ffc01b9a7f379e2f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899296"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="40255-104">F\# を使用した Azure Queue Storage の概要</span><span class="sxs-lookup"><span data-stu-id="40255-104">Get started with Azure Queue Storage using F\#</span></span>

<span data-ttu-id="40255-105">Azure Queue Storage を使用すると、アプリケーション コンポーネント間のクラウド メッセージングが提供されます。</span><span class="sxs-lookup"><span data-stu-id="40255-105">Azure Queue Storage provides cloud messaging between application components.</span></span> <span data-ttu-id="40255-106">拡張性を重視してアプリケーションを設計する場合、通常、アプリケーション コンポーネントを個別に拡張できるように分離します。</span><span class="sxs-lookup"><span data-stu-id="40255-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="40255-107">Queue Storage は、アプリケーション コンポーネントがクラウド、デスクトップ、オンプレミスのサーバー、モバイル デバイスのいずれで実行されている場合でも、アプリケーション コンポーネント間の通信に非同期メッセージングを提供します。</span><span class="sxs-lookup"><span data-stu-id="40255-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="40255-108">Queue Storage ではまた、非同期タスクの管理とプロセス ワークフローの構築もサポートします。</span><span class="sxs-lookup"><span data-stu-id="40255-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="40255-109">このチュートリアルについて</span><span class="sxs-lookup"><span data-stu-id="40255-109">About this tutorial</span></span>

<span data-ttu-id="40255-110">このチュートリアルでは、Azure Queue Storage を使用していくつかの一般的なタスクを実行するための F# コードを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="40255-110">This tutorial shows how to write F# code for some common tasks using Azure Queue Storage.</span></span> <span data-ttu-id="40255-111">紹介するタスクは、キューの作成と削除、キュー メッセージの追加、読み取り、削除です。</span><span class="sxs-lookup"><span data-stu-id="40255-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="40255-112">キュー ストレージの概念の概要については、[キュー ストレージの .NET ガイド](/azure/storage/storage-dotnet-how-to-use-queues)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40255-112">For a conceptual overview of queue storage, see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40255-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="40255-113">Prerequisites</span></span>

<span data-ttu-id="40255-114">このガイドを使用するには、まず [Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)必要があります。</span><span class="sxs-lookup"><span data-stu-id="40255-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="40255-115">また、このアカウントのストレージ アクセス キーも必要になります。</span><span class="sxs-lookup"><span data-stu-id="40255-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="40255-116">F# スクリプトを作成して F# インタラクティブを開始する</span><span class="sxs-lookup"><span data-stu-id="40255-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="40255-117">この記事のサンプルは、F# アプリケーションまたは F# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="40255-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="40255-118">F# スクリプトを作成するには、`.fsx` 拡張子のファイルを作成します。たとえば、F# 開発環境では `queues.fsx` です。</span><span class="sxs-lookup"><span data-stu-id="40255-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="40255-119">次に、[Paket](https://fsprojects.github.io/Paket/)や [NuGet](https://www.nuget.org/) などの[パッケージ マネージャー](package-management.md)を使用し、`#r` ディレクティブを使用して `WindowsAzure.Storage` パッケージと参照 `WindowsAzure.Storage.dll` をスクリプトにインストールします。</span><span class="sxs-lookup"><span data-stu-id="40255-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="40255-120">名前空間宣言の追加</span><span class="sxs-lookup"><span data-stu-id="40255-120">Add namespace declarations</span></span>

<span data-ttu-id="40255-121">次の `open` ステートメントを `queues.fsx` ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="40255-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="40255-122">接続文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="40255-122">Get your connection string</span></span>

<span data-ttu-id="40255-123">このチュートリアルでは、Azure Storage 接続文字列が必要になります。</span><span class="sxs-lookup"><span data-stu-id="40255-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="40255-124">接続文字列の詳細については、[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40255-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="40255-125">このチュートリアルでは、次のようにスクリプトに接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="40255-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="40255-126">ただし、これは実際のプロジェクトでは **お勧めしません**。</span><span class="sxs-lookup"><span data-stu-id="40255-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="40255-127">ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="40255-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="40255-128">ストレージ アカウント キーは常に慎重に保護してください。</span><span class="sxs-lookup"><span data-stu-id="40255-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="40255-129">このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="40255-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="40255-130">キーがセキュリティ侵害されたと思われる場合は、Azure portal を使用してキーを再生成できます。</span><span class="sxs-lookup"><span data-stu-id="40255-130">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="40255-131">実際のアプリケーションでは、ストレージ接続文字列を維持する最適な場所は構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="40255-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="40255-132">構成ファイルから接続文字列をフェッチするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="40255-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="40255-133">Azure Configuration Manager の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="40255-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="40255-134">また、.NET Framework の `ConfigurationManager` 型などの API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="40255-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="40255-135">接続文字列を解析する</span><span class="sxs-lookup"><span data-stu-id="40255-135">Parse the connection string</span></span>

<span data-ttu-id="40255-136">接続文字列を解析するには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="40255-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="40255-137">これによって、`CloudStorageAccount` が返されます。</span><span class="sxs-lookup"><span data-stu-id="40255-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="40255-138">Queue サービス クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="40255-138">Create the Queue service client</span></span>

<span data-ttu-id="40255-139">`CloudQueueClient` クラスを使用すると、Queue Storage に格納されているキューを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40255-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="40255-140">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="40255-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="40255-141">これで、Queue Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="40255-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="40255-142">キューを作成する</span><span class="sxs-lookup"><span data-stu-id="40255-142">Create a queue</span></span>

<span data-ttu-id="40255-143">この例では、まだキューがない場合にこれを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="40255-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="40255-144">メッセージをキューに挿入する</span><span class="sxs-lookup"><span data-stu-id="40255-144">Insert a message into a queue</span></span>

<span data-ttu-id="40255-145">既存のキューにメッセージを挿入するには、最初に新しい `CloudQueueMessage` を作成します。</span><span class="sxs-lookup"><span data-stu-id="40255-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="40255-146">次に、`AddMessage` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40255-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="40255-147">`CloudQueueMessage` は、次のように文字列 (UTF-8 形式) または `byte` 配列から作成できます。</span><span class="sxs-lookup"><span data-stu-id="40255-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="40255-148">次のメッセージをピークする</span><span class="sxs-lookup"><span data-stu-id="40255-148">Peek at the next message</span></span>

<span data-ttu-id="40255-149">`PeekMessage` メソッドを呼び出すと、キューの先頭にあるメッセージを、キューから削除せずにピークできます。</span><span class="sxs-lookup"><span data-stu-id="40255-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="40255-150">処理する次のメッセージを取得する</span><span class="sxs-lookup"><span data-stu-id="40255-150">Get the next message for processing</span></span>

<span data-ttu-id="40255-151">キューの先頭にあるメッセージを取得して処理するには、`GetMessage` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40255-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="40255-152">後で、`DeleteMessage` を使用してメッセージの処理が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="40255-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="40255-153">キューに配置されたメッセージの内容を変更する</span><span class="sxs-lookup"><span data-stu-id="40255-153">Change the contents of a queued message</span></span>

<span data-ttu-id="40255-154">キュー内の取得したメッセージの内容をインプレースで変更できます。</span><span class="sxs-lookup"><span data-stu-id="40255-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="40255-155">メッセージが作業タスクを表している場合は、この機能を使用して、作業タスクの状態を更新できます。</span><span class="sxs-lookup"><span data-stu-id="40255-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="40255-156">次のコードでは、キュー メッセージを新しい内容に更新し、表示タイムアウトを設定して、60 秒延長します。</span><span class="sxs-lookup"><span data-stu-id="40255-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="40255-157">これにより、メッセージに関連付けられている作業の状態が保存され、クライアントにメッセージの操作を続行する時間が 1 分与えられます。</span><span class="sxs-lookup"><span data-stu-id="40255-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="40255-158">この方法を使用すると、キュー メッセージに対する複数の手順から成るワークフローを追跡でき、ハードウェアまたはソフトウェアの問題が原因で処理手順が失敗した場合に最初からやり直す必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="40255-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="40255-159">通常は、さらに再試行回数を保持し、メッセージの再試行回数が特定の回数を超えた場合はこれを削除するようにします。</span><span class="sxs-lookup"><span data-stu-id="40255-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="40255-160">こうすることで、処理するたびにアプリケーション エラーをトリガーするメッセージから保護されます。</span><span class="sxs-lookup"><span data-stu-id="40255-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="40255-161">次のメッセージをデキューする</span><span class="sxs-lookup"><span data-stu-id="40255-161">De-queue the next message</span></span>

<span data-ttu-id="40255-162">コードでは、2 つの手順でキューからメッセージをデキューします。</span><span class="sxs-lookup"><span data-stu-id="40255-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="40255-163">`GetMessage`を呼び出すと、キュー内の次のメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="40255-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="40255-164">`GetMessage` から返されたメッセージは、このキューからメッセージを読み取る他のコードから参照できなくなります。</span><span class="sxs-lookup"><span data-stu-id="40255-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="40255-165">既定では、このメッセージを参照できない状態は 30 秒間続きます。</span><span class="sxs-lookup"><span data-stu-id="40255-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="40255-166">また、キューからのメッセージの削除を完了するには、`DeleteMessage` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="40255-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="40255-167">このようにメッセージを 2 つの手順で削除することで、ハードウェアまたはソフトウェアの問題が原因でコードによるメッセージの処理が失敗した場合に、コードの別のインスタンスで同じメッセージを取得し、もう一度処理することができます。</span><span class="sxs-lookup"><span data-stu-id="40255-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="40255-168">ご自分のコードで、メッセージが処理された直後に `DeleteMessage` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40255-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="40255-169">一般的な Queue Storage API を使った非同期ワークフローの使用</span><span class="sxs-lookup"><span data-stu-id="40255-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="40255-170">この例では、一般的な Queue Storage API を使って非同期ワークフローを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="40255-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="40255-171">メッセージのデキュー用の追加オプション</span><span class="sxs-lookup"><span data-stu-id="40255-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="40255-172">キューからのメッセージの取得をカスタマイズする方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="40255-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="40255-173">1 つ目の方法では、(最大 32 個の) メッセージのバッチを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40255-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="40255-174">2 つ目の方法では、コードで各メッセージを完全に処理できるように、非表示タイムアウトの設定を長くまたは短くすることができます。</span><span class="sxs-lookup"><span data-stu-id="40255-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="40255-175">次のコード例では、`GetMessages` を使用して 1 回の呼び出しで 20 件のメッセージを取得してから、各メッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="40255-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="40255-176">また、各メッセージの非表示タイムアウトを 5 分に設定します。</span><span class="sxs-lookup"><span data-stu-id="40255-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="40255-177">この 5 分間は、すべてのメッセージに対して同時に開始されます。そのため、`GetMessages` への呼び出しから 5 分が経過すると、削除されていないすべてのメッセージが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="40255-177">The 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages that have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="40255-178">キューの長さを取得する</span><span class="sxs-lookup"><span data-stu-id="40255-178">Get the queue length</span></span>

<span data-ttu-id="40255-179">キュー内のメッセージの概数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="40255-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="40255-180">`FetchAttributes` メソッドによって、メッセージ数などのキューの属性を取得するように Queue サービスに要求します。</span><span class="sxs-lookup"><span data-stu-id="40255-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="40255-181">`ApproximateMessageCount` プロパティを使用すると、Queue サービスを呼び出すことなく、`FetchAttributes` メソッドによって取得された最後の値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="40255-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="40255-182">キューを削除する</span><span class="sxs-lookup"><span data-stu-id="40255-182">Delete a queue</span></span>

<span data-ttu-id="40255-183">キューおよびキューに格納されているすべてのメッセージを削除するには、キュー オブジェクトの `Delete` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40255-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="40255-184">次のステップ</span><span class="sxs-lookup"><span data-stu-id="40255-184">Next steps</span></span>

<span data-ttu-id="40255-185">これで、Queue ストレージの基本を学習できました。さらに複雑なストレージ タスクを実行するには、次のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40255-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="40255-186">.NET 用 Azure Storage API</span><span class="sxs-lookup"><span data-stu-id="40255-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="40255-187">Azure Storage Type Provider</span><span class="sxs-lookup"><span data-stu-id="40255-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="40255-188">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="40255-188">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="40255-189">Azure Storage の接続文字列を構成する</span><span class="sxs-lookup"><span data-stu-id="40255-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="40255-190">Azure Storage サービスの REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="40255-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
