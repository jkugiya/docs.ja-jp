---
title: カスタム .NET Core ランタイム ホストを作成する
description: .NET Core ランタイムの動作を制御する必要がある高度なシナリオをサポートするために、ネイティブ コードから .NET Core ランタイムをホストする方法について説明します。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: db458e9ebb0c6ad930f82e1d67619632a493ae3b
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604698"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>ネイティブ コードから .NET ランタイムを制御するカスタム .NET Core ホストを作成する

あらゆるマネージド コードと同様に、.NET Core アプリケーションはホストにより実行されます。 ホストは、ランタイム (JIT やガベージ コレクターのようなコンポーネントを含む) の開始、マネージド エントリ ポイントの呼び出しを担当します。

.NET Core ランタイムのホスティングは高度なシナリオです。ほとんどの場合、.NET Core 開発者はホスティングについて心配する必要がありません。 .NET Core ビルド プロセスが .NET Core アプリケーションを実行するための既定ホストを提供するためです。 ただし、特別な状況で、ネイティブ プロセスのマネージド コードを呼び出す手段として、あるいはランタイムの動作をさらに細かくコントロールする目的で .NET Core ランタイムを明示的にホスティングすると効果的な場合があります。

この記事では、ネイティブ コードから .NET Core ランタイムを開始し、その中でマネージド コードを実行するために必要な手順について説明します。

## <a name="prerequisites"></a>必須コンポーネント

ホストはネイティブ アプリケーションであるため、このチュートリアルでは、C++ アプリケーションを構築して .NET Core をホスティングする方法について説明します。 C++ 開発環境が必要になります ([Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) に付属のものなど)。

