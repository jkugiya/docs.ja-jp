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
# <a name="get-started-with-azure-file-storage-using-f"></a>F\# を使用した Azure File Storage の概要

Azure File Storage は、標準の[サーバー メッセージ ブロック (SMB) プロトコル](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)を使用してクラウドでファイル共有を提供するサービスです。 SMB 2.1 と SMB 3.0 の両方がサポートされます。 Azure File Storage を使用すると、コストがかかる書き換えを行わずに、ファイル共有に依存しているレガシ アプリケーションをすばやく Azure に移行することができます。 Azure 仮想マシンまたはクラウド サービスで実行されているアプリケーション、またはオンプレミスのクライアントから実行されているアプリケーションは、デスクトップ アプリケーションが一般的な SMB 共有をマウントするのと同じように、クラウドにファイル共有をマウントできます。 このため、任意の数のアプリケーション コンポーネントが、File Storage 共有をマウントして同時にアクセスできます。

File Storage の概念の概要については、[File Storage の .NET ガイド](/azure/storage/storage-dotnet-how-to-use-files)をご覧ください。

## <a name="prerequisites"></a>前提条件

このガイドを使用するには、まず [Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)必要があります。
また、このアカウントのストレージ アクセス キーも必要になります。

## <a name="create-an-f-script-and-start-f-interactive"></a>F# スクリプトを作成して F# インタラクティブを開始する

この記事のサンプルは、F# アプリケーションまたは F# スクリプトで使用できます。 F# スクリプトを作成するには、`.fsx` 拡張子のファイルを作成します。たとえば、F# 開発環境では `files.fsx` です。

次に、[Paket](https://fsprojects.github.io/Paket/)や [NuGet](https://www.nuget.org/) などの[パッケージ マネージャー](package-management.md)を使用し、`#r` ディレクティブを使用して `WindowsAzure.Storage` パッケージと参照 `WindowsAzure.Storage.dll` をスクリプトにインストールします。

### <a name="add-namespace-declarations"></a>名前空間宣言の追加

次の `open` ステートメントを `files.fsx` ファイルの先頭に追加します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得する

このチュートリアルでは、Azure Storage 接続文字列が必要になります。 接続文字列の詳細については、[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)に関する記事をご覧ください。

このチュートリアルでは、次のようにスクリプトに接続文字列を入力します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

ただし、これは実際のプロジェクトでは **お勧めしません**。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 ストレージ アカウント キーは常に慎重に保護してください。 このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。 キーがセキュリティ侵害されたと思われる場合は、Azure portal を使用してキーを再生成できます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最適な場所は構成ファイルです。 構成ファイルから接続文字列をフェッチするには、次の手順を実行します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Configuration Manager の使用はオプションです。 また、.NET Framework の `ConfigurationManager` 型などの API を使用することもできます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次を使用します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

これによって、`CloudStorageAccount` が返されます。

### <a name="create-the-file-service-client"></a>ファイル サービス クライアントを作成する

`CloudFileClient` 型を使用すると、File Storage に格納されているファイルをプログラムで使用できます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

これで、File Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。

## <a name="create-a-file-share"></a>ファイル共有を作成する

この例では、ファイル共有がない場合に、それを作成する方法を示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>ルート ディレクトリとサブディレクトリを作成する

ここでは、ルート ディレクトリを取得し、ルートのサブディレクトリを取得します。 まだ存在しない場合は、両方を作成します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>テキストをファイルとしてアップロードする

この例では、テキストをファイルとしてアップロードする方法を示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>ファイルのローカル コピーにファイルをダウンロードする

ここでは、作成したばかりのファイルをダウンロードし、ローカル ファイルにコンテンツを追加します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>ファイル共有の最大サイズの設定

次の例では、共有の現在の使用状況を確認する方法と、共有のクォータを設定する方法を示します。 共有の `Properties` を設定するには `FetchAttributes` を呼び出し、ローカルの変更を Azure File Storage に反映するには `SetProperties` を呼び出す必要があります。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>ファイルまたはファイル共有の Shared Access Signature の生成

ファイル共有または個々のファイルの Shared Access Signature (SAS) を生成することができます。 また、ファイル共有に共有アクセス ポリシーを作成して、Shared Access Signature を管理することもできます。 共有アクセス ポリシーを作成することをお勧めします。これにより、侵害されそうな場合に SAS を取り消すことができます。

ここでは、共有上に共有アクセス ポリシーを作成してから、そのポリシーを使用して共有上のファイルの SAS に制約を指定します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Shared Access Signature の作成と使用の詳細については、「[Shared Access Signature (SAS) の使用](/azure/storage/storage-dotnet-shared-access-signature-part-1)」と、[Blob Storage での SAS の作成と使用](/azure/storage/storage-dotnet-shared-access-signature-part-2)に関するページを参照してください。

### <a name="copy-files"></a>ファイルのコピー

ファイルを別のファイルまたは BLOB にコピーしたり、BLOB をファイルにコピーしたりすることができます。 BLOB をファイルにコピーしたり、ファイルを BLOB にコピーしたりする場合は、同じストレージ アカウント内でコピーする場合でも、Shared Access Signature (SAS) を使用してソース オブジェクトを認証する *必要* があります。

### <a name="copy-a-file-to-another-file"></a>別のファイルへのファイルのコピー

ここでは、同じ共有内の別のファイルにファイルをコピーします。 このコピー操作では同じストレージ アカウント内のファイルがコピーされるため、共有キー認証を使用してコピーを実行できます。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>BLOB へのファイルのコピー

ここでは、ファイルを作成し、同じストレージ アカウント内の BLOB にコピーします。 ソース ファイルの SAS を作成します。サービスによってこれを使用されて、コピー操作中にソース ファイルへのアクセスが認証されます。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

同じ方法で、ファイルに BLOB をコピーできます。 ソース オブジェクトが BLOB である場合、SAS を作成して、コピー操作中にその BLOB へのアクセスを認証します。

## <a name="troubleshooting-file-storage-using-metrics"></a>メトリックを使用した File Storage のトラブルシューティング

Azure Storage Analytics では File Storage のメトリックがサポートされています。 メトリック データを使用すると、要求のトレースや問題の診断ができます。

[Azure portal](https://portal.azure.com) から File Storage のメトリックを有効にすることも、次のように F# から行うこともできます。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>次のステップ

Azure File Storage の詳細については、次のリンクをご覧ください。

### <a name="conceptual-articles-and-videos"></a>概念に関する記事とビデオ

- [Azure File Storage: Windows および Linux 用の円滑なクラウド SMB ファイル システム](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux で Azure File Storage を使用する方法](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File Storage 用のツールのサポート

- [Azure Storage での Azure PowerShell の使用](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage で AzCopy を使用する方法](/azure/storage/storage-use-azcopy)
- [Azure CLI を使用して BLOB を作成、ダウンロード、一覧表示する](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>リファレンス

- [.NET 用ストレージ クライアント ライブラリ リファレンス](/dotnet/api/overview/azure/storage)
- [File サービスの REST API リファレンス](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>ブログ記事

- [Azure File Storage の一般提供開始](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage (Azure File Storage の内部)](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure File サービスの概要](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Microsoft Azure Files への接続の維持](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
