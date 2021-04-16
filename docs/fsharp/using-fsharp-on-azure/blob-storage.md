---
title: F# を使用した Azure Blob Storage の概要
description: Azure Blob Storage を使用して、非構造化データをクラウドに格納します。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 58c120c26a1e99481b49ae3a0fb096a2188f359e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794812"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="93228-103">F\# を使用した Azure Blob Storage の概要</span><span class="sxs-lookup"><span data-stu-id="93228-103">Get started with Azure Blob Storage using F\#</span></span>

<span data-ttu-id="93228-104">Azure Blob Storage は、非構造化データをオブジェクトまたは BLOB としてクラウドに格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="93228-104">Azure Blob Storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="93228-105">Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキスト データやバイナリ データを格納できます。</span><span class="sxs-lookup"><span data-stu-id="93228-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="93228-106">Blob Storage は、オブジェクト ストレージとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="93228-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="93228-107">この記事では、BLOB ストレージを使用して一般的なタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93228-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="93228-108">例は F# を使用して記述され、.NET 用 Azure Storage クライアント ライブラリを利用しています。</span><span class="sxs-lookup"><span data-stu-id="93228-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="93228-109">紹介するタスクでは、BLOB のアップロード、一覧表示、ダウンロード、削除の方法を扱います。</span><span class="sxs-lookup"><span data-stu-id="93228-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="93228-110">BLOB ストレージの概念の概要については、[BLOB ストレージの .NET ガイド](/azure/storage/blobs/storage-quickstart-blobs-dotnet)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93228-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93228-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="93228-111">Prerequisites</span></span>

<span data-ttu-id="93228-112">このガイドを使用するには、まず [Azure ストレージ アカウントを作成する](/azure/storage/common/storage-account-create)必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="93228-113">また、このアカウントのストレージ アクセス キーも必要です。</span><span class="sxs-lookup"><span data-stu-id="93228-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="93228-114">F# スクリプトを作成して F# インタラクティブを開始する</span><span class="sxs-lookup"><span data-stu-id="93228-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="93228-115">この記事のサンプルは、F# アプリケーションまたは F# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="93228-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="93228-116">F# スクリプトを作成するには、`.fsx` 拡張子のファイルを作成します。たとえば、F# 開発環境では `blobs.fsx` です。</span><span class="sxs-lookup"><span data-stu-id="93228-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="93228-117">次に、[Paket](https://fsprojects.github.io/Paket/) や [NuGet](https://www.nuget.org/) などの[パッケージ マネージャー](package-management.md)を使用して、`WindowsAzure.Storage` および `Microsoft.WindowsAzure.ConfigurationManager` パッケージをインストールします。スクリプト内で `#r` ディレクティブを使用して、`WindowsAzure.Storage.dll` と `Microsoft.WindowsAzure.Configuration.dll` を参照します。</span><span class="sxs-lookup"><span data-stu-id="93228-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="93228-118">名前空間宣言の追加</span><span class="sxs-lookup"><span data-stu-id="93228-118">Add namespace declarations</span></span>

<span data-ttu-id="93228-119">次の `open` ステートメントを `blobs.fsx` ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="93228-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="93228-120">接続文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="93228-120">Get your connection string</span></span>

<span data-ttu-id="93228-121">このチュートリアルでは、Azure Storage 接続文字列が必要です。</span><span class="sxs-lookup"><span data-stu-id="93228-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="93228-122">接続文字列の詳細については、[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93228-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="93228-123">このチュートリアルでは、次のようにスクリプトに接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="93228-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="93228-124">ただし、これは実際のプロジェクトでは **お勧めしません**。</span><span class="sxs-lookup"><span data-stu-id="93228-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="93228-125">ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="93228-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="93228-126">ストレージ アカウント キーは常に慎重に保護してください。</span><span class="sxs-lookup"><span data-stu-id="93228-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="93228-127">このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="93228-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="93228-128">キーがセキュリティ侵害されたと思われる場合は、Azure portal を使用してキーを再生成できます。</span><span class="sxs-lookup"><span data-stu-id="93228-128">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="93228-129">実際のアプリケーションでは、ストレージ接続文字列を維持する最適な場所は構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="93228-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="93228-130">構成ファイルから接続文字列をフェッチするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="93228-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="93228-131">Azure Configuration Manager の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="93228-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="93228-132">また、.NET Framework の `ConfigurationManager` 型などの API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="93228-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="93228-133">接続文字列を解析する</span><span class="sxs-lookup"><span data-stu-id="93228-133">Parse the connection string</span></span>

