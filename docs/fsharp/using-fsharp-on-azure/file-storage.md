---
title: F# を使用した Azure File Storage の概要
description: Azure File Storage を使用してクラウドにファイル データを格納し、Azure 仮想マシン (VM) から、または Windows を実行しているオンプレミスのアプリケーションからクラウド ファイル共有をマウントします。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: bcea58b4bf756fc9d696cd5a1010b0feffb127a7
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899426"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="906ea-103">F\# を使用した Azure File Storage の概要</span><span class="sxs-lookup"><span data-stu-id="906ea-103">Get started with Azure File Storage using F\#</span></span>

<span data-ttu-id="906ea-104">Azure File Storage は、標準の[サーバー メッセージ ブロック (SMB) プロトコル](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)を使用してクラウドでファイル共有を提供するサービスです。</span><span class="sxs-lookup"><span data-stu-id="906ea-104">Azure File Storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview).</span></span> <span data-ttu-id="906ea-105">SMB 2.1 と SMB 3.0 の両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="906ea-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="906ea-106">Azure File Storage を使用すると、コストがかかる書き換えを行わずに、ファイル共有に依存しているレガシ アプリケーションをすばやく Azure に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="906ea-106">With Azure File Storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="906ea-107">Azure 仮想マシンまたはクラウド サービスで実行されているアプリケーション、またはオンプレミスのクライアントから実行されているアプリケーションは、デスクトップ アプリケーションが一般的な SMB 共有をマウントするのと同じように、クラウドにファイル共有をマウントできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="906ea-108">このため、任意の数のアプリケーション コンポーネントが、File Storage 共有をマウントして同時にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="906ea-109">File Storage の概念の概要については、[File Storage の .NET ガイド](/azure/storage/storage-dotnet-how-to-use-files)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="906ea-109">For a conceptual overview of file storage, see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="906ea-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="906ea-110">Prerequisites</span></span>

<span data-ttu-id="906ea-111">このガイドを使用するには、まず [Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)必要があります。</span><span class="sxs-lookup"><span data-stu-id="906ea-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="906ea-112">また、このアカウントのストレージ アクセス キーも必要になります。</span><span class="sxs-lookup"><span data-stu-id="906ea-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="906ea-113">F# スクリプトを作成して F# インタラクティブを開始する</span><span class="sxs-lookup"><span data-stu-id="906ea-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="906ea-114">この記事のサンプルは、F# アプリケーションまたは F# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="906ea-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="906ea-115">F# スクリプトを作成するには、`.fsx` 拡張子のファイルを作成します。たとえば、F# 開発環境では `files.fsx` です。</span><span class="sxs-lookup"><span data-stu-id="906ea-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="906ea-116">次に、[Paket](https://fsprojects.github.io/Paket/)や [NuGet](https://www.nuget.org/) などの[パッケージ マネージャー](package-management.md)を使用し、`#r` ディレクティブを使用して `WindowsAzure.Storage` パッケージと参照 `WindowsAzure.Storage.dll` をスクリプトにインストールします。</span><span class="sxs-lookup"><span data-stu-id="906ea-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="906ea-117">名前空間宣言の追加</span><span class="sxs-lookup"><span data-stu-id="906ea-117">Add namespace declarations</span></span>

<span data-ttu-id="906ea-118">次の `open` ステートメントを `files.fsx` ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="906ea-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="906ea-119">接続文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="906ea-119">Get your connection string</span></span>