ホストをテストするための単純な .NET Core アプリケーションも必要です。そのため、[.NET Core SDK](https://dotnet.microsoft.com/download) をインストールし、[小さい .NET Core テスト アプリを作成](with-visual-studio.md)してください ('Hello World' アプリなど)。 新しい .NET Core コンソール プロジェクト テンプレートで作成される 'Hello World' アプリで十分です。

## <a name="hosting-apis"></a>ホスト API

.NET Core をホストするために使用できる API が 2 種類あります。 この記事 (とそれに関連する[サンプル](https://github.com/dotnet/samples/tree/master/core/hosting)) では、これら 2 つのオプションについて説明します。

* .NET Core 3.0 以降の .NET Core ランタイムをホストする推奨される方法は、`nethost` および `hostfxr` ライブラリの API を使うことです。 これらのエントリ ポイントは、初期化のためにランタイムを検索して設定する複雑な処理が行われ、マネージド アプリケーションの起動と静的マネージド メソッドの呼び出しの両方が可能です。
* .NET Core 3.0 より前の .NET Core ランタイムをホストする推奨される方法は、[`coreclrhost.h`](https://github.com/dotnet/runtime/blob/master/src/coreclr/hosts/inc/coreclrhost.h) API を使うことです。 この API では、ランタイムを簡単に開始および停止し、(マネージド exe を起動するか、静的マネージド メソッドを呼び出すことで) マネージド コードを呼び出すために関数が公開されます。

## <a name="sample-hosts"></a>サンプル ホスト

dotnet/samples GitHub リポジトリには、以下のチュートリアルで説明する手順を実演する[サンプル ホスト](https://github.com/dotnet/samples/tree/master/core/hosting)があります。 サンプルのコメントを見れば、これらのチュートリアルで番号が付けられている手順がサンプルのどこで実行されるかわかります。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。

サンプル ホストは学習目的のために利用されるものです。エラーのチェック時に軽くなっており、効率性より読みやすさを重視して設計されています。

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>`nethost.h` と `hostfxr.h` を使用してホストを作成する

以下は、`nethost` および `hostfxr` ライブラリを使用してネイティブ アプリケーションで .NET Core ランタイムを起動し、静的マネージド メソッドを呼び出す手順を詳しくまとめたものです。 [サンプル](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr)では、.NET SDK でインストールされる `nethost` ヘッダーとライブラリ、および [dotnet/runtime](https://github.com/dotnet/runtime) リポジトリからの [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/coreclr_delegates.h) および [`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/native/corehost/hostfxr.h) ファイルのコピーが使用されます。

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>ステップ 1 - `hostfxr` を読み込んで、エクスポートされたホスティング関数を取得する

`nethost` ライブラリでは、`hostfxr` ライブラリを検索するための `get_hostfxr_path` 関数が提供されています。 `hostfxr` ライブラリでは、.NET Core ランタイムをホストするための関数が公開されています。 関数の完全な一覧については、[`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/native/corehost/hostfxr.h) および[ネイティブ ホスティング デザインのドキュメント](https://github.com/dotnet/runtime/blob/master/docs/design/features/native-hosting.md)をご覧ください。 サンプルとこのチュートリアルでは以下を使います。

* `hostfxr_initialize_for_runtime_config`:ホスト コンテキストを初期化し、指定されたランタイム構成を使って .NET Core ランタイムの初期化を準備します。
* `hostfxr_get_runtime_delegate`:ランタイム機能に対するデリゲートを取得します。
* `hostfxr_close`:ホスト コンテキストを閉じます。

`hostfxr` ライブラリは、`get_hostfxr_path` を使って検索されます。 その後、読み込まれて、そのエクスポートが取得されます。

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>ステップ 2 - .NET Core ランタイムを初期化して開始する

`hostfxr_initialize_for_runtime_config` および `hostfxr_get_runtime_delegate` 関数では、後で読み込まれるマネージド コンポーネントに対するランタイム構成を使って、.NET Core ランタイムが初期化されて開始されます。 マネージド アセンブリの読み込み、およびそのアセンブリ内の静的メソッドへの関数ポインターの取得を可能にするランタイムのデリゲートを取得するには、`hostfxr_get_runtime_delegate` 関数を使います。

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>ステップ 3 - マネージド アセンブリを読み込み、マネージド メソッドへの関数ポインターを取得する

マネージド アセンブリを読み込んで、マネージド メソッドへの関数ポインターを取得するには、ランタイムのデリゲートを呼び出します。 デリゲートでは、入力としてアセンブリのパス、型の名前、およびメソッドの名前が必要であり、マネージド メソッドの呼び出しに使用できる関数ポインターが返されます。

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

ランタイムのデリゲートを呼び出すときにデリゲートの型の名前として `nullptr` を渡すことにより、サンプルではマネージド メソッドに対して既定のシグネチャを使います。

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

ランタイムのデリゲートを呼び出すときに、デリゲートの型名を指定することにより、異なるシグネチャを使用できます。

### <a name="step-4---run-managed-code"></a>ステップ 4 - マネージド コードを実行する

ネイティブ ホストでは、マネージド メソッドを呼び出し、目的のパラメーターを渡すことができます。

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>`coreclrhost.h` を使用してホストを作成する

以下は、`coreclrhost.h` API を使用してネイティブ アプリケーションで .NET Core ランタイムを起動し、静的マネージド メソッドを呼び出す手順を詳しくまとめたものです。 このドキュメントのコード スニペットでは Windows 固有の API が使用されてますが、[こちら](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)にある完全版サンプル ホストでは、Windows コード パスと Linux コード パスの両方を確認できます。

[Unix CoreRun ホスト](https://github.com/dotnet/runtime/tree/master/src/coreclr/hosts/unixcorerun)では、`coreclrhost.h` を使ったホスティングの、より複雑で現実的な例が示されています。

### <a name="step-1---find-and-load-coreclr"></a>手順 1 - CoreCLR を見つけて読み込む

.NET Core ランタイム API は *coreclr.dll* (Windows の場合)、*libcoreclr.so* (Linux の場合)、*libcoreclr.dylib* (macOS の場合) にあります。 .NET Core をホストする最初の手順は CoreCLR ライブラリを読み込むことです。 ホストによってはさまざまなパスを探るか、入力パラメーターを使用してライブラリを見つけるものもあれば、特定のパスから (ホストの隣やコンピューター全体からなど) 読み込むことが認識されているものもあります。

ライブラリが見つかると、それが `LoadLibraryEx` (Windows の場合) か `dlopen` (Linux/macOS の場合) によって読み込まれます。

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>手順 2 - .NET Core をホストする関数を取得する

CoreClrHost には、.NET Core をホストするために役立つ重要なメソッドがいくつかあります。

* `coreclr_initialize`:.NET Core ランタイムを起動し、既定 (で唯一) の AppDomain を設定します。
* `coreclr_execute_assembly`:マネージド アセンブリを実行します。
* `coreclr_create_delegate`:マネージド メソッドを指す関数ポインターを作成します。
* `coreclr_shutdown`:.NET Core ランタイムをシャットダウンします。
* `coreclr_shutdown_2`:`coreclr_shutdown` など。ただし、マネージド コードの終了コードも取得されます。

CoreCLR ライブラリを読み込んだ後、次の手順は、`GetProcAddress` (Windows の場合) または `dlsym` (Linux/macOS の場合) を使用してこれらの関数の参照を取得することです。

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>手順 3 - ランタイム プロパティを準備する

ランタイムを開始する前に、(特に、アセンブリ ローダーに関連して) 動作を指定するいくつかのプロパティを用意する必要があります。

共通プロパティには次があります。

* `TRUSTED_PLATFORM_ASSEMBLIES` これはランタイムが既定で解決できるアセンブリ パスのリストです (Windows の場合は ';' で、Linux の場合は ':' で区切られます)。 一部のホストでは、アセンブリを一覧表示するマニフェストがハードコードされており、それを読み込むことができます。 他のホストの場合、このリストにある特定の場所にライブラリが置かれます (*coreclr.dll* の隣など)。
* `APP_PATHS` これは、信頼されるプラットフォーム アセンブリ (TPA) リストでアセンブリが見つからない場合、アセンブリを探すパスのリストです。 TPA リストの場合、読み込まれるアセンブリをホスト側でより細かく制御できるため、ホストで読み込み、列挙するアセンブリを明示的に決定することがホストにとってはベスト プラクティスです。 ただし、実行時にプローブが必要な場合は、このプロパティでそのシナリオに対処できます。
* `APP_NI_PATHS` このリストは、ネイティブ イメージを探すパスであることを除き、APP_PATHS と似ています。
* `NATIVE_DLL_SEARCH_DIRECTORIES` このプロパティは、p/invoke で呼び出されたネイティブ ライブラリを探すときにローダーが調べるパスの一覧です。
* `PLATFORM_RESOURCE_ROOTS` このリストには、(カルチャ固有の下位ディレクトリで) リソース サテライト アセンブリを探すパスが含まれています。

このサンプル ホストでは、現在のディレクトリにあるすべてのライブラリを単純に列挙することで TPA リストが作成されます。

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

サンプルが単純なため、`TRUSTED_PLATFORM_ASSEMBLIES` プロパティのみを必要とします。

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>手順 4 - ランタイムを起動する

`coreclrhost.h` API により、1 回の呼び出しでランタイムの起動と既定の AppDomain の作成が行われます。 `coreclr_initialize` 関数はベース パス、名前、前述のプロパティを取得し、`hostHandle` パラメーターを介してホストにハンドルを戻します。

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>手順 5 - マネージド コードを実行する

ランタイムが起動すると、ホストではマネージド コードを呼び出せるようになります。 これにはさまざまな方法があります。 このチュートリアルにリンクされているサンプル コードでは、`coreclr_create_delegate` 関数を使用して静的マネージド メソッドのデリゲートが作成されます。 この API は、[アセンブリ名](../../standard/assembly/names.md)、名前空間で修飾された型名、メソッド名を入力として取得し、メソッドの呼び出しに使用できるデリゲートを返します。

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

このサンプルでは、これでホストは `managedDelegate` を呼び出し、`ManagedWorker.DoWork` メソッドを実行できます。

あるいは、`coreclr_execute_assembly` 関数を使用し、マネージド実行可能ファイルを起動できます。 この API は、入力パラメーターとしてアセンブリのパスと一連の引数を受け取ります。 そのパスでアセンブリを読み込み、そのメイン メソッドを呼び出します。

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>手順 6 - シャットダウンとクリーンアップ

最後になりますが、ホストでマネージド コードの実行が完了すると、.NET Core ランタイムが `coreclr_shutdown` または `coreclr_shutdown_2` でシャットダウンされます。

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR では、再初期化またはアンロードはサポートされていません。 `coreclr_initialize` を再度呼び出したり、CoreCLR ライブラリをアンロードしたりしないでください。

## <a name="conclusion"></a>まとめ

ホストがビルドされたら、テストを行うことができます。コマンド ラインから実行し、ホストで想定される引数を渡します。 実行するホストの .NET Core アプリを指定するとき、`dotnet build` により生成された .dll を使用してください。 自己完結型アプリケーションのために `dotnet publish` で生成された実行可能ファイル (.exe ファイル) が実質的に既定の .NET Core ホストになります (メインライン シナリオでコマンド ラインから直接、アプリを起動できるように)。ユーザー コードがコンパイルされ、同じ名前の dll が作られます。

最初の実行で動作しなかった場合、ホストが期待している場所に *coreclr.dll* があること、必要なすべての Framework ライブラリが TPA 一覧にあること、CoreCLR のビット数 (32 ビットまたは 64 ビット) がホストのビルド方法に一致することをもう一度確認してください。

.NET Core ランタイムのホスティングは、多くの開発者が必要としない高度なシナリオですが、ネイティブ プロセスからマネージド コードを起動する場合や .NET Core ランタイムの動作をより細かくコントロールする場合、非常に便利です。