<span data-ttu-id="93228-134">接続文字列を解析するには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="93228-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="93228-135">これにより、`CloudStorageAccount` が返されます。</span><span class="sxs-lookup"><span data-stu-id="93228-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="93228-136">ローカル ダミー データを作成する</span><span class="sxs-lookup"><span data-stu-id="93228-136">Create some local dummy data</span></span>

<span data-ttu-id="93228-137">開始する前に、スクリプトのディレクトリにダミーのローカル データを作成します。</span><span class="sxs-lookup"><span data-stu-id="93228-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="93228-138">後でこのデータをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="93228-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="93228-139">Blob service クライアントの作成</span><span class="sxs-lookup"><span data-stu-id="93228-139">Create the Blob service client</span></span>

<span data-ttu-id="93228-140">`CloudBlobClient` 型を使用すると、BLOB ストレージ内に格納されているコンテナーと BLOB を取得できます。</span><span class="sxs-lookup"><span data-stu-id="93228-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="93228-141">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="93228-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="93228-142">これで、Blob Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="93228-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="93228-143">コンテナーを作成する</span><span class="sxs-lookup"><span data-stu-id="93228-143">Create a container</span></span>

<span data-ttu-id="93228-144">この例は、コンテナーがない場合に、コンテナーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93228-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="93228-145">既定では、新しいコンテナーはプライベートなので、このコンテナーから BLOB をダウンロードするにはストレージ アクセス キーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="93228-146">コンテナー内のファイルをだれでも利用できるようにする場合は、次のコードを使ってコンテナーをパブリックに設定できます。</span><span class="sxs-lookup"><span data-stu-id="93228-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="93228-147">パブリック コンテナー内の BLOB は、インターネットに接続しているすべてのユーザーが表示できますが、変更または削除できるのは、適切なアカウント アクセス キーまたは Shared Access Signature を持っているユーザーだけです。</span><span class="sxs-lookup"><span data-stu-id="93228-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="93228-148">コンテナーに BLOB をアップロードする</span><span class="sxs-lookup"><span data-stu-id="93228-148">Upload a blob into a container</span></span>

<span data-ttu-id="93228-149">Azure Blob Storage では、ブロック BLOB とページ BLOB がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="93228-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="93228-150">ほとんどの場合は、ブロック BLOB の種類を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="93228-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="93228-151">ファイルをブロック blob にアップロードするには、コンテナーの参照を取得し、それを使用してブロック blob の参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="93228-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="93228-152">BLOB の参照を取得したら、`UploadFromFile` メソッドを呼び出すことによって、データの任意のストリームを BLOB にアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="93228-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="93228-153">この操作により、BLOB がまだ存在しない場合は作成され、存在する場合は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="93228-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="93228-154">コンテナー内の BLOB を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="93228-154">List the blobs in a container</span></span>