<span data-ttu-id="906ea-120">このチュートリアルでは、Azure Storage 接続文字列が必要になります。</span><span class="sxs-lookup"><span data-stu-id="906ea-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="906ea-121">接続文字列の詳細については、[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="906ea-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="906ea-122">このチュートリアルでは、次のようにスクリプトに接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="906ea-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="906ea-123">ただし、これは実際のプロジェクトでは **お勧めしません**。</span><span class="sxs-lookup"><span data-stu-id="906ea-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="906ea-124">ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="906ea-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="906ea-125">ストレージ アカウント キーは常に慎重に保護してください。</span><span class="sxs-lookup"><span data-stu-id="906ea-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="906ea-126">このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="906ea-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="906ea-127">キーがセキュリティ侵害されたと思われる場合は、Azure portal を使用してキーを再生成できます。</span><span class="sxs-lookup"><span data-stu-id="906ea-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="906ea-128">実際のアプリケーションでは、ストレージ接続文字列を維持する最適な場所は構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="906ea-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="906ea-129">構成ファイルから接続文字列をフェッチするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="906ea-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="906ea-130">Azure Configuration Manager の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="906ea-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="906ea-131">また、.NET Framework の `ConfigurationManager` 型などの API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="906ea-132">接続文字列を解析する</span><span class="sxs-lookup"><span data-stu-id="906ea-132">Parse the connection string</span></span>

<span data-ttu-id="906ea-133">接続文字列を解析するには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="906ea-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="906ea-134">これによって、`CloudStorageAccount` が返されます。</span><span class="sxs-lookup"><span data-stu-id="906ea-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="906ea-135">ファイル サービス クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="906ea-135">Create the File service client</span></span>

<span data-ttu-id="906ea-136">`CloudFileClient` 型を使用すると、File Storage に格納されているファイルをプログラムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="906ea-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="906ea-137">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="906ea-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="906ea-138">これで、File Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="906ea-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="906ea-139">ファイル共有を作成する</span><span class="sxs-lookup"><span data-stu-id="906ea-139">Create a file share</span></span>

<span data-ttu-id="906ea-140">この例では、ファイル共有がない場合に、それを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="906ea-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="906ea-141">ルート ディレクトリとサブディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="906ea-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="906ea-142">ここでは、ルート ディレクトリを取得し、ルートのサブディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="906ea-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="906ea-143">まだ存在しない場合は、両方を作成します。</span><span class="sxs-lookup"><span data-stu-id="906ea-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="906ea-144">テキストをファイルとしてアップロードする</span><span class="sxs-lookup"><span data-stu-id="906ea-144">Upload text as a file</span></span>

<span data-ttu-id="906ea-145">この例では、テキストをファイルとしてアップロードする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="906ea-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="906ea-146">ファイルのローカル コピーにファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="906ea-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="906ea-147">ここでは、作成したばかりのファイルをダウンロードし、ローカル ファイルにコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="906ea-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="906ea-148">ファイル共有の最大サイズの設定</span><span class="sxs-lookup"><span data-stu-id="906ea-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="906ea-149">次の例では、共有の現在の使用状況を確認する方法と、共有のクォータを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="906ea-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="906ea-150">共有の `Properties` を設定するには `FetchAttributes` を呼び出し、ローカルの変更を Azure File Storage に反映するには `SetProperties` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="906ea-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File Storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="906ea-151">ファイルまたはファイル共有の Shared Access Signature の生成</span><span class="sxs-lookup"><span data-stu-id="906ea-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="906ea-152">ファイル共有または個々のファイルの Shared Access Signature (SAS) を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="906ea-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="906ea-153">また、ファイル共有に共有アクセス ポリシーを作成して、Shared Access Signature を管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="906ea-154">共有アクセス ポリシーを作成することをお勧めします。これにより、侵害されそうな場合に SAS を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="906ea-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="906ea-155">ここでは、共有上に共有アクセス ポリシーを作成してから、そのポリシーを使用して共有上のファイルの SAS に制約を指定します。</span><span class="sxs-lookup"><span data-stu-id="906ea-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="906ea-156">Shared Access Signature の作成と使用の詳細については、「[Shared Access Signature (SAS) の使用](/azure/storage/storage-dotnet-shared-access-signature-part-1)」と、[Blob Storage での SAS の作成と使用](/azure/storage/storage-dotnet-shared-access-signature-part-2)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="906ea-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="906ea-157">ファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="906ea-157">Copy files</span></span>

<span data-ttu-id="906ea-158">ファイルを別のファイルまたは BLOB にコピーしたり、BLOB をファイルにコピーしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="906ea-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="906ea-159">BLOB をファイルにコピーしたり、ファイルを BLOB にコピーしたりする場合は、同じストレージ アカウント内でコピーする場合でも、Shared Access Signature (SAS) を使用してソース オブジェクトを認証する *必要* があります。</span><span class="sxs-lookup"><span data-stu-id="906ea-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="906ea-160">別のファイルへのファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="906ea-160">Copy a file to another file</span></span>

