---
description: '詳細情報: STARTUP_FLAGS 列挙型'
title: STARTUP_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
ms.openlocfilehash: 2136f1c43545342f2cdc7cde884999a2f2c11bdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679343"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="99e67-103">STARTUP_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="99e67-103">STARTUP_FLAGS Enumeration</span></span>

<span data-ttu-id="99e67-104">共通言語ランタイム (CLR: Common Language Runtime) の起動動作を示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="99e67-104">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="99e67-105">既定では、ガベージ コレクションは非同時実行で、基底クラス ライブラリだけがドメイン中立領域に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="99e67-105">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e67-106">構文</span><span class="sxs-lookup"><span data-stu-id="99e67-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="99e67-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="99e67-107">Members</span></span>  
  
|<span data-ttu-id="99e67-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="99e67-108">Member</span></span>|<span data-ttu-id="99e67-109">説明</span><span class="sxs-lookup"><span data-stu-id="99e67-109">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="99e67-110">同時実行ガベージ コレクションを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-110">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="99e67-111">呼び出し元がサーバー ビルドと同時実行ガベージ コレクションをシングル プロセッサ コンピューター上で要求した場合は、代わりにワークステーション ビルドと非同時実行ガベージ コレクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="99e67-111">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="99e67-112">**注:**  同時実行ガベージコレクションは、Intel Itanium アーキテクチャ (旧称 IA-64) を実装する64ビットシステムで WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="99e67-112">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="99e67-113">64ビット Windows システムでの WOW64 の使用の詳細については、「 [32 ビットアプリケーションの実行](/windows/desktop/WinProg64/running-32-bit-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e67-113">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="99e67-114">ローダーの最適化を行う必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-114">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="99e67-115">どのアセンブリもドメイン中立として読み込まないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-115">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="99e67-116">すべてのアセンブリをドメイン中立として読み込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-116">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="99e67-117">厳密な名前を付けられたすべてのアセンブリをドメイン中立として読み込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-117">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="99e67-118">CLR バージョン ポリシーが、渡されたバージョンに適用されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-118">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="99e67-119">指定された CLR のバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="99e67-119">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="99e67-120">シムは、互換性のある最新バージョンを決めるためのポリシーの評価を実行しません。</span><span class="sxs-lookup"><span data-stu-id="99e67-120">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="99e67-121">推奨ランタイムを設定するように指定しますが、実際には起動されません。</span><span class="sxs-lookup"><span data-stu-id="99e67-121">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="99e67-122">サーバー ガベージ コレクションを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-122">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="99e67-123">ガベージ コレクションで、使用された仮想アドレスを保持することを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-123">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="99e67-124">ホスト インターフェイスの混合を許可しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-124">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="99e67-125">既定として偽装が非同期ポイント間をフローしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-125">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="99e67-126">スレッドが実行を開始するときにスレッド スタック全体をコミットしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-126">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="99e67-127">マネージド偽装およびプラットフォーム呼び出しによって実行された偽装が非同期ポイント間をフローするように指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-127">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="99e67-128">既定では、マネージド偽装だけが非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="99e67-128">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="99e67-129">システム メモリが少ないときに、ガベージ コレクションによるコミットされた領域の使用量を抑えることを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-129">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="99e67-130">`gcTrimCommitOnLowMemory`[共有 Web ホスティングの最適化](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md)については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e67-130">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="99e67-131">共通言語ランタイム イベントで Windows イベント トレーシング (ETW) が有効になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-131">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="99e67-132">Windows Vista 以降、イベント トレーシングは常に有効になっているため、このフラグの効果はありません。</span><span class="sxs-lookup"><span data-stu-id="99e67-132">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="99e67-133">「 [.NET Framework のログ記録の制御](../../performance/controlling-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e67-133">See [Controlling .NET Framework Logging](../../performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="99e67-134">アプリケーション ドメインのリソース監視が有効になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="99e67-134">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="99e67-135"><xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>プロパティと[ \<appDomainResourceMonitoring> 要素](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e67-135">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99e67-136">要件</span><span class="sxs-lookup"><span data-stu-id="99e67-136">Requirements</span></span>  

 <span data-ttu-id="99e67-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99e67-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99e67-138">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="99e67-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99e67-139">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99e67-139">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99e67-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99e67-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e67-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="99e67-141">See also</span></span>

- [<span data-ttu-id="99e67-142">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="99e67-142">Hosting Enumerations</span></span>](hosting-enumerations.md)