<span data-ttu-id="93228-155">コンテナー内の BLOB を一覧表示するには、まず、コンテナーの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="93228-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="93228-156">次に、コンテナーの `ListBlobs` メソッドを使用して、その中の BLOB やディレクトリを取得できます。</span><span class="sxs-lookup"><span data-stu-id="93228-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="93228-157">返された `IListBlobItem` の豊富なプロパティとメソッドにアクセスするには、これを `CloudBlockBlob`、`CloudPageBlob`、または `CloudBlobDirectory` オブジェクトにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="93228-158">型がわからない場合は、型チェックを使うとどれにキャストすればよいかがわかります。</span><span class="sxs-lookup"><span data-stu-id="93228-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="93228-159">次のコードは、 `mydata` コンテナー内の各アイテムの URI を取得して出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93228-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="93228-160">BLOB の名前はパス情報を含めて指定することができます。</span><span class="sxs-lookup"><span data-stu-id="93228-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="93228-161">これで、従来のファイル システムと同じように、整理およびスキャン可能な仮想ディレクトリ構造が作成されます。</span><span class="sxs-lookup"><span data-stu-id="93228-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="93228-162">ディレクトリ構造は仮想のみであり、BLOB ストレージで使用できるリソースはコンテナーと BLOB のみです。</span><span class="sxs-lookup"><span data-stu-id="93228-162">The directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="93228-163">ただし、ストレージ クライアント ライブラリでは、仮想ディレクトリを参照し、この方法で整理されている BLOB の操作プロセスを簡略化するための `CloudBlobDirectory` オブジェクトが提供されています。</span><span class="sxs-lookup"><span data-stu-id="93228-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="93228-164">たとえば、 `photos`という名前のコンテナーに次の一連のブロック BLOB があったとします。</span><span class="sxs-lookup"><span data-stu-id="93228-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="93228-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-165">*photo1.jpg*</span></span>\
<span data-ttu-id="93228-166">*2015/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="93228-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="93228-167">*2015/architecture/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="93228-168">*2015/architecture/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="93228-169">*2016/architecture/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="93228-170">*2016/architecture/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="93228-171">*2016/architecture/description.txt*</span><span class="sxs-lookup"><span data-stu-id="93228-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="93228-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="93228-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="93228-173">1 つのコンテナーに対して `ListBlobs` を呼び出すと (上記サンプルを参照)、階層化された一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="93228-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="93228-174">コンテナー内のディレクトリと BLOB をそれぞれ表す `CloudBlobDirectory` と `CloudBlockBlob` オブジェクトの両方がこれに含まれている場合、結果の出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93228-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="93228-175">必要に応じて、`ListBlobs` メソッドの `UseFlatBlobListing` パラメーターを `true` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="93228-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="93228-176">この場合、コンテナー内のすべての BLOB が `CloudBlockBlob` オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="93228-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="93228-177">フラットな一覧を返す `ListBlobs` への呼び出しは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93228-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="93228-178">また、コンテナーの現在の内容によっては、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93228-178">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="93228-179">BLOB をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="93228-179">Download blobs</span></span>

<span data-ttu-id="93228-180">BLOB をダウンロードするには、まず BLOB の参照を取得し、次に `DownloadToStream` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="93228-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="93228-181">次の例は、`DownloadToStream` メソッドを使用して、ローカル ファイルに保存できるストリーム オブジェクトに BLOB の内容を転送します。</span><span class="sxs-lookup"><span data-stu-id="93228-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="93228-182">`DownloadToStream` メソッドを使用して BLOB の内容をテキスト文字列としてダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="93228-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="93228-183">BLOB を削除する</span><span class="sxs-lookup"><span data-stu-id="93228-183">Delete blobs</span></span>

<span data-ttu-id="93228-184">BLOB を削除するには、まず BLOB の参照を取得し、次にその `Delete` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="93228-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="93228-185">BLOB をページで非同期に一覧表示する</span><span class="sxs-lookup"><span data-stu-id="93228-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="93228-186">多数の BLOB を一覧表示する場合や、1 回の一覧表示操作で返される結果の数を制御する場合には、BLOB の一覧を結果のページで表示できます。</span><span class="sxs-lookup"><span data-stu-id="93228-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="93228-187">この例は、大きな結果のセットを返すために待機している間に実行がブロックされないように、結果をページで非同期に返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93228-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="93228-188">この例では、BLOB をフラットな一覧で表示しますが、`ListBlobsSegmentedAsync` メソッドの `useFlatBlobListing` パラメーターを `false` に設定することによって、階層化された一覧で表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="93228-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="93228-189">このサンプルでは、`async` ブロックを使用して非同期メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="93228-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="93228-190">``let!`` キーワードを使用すると、一覧表示タスクが完了するまでサンプル メソッドの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="93228-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="93228-191">次のように、この非同期ルーチンを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="93228-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="93228-192">まずダミー データをアップロードします (このチュートリアルで既に作成したローカル ファイルを使用します)。</span><span class="sxs-lookup"><span data-stu-id="93228-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="93228-193">ここで、ルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="93228-193">Now, call the routine.</span></span> <span data-ttu-id="93228-194">非同期操作の実行を強制するには、`Async.RunSynchronously` を使用します。</span><span class="sxs-lookup"><span data-stu-id="93228-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="93228-195">追加 BLOB への書き込み</span><span class="sxs-lookup"><span data-stu-id="93228-195">Writing to an append blob</span></span>