<span data-ttu-id="906ea-161">ここでは、同じ共有内の別のファイルにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="906ea-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="906ea-162">このコピー操作では同じストレージ アカウント内のファイルがコピーされるため、共有キー認証を使用してコピーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="906ea-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="906ea-163">BLOB へのファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="906ea-163">Copy a file to a blob</span></span>

<span data-ttu-id="906ea-164">ここでは、ファイルを作成し、同じストレージ アカウント内の BLOB にコピーします。</span><span class="sxs-lookup"><span data-stu-id="906ea-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="906ea-165">ソース ファイルの SAS を作成します。サービスによってこれを使用されて、コピー操作中にソース ファイルへのアクセスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="906ea-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="906ea-166">同じ方法で、ファイルに BLOB をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="906ea-167">ソース オブジェクトが BLOB である場合、SAS を作成して、コピー操作中にその BLOB へのアクセスを認証します。</span><span class="sxs-lookup"><span data-stu-id="906ea-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="906ea-168">メトリックを使用した File Storage のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="906ea-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="906ea-169">Azure Storage Analytics では File Storage のメトリックがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="906ea-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="906ea-170">メトリック データを使用すると、要求のトレースや問題の診断ができます。</span><span class="sxs-lookup"><span data-stu-id="906ea-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="906ea-171">[Azure portal](https://portal.azure.com) から File Storage のメトリックを有効にすることも、次のように F# から行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="906ea-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="906ea-172">次のステップ</span><span class="sxs-lookup"><span data-stu-id="906ea-172">Next steps</span></span>

<span data-ttu-id="906ea-173">Azure File Storage の詳細については、次のリンクをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="906ea-173">For more information about Azure File Storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="906ea-174">概念に関する記事とビデオ</span><span class="sxs-lookup"><span data-stu-id="906ea-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="906ea-175">Azure File Storage: Windows および Linux 用の円滑なクラウド SMB ファイル システム</span><span class="sxs-lookup"><span data-stu-id="906ea-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="906ea-176">Linux で Azure File Storage を使用する方法</span><span class="sxs-lookup"><span data-stu-id="906ea-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="906ea-177">File Storage 用のツールのサポート</span><span class="sxs-lookup"><span data-stu-id="906ea-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="906ea-178">Azure Storage での Azure PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="906ea-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="906ea-179">Microsoft Azure Storage で AzCopy を使用する方法</span><span class="sxs-lookup"><span data-stu-id="906ea-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="906ea-180">Azure CLI を使用して BLOB を作成、ダウンロード、一覧表示する</span><span class="sxs-lookup"><span data-stu-id="906ea-180">Create, download, and list blobs with Azure CLI</span></span>](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="906ea-181">リファレンス</span><span class="sxs-lookup"><span data-stu-id="906ea-181">Reference</span></span>

- [<span data-ttu-id="906ea-182">.NET 用ストレージ クライアント ライブラリ リファレンス</span><span class="sxs-lookup"><span data-stu-id="906ea-182">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="906ea-183">File サービスの REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="906ea-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="906ea-184">ブログ記事</span><span class="sxs-lookup"><span data-stu-id="906ea-184">Blog posts</span></span>

- [<span data-ttu-id="906ea-185">Azure File Storage の一般提供開始</span><span class="sxs-lookup"><span data-stu-id="906ea-185">Azure File Storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="906ea-186">Inside Azure File Storage (Azure File Storage の内部)</span><span class="sxs-lookup"><span data-stu-id="906ea-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="906ea-187">Microsoft Azure File サービスの概要</span><span class="sxs-lookup"><span data-stu-id="906ea-187">Introducing Microsoft Azure File Service</span></span>](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="906ea-188">Microsoft Azure Files への接続の維持</span><span class="sxs-lookup"><span data-stu-id="906ea-188">Persisting connections to Microsoft Azure Files</span></span>](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
