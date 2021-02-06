---
description: '詳細情報: <runtime> 要素'
title: <runtime> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: eeffc8de4eeb6fb53ef3829b8c5b078be4cee83a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652771"
---
# <a name="runtime-element"></a><span data-ttu-id="c0264-103">\<runtime> 要素</span><span class="sxs-lookup"><span data-stu-id="c0264-103">\<runtime> Element</span></span>

<span data-ttu-id="c0264-104">アプリケーションを構成するために共通言語ランタイムによって使用される情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c0264-104">Provides information used by the common language runtime to configure applications.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a><span data-ttu-id="c0264-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0264-105">Syntax</span></span>

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0264-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c0264-106">Attributes and Elements</span></span>

<span data-ttu-id="c0264-107">次のセクションでは、子要素と親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0264-107">The following sections describe child elements and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0264-108">属性</span><span class="sxs-lookup"><span data-stu-id="c0264-108">Attributes</span></span>

<span data-ttu-id="c0264-109">なし。</span><span class="sxs-lookup"><span data-stu-id="c0264-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0264-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c0264-110">Child Elements</span></span>

|<span data-ttu-id="c0264-111">要素</span><span class="sxs-lookup"><span data-stu-id="c0264-111">Element</span></span>|<span data-ttu-id="c0264-112">説明</span><span class="sxs-lookup"><span data-stu-id="c0264-112">Description</span></span>|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="c0264-113">偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-113">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="c0264-114"><xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。</span><span class="sxs-lookup"><span data-stu-id="c0264-114">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="c0264-115">プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-115">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="c0264-116">既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの役割を果たす種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-116">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="c0264-117">プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="c0264-117">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="c0264-118">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c0264-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="c0264-119">信頼されたアセンブリに対する厳密な名前の検証をバイパスするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-119">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="c0264-120">文字列比較を実行するときに、ランタイムが従来の並べ替え動作を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-120">Specifies that the runtime should use legacy sorting behavior when performing string comparisons.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="c0264-121">DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-121">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="c0264-122">バインディングエラーのキャッシュ (.NET Framework バージョン2.0 での既定の動作) を無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-122">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="c0264-123">スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-123">Specifies whether the full thread stack is committed when a thread is started.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="c0264-124">アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドする既定の動作を無効化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-124">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="c0264-125">日付と時刻の解析メソッドが、日、月、時間、および午前/午後のみを含む日付の文字列を解析するように調整されたルールのセットを使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-125">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="c0264-126">暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-126">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="c0264-127">共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-127">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="c0264-128">PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-128">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="c0264-129">64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c0264-129">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="c0264-130">共通言語ランタイムがガベージコレクションを同時に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-130">Specifies whether the common language runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="c0264-131">ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-131">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="c0264-132">ガベージコレクションヒープと個々のプロセッサ間の関係を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0264-132">Defines the affinity between garbage collection heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="c0264-133">サーバーのガベージコレクションに使用するヒープまたはスレッドの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-133">Specifies the number of heaps/threads to use for server garbage collection.</span></span>|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="c0264-134">ガベージコレクターが大きなオブジェクトヒープにオブジェクトを配置するしきい値のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-134">Specifies the threshold size that causes the garbage collector to put objects on the large object heap.</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="c0264-135">Cpu を使用してサーバーガベージコレクションスレッドを関係付けするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-135">Specifies whether or not to affinitize server garbage collection threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="c0264-136">共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-136">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="c0264-137">ランタイムがコード アクセス セキュリティ (CAS) の発行元ポリシーを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-137">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="c0264-138">ランタイムがアクセス違反およびその他の破損状態例外をキャッチするマネージド コードを許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-138">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="c0264-139">Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-139">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="c0264-140">リモート ソースからのアセンブリを完全な信頼として読み込むかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-140">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="c0264-141">ランタイムがレガシ コード アクセス セキュリティ (CAS) ポリシーを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-141">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="c0264-142">ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージド コードとアンマネージド コード間の遷移が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="c0264-142">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="c0264-143">ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-143">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="c0264-144">ランタイムが、アプリケーション ドメインの境界間のリモート処理ではなく COM 相互運用を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-144">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="c0264-145">サテライト アセンブリのプローブを最適化します。</span><span class="sxs-lookup"><span data-stu-id="c0264-145">Optimizes the probe for satellite assemblies.</span></span>|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="c0264-146">シャドウコピーで .NET Framework 4 で導入された既定の起動動作を使用するか、以前のバージョンの .NET Framework の起動動作に戻すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-146">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="c0264-147">.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="c0264-147">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="c0264-148">既定のメモリ内オブジェクト キャッシュの構成情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c0264-148">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="c0264-149">ランタイムによって、すべての CPU グループにマネージド スレッドを分散するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-149">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="c0264-150">タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-150">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|<span data-ttu-id="c0264-151">ランタイムで <xref:System.TimeSpan> の値に従来の書式を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-151">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="c0264-152">共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-152">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="c0264-153">ランタイムがアプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0264-153">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="c0264-154">ランタイムが内部的に使用する特定のスレッド作成時に、既定のスタック サイズではなく明示的なスタック サイズを使用することを要求します。</span><span class="sxs-lookup"><span data-stu-id="c0264-154">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0264-155">親要素</span><span class="sxs-lookup"><span data-stu-id="c0264-155">Parent Elements</span></span>

|<span data-ttu-id="c0264-156">要素</span><span class="sxs-lookup"><span data-stu-id="c0264-156">Element</span></span>|<span data-ttu-id="c0264-157">説明</span><span class="sxs-lookup"><span data-stu-id="c0264-157">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c0264-158">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c0264-158">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0264-159">解説</span><span class="sxs-lookup"><span data-stu-id="c0264-159">Remarks</span></span>

<span data-ttu-id="c0264-160">[\<runtime>](runtime-element.md)構成ファイルのセクションの子要素は、アプリケーションの実行方法を構成するために共通言語ランタイムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0264-160">The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes.</span></span> <span data-ttu-id="c0264-161">たとえば、要素は、 [\<gcServer>](gcserver-element.md) ガベージコレクターがワークステーションのガベージコレクションまたはサーバーのガベージコレクションを使用するかどうかを決定します。要素は、 [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) 共通言語ランタイムが、アプリケーションごとに、またはアプリケーションドメインごとに文字列のハッシュコードを計算するかどうかを決定し `AppContextSwitchOverrides` ます</span><span class="sxs-lookup"><span data-stu-id="c0264-161">For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.</span></span>

<span data-ttu-id="c0264-162">セクションの要素は、 [\<runtime>](runtime-element.md) アプリケーションの起動時に共通言語ランタイムによって自動的に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="c0264-162">The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup.</span></span> <span data-ttu-id="c0264-163">既定以外のアプリケーションドメインの構成ファイルは、プロパティに名前を指定することによって定義することもできます <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> 。アプリケーションドメインが読み込まれると、その設定が自動的に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="c0264-163">You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded.</span></span> <span data-ttu-id="c0264-164">ほとんどの場合、 [\<runtime>](runtime-element.md) アプリケーションの構成ファイルのセクションで設定を直接読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0264-164">You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0264-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0264-165">See also</span></span>

- [<span data-ttu-id="c0264-166">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c0264-166">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0264-167">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c0264-167">Configuration File Schema</span></span>](../index.md)
