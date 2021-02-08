---
description: '詳細情報: アンマネージ API リファレンス'
title: アンマネージ API リファレンス
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: 3c9c485d8dced9641d0d1af850de190318902aa9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678992"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="a5099-103">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="a5099-103">Unmanaged API Reference</span></span>

<span data-ttu-id="a5099-104">このセクションには、ランタイム ホスト、コンパイラ、逆アセンブラー、難読化ツール、デバッガー、プロファイラーなど、マネージ コード関連のアプリケーションが使用できるアンマネージ API に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5099-104">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5099-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a5099-105">In This Section</span></span>  

 [<span data-ttu-id="a5099-106">共有のデータ型</span><span class="sxs-lookup"><span data-stu-id="a5099-106">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="a5099-107">特にアンマネージ プロファイリング API とデバッギング API で使用される一般的なデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="a5099-107">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="a5099-108">ALink</span><span class="sxs-lookup"><span data-stu-id="a5099-108">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="a5099-109">ALink API について説明します。この API は .NET Framework アセンブリおよび非バインド モジュールの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a5099-109">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="a5099-110">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a5099-110">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="a5099-111">Authenticode XrML ライセンスの作成および検証モジュールをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a5099-111">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="a5099-112">定数</span><span class="sxs-lookup"><span data-stu-id="a5099-112">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="a5099-113">CorSym.idl で定義される定数について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5099-113">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="a5099-114">[カスタム インターフェイス属性](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a5099-114">[Custom Interface Attributes](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="a5099-115">コンポーネント オブジェクト モデル (COM) のカスタム インターフェイス属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5099-115">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="a5099-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a5099-116">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="a5099-117">デバッグ API について説明します。これによりデバッガーは、共通言語ランタイム (CLR) 環境で実行するコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="a5099-117">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="a5099-118">シンボル ストア診断</span><span class="sxs-lookup"><span data-stu-id="a5099-118">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="a5099-119">シンボル ストア診断 API について説明します。これによりコンパイラは、デバッガーが使用するためのシンボル情報を生成できます。</span><span class="sxs-lookup"><span data-stu-id="a5099-119">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="a5099-120">Fusion</span><span class="sxs-lookup"><span data-stu-id="a5099-120">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="a5099-121">Fusion API について説明します。これによりランタイム ホストは、アプリケーションに対するリソースの正しいバージョンを見つけるために、アプリケーションのリソースのプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a5099-121">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="a5099-122">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a5099-122">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="a5099-123">ホスト API について説明します。これにより、アンマネージ ホストが CLR をホストのアプリケーションに統合できます。</span><span class="sxs-lookup"><span data-stu-id="a5099-123">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="a5099-124">メタデータ</span><span class="sxs-lookup"><span data-stu-id="a5099-124">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="a5099-125">メタデータ API について説明します。これによりコンパイラなどのクライアントは、CLR によって読み込まれる型を使用せずに、コンポーネントのメタデータを生成したり、メタデータにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="a5099-125">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="a5099-126">プロファイル</span><span class="sxs-lookup"><span data-stu-id="a5099-126">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="a5099-127">プロファイル API について説明します。これによりプロファイラーは CLR によるプログラムの実行を監視できます。</span><span class="sxs-lookup"><span data-stu-id="a5099-127">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="a5099-128">厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="a5099-128">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="a5099-129">厳密な名前付け API について説明します。これによりクライアントは、アセンブリに対する厳密な名前の署名を管理できます。</span><span class="sxs-lookup"><span data-stu-id="a5099-129">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="a5099-130">WMI およびパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="a5099-130">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="a5099-131">Windows Management Instrumentation (WMI) ライブラリへの呼び出しをラッピングするAPI について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5099-131">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="a5099-132">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="a5099-132">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="a5099-133">タイプ ライブラリ エクスポーター (Tlbexp.exe) がアセンブリからタイプ ライブラリへの変換プロセス中に使用する、2 つのヘルパー関数とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5099-133">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a5099-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5099-134">Related Sections</span></span>  

 [<span data-ttu-id="a5099-135">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="a5099-135">Development Guide</span></span>](../development-guide.md)