<span data-ttu-id="93228-196">追加 BLOB は、ログ記録などの追加操作のために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="93228-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="93228-197">ブロック BLOB のように、追加 BLOB はブロックで構成されますが、追加 BLOB に新しいブロックを追加する場合は常に BLOB の最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="93228-197">Like a block blob, an append blob is composed of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="93228-198">追加 BLOB の既存のブロックは更新したり、削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="93228-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="93228-199">追加 BLOB のブロック ID はブロック BLOB 用のため、公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="93228-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="93228-200">追加 BLOB 内の各ブロックは、最大 4 MB のサイズにすることができます。また追加 BLOB には最大 50,000 のブロックを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="93228-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="93228-201">よって追加 BLOB の最大サイズは 195 GB (4 MB X 50,000 ブロック) よりも少し大きくなります。</span><span class="sxs-lookup"><span data-stu-id="93228-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="93228-202">次の例では、新しい追加 BLOB を作成し、データを追加してシンプルなログ記録操作をシミュレートしています。</span><span class="sxs-lookup"><span data-stu-id="93228-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="93228-203">3 つの BLOB タイプにおける違いの詳細については、「 [Understanding Block Blobs, Page Blobs, and Append Blobs (ブロック BLOB、ページ BLOB、追加 BLOB を理解する)](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="93228-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="93228-204">同時アクセス</span><span class="sxs-lookup"><span data-stu-id="93228-204">Concurrent access</span></span>

<span data-ttu-id="93228-205">複数のクライアントまたは複数のプロセス インスタンスからの BLOB への同時アクセスをサポートするには、**ETag** または **占有** を使います。</span><span class="sxs-lookup"><span data-stu-id="93228-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="93228-206">**Etag** - BLOB またはコンテナーが別のプロセスによって変更されていることを検出する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="93228-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="93228-207">**占有** - 一定期間、BLOB に対する排他的で更新可能な書き込みアクセスまたは削除アクセスを取得する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="93228-207">**Lease** - provides a way to obtain exclusive, renewable, write, or delete access to a blob for a period of time</span></span>

<span data-ttu-id="93228-208">詳細については、「[Microsoft Azure Storage でのコンカレンシーの管理](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93228-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="93228-209">名前付けコンテナー</span><span class="sxs-lookup"><span data-stu-id="93228-209">Naming containers</span></span>

<span data-ttu-id="93228-210">Azure Storage のどの BLOB もコンテナーに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="93228-211">コンテナーは、BLOB 名の一部を形成しています。</span><span class="sxs-lookup"><span data-stu-id="93228-211">The container forms part of the blob name.</span></span> <span data-ttu-id="93228-212">たとえば、次の BLOB の URI のサンプルでは、 `mydata` がコンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="93228-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="93228-213">コンテナー名は有効な DNS 名で、次の名前規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="93228-214">コンテナー名は英文字または数字で始まり、英文字、数字、ダッシュ (-) 文字のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="93228-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="93228-215">すべてのダッシュ (-) 文字は、その直前または直後に文字または数字が使用されている必要があります。連続するダッシュ文字は、コンテナー名では使用できません。</span><span class="sxs-lookup"><span data-stu-id="93228-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="93228-216">コンテナー名の文字はすべて小文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="93228-217">コンテナー名の長さは、3 ～ 63 文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="93228-218">コンテナーの名前は、常に小文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="93228-218">The name of a container must always be lowercase.</span></span> <span data-ttu-id="93228-219">コンテナー名に大文字が含まれている場合や、コンテナーの名前付け規則の他の違反がある場合、400 エラー (無効な要求) が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="93228-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="93228-220">BLOB のセキュリティの管理</span><span class="sxs-lookup"><span data-stu-id="93228-220">Managing security for blobs</span></span>

<span data-ttu-id="93228-221">既定では、Azure Storage はアカウント所有者へのアクセスを制限することによってデータのセキュリティを維持します。アカウントの所有者は、アカウント アクセス キーを所持している人です。</span><span class="sxs-lookup"><span data-stu-id="93228-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="93228-222">ストレージ アカウント内の BLOB データを共有する必要がある場合は、アカウント アクセス キーのセキュリティを損なわずに共有することが重要です。</span><span class="sxs-lookup"><span data-stu-id="93228-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="93228-223">また、ネットワーク経由の送信と Azure Storage でのセキュリティを確保するために、BLOB データを暗号化することもできます。</span><span class="sxs-lookup"><span data-stu-id="93228-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="93228-224">BLOB データへのアクセスの制御</span><span class="sxs-lookup"><span data-stu-id="93228-224">Controlling access to blob data</span></span>

<span data-ttu-id="93228-225">既定では、ストレージ アカウント内の BLOB データには、ストレージ アカウント所有者だけがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="93228-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="93228-226">Blob Storage に対する認証要求には、既定ではアカウント アクセス キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="93228-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="93228-227">ただし、特定の BLOB データは他のユーザーが使用できるようにしたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="93228-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="93228-228">BLOB データの暗号化</span><span class="sxs-lookup"><span data-stu-id="93228-228">Encrypting blob data</span></span>

<span data-ttu-id="93228-229">Azure Storage では、クライアント側とサーバー側の両方で、BLOB データの暗号化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="93228-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="93228-230">次のステップ</span><span class="sxs-lookup"><span data-stu-id="93228-230">Next steps</span></span>

<span data-ttu-id="93228-231">これで、Blob Storage の基本を学習できました。さらに詳細な情報が必要な場合は、次のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93228-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="93228-232">ツール</span><span class="sxs-lookup"><span data-stu-id="93228-232">Tools</span></span>

- <span data-ttu-id="93228-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="93228-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="93228-234">BLOB、テーブル、キューの Azure Storage 資産を探索し、それに CRUD 操作を簡単に適用するために使用できる F# 型プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="93228-234">An F# Type Provider that can be used to explore Blob, Table, and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="93228-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="93228-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="93228-236">Microsoft Azure Table Storage サービスを使用するための F# API</span><span class="sxs-lookup"><span data-stu-id="93228-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="93228-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="93228-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="93228-238">Windows、OS X、Linux 上で Azure Storage のデータを視覚的に操作できる Microsoft 製の無料のスタンドアロン アプリです。</span><span class="sxs-lookup"><span data-stu-id="93228-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="93228-239">Blob Storage リファレンス</span><span class="sxs-lookup"><span data-stu-id="93228-239">Blob storage reference</span></span>

- [<span data-ttu-id="93228-240">.NET 用 Azure Storage API</span><span class="sxs-lookup"><span data-stu-id="93228-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="93228-241">Azure Storage サービスの REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="93228-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="93228-242">関連ガイド</span><span class="sxs-lookup"><span data-stu-id="93228-242">Related guides</span></span>

- [<span data-ttu-id="93228-243">.NET 用の Azure Blob Storage サンプル</span><span class="sxs-lookup"><span data-stu-id="93228-243">Azure Blob Storage Samples for .NET</span></span>](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="93228-244">AzCopy を使ってみる</span><span class="sxs-lookup"><span data-stu-id="93228-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="93228-245">Azure Storage の接続文字列を構成する</span><span class="sxs-lookup"><span data-stu-id="93228-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="93228-246">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="93228-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="93228-247">クイック スタート: .NET を使用してオブジェクト ストレージ内に BLOB を作成する</span><span class="sxs-lookup"><span data-stu-id="93228-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
