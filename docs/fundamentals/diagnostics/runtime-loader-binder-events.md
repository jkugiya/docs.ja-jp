---
title: ローダーおよびバインダー ランタイム イベント
description: アセンブリ ローダーとバインダーに関する情報を収集するローダーおよびバインダー ETW イベントに固有の診断情報を収集する .NET ランタイム イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594109"
---
# <a name="net-runtime-loader-and-binder-events"></a><span data-ttu-id="57e36-103">.NET ランタイム ローダーとバインダー イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-103">.NET runtime loader and binder events</span></span>

<span data-ttu-id="57e36-104">これらのイベントは、アセンブリ、およびモジュールのロードとアンロードに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="57e36-104">These events collect information relating to loading and unloading assemblies and modules.</span></span> <span data-ttu-id="57e36-105">診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e36-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

|<span data-ttu-id="57e36-106">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-106">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-107">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-107">Event</span></span>|<span data-ttu-id="57e36-108">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-108">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-109">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-109">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-110">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-110">Informational (4)</span></span>|

|<span data-ttu-id="57e36-111">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-111">Event</span></span>|<span data-ttu-id="57e36-112">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-112">Event ID</span></span>|<span data-ttu-id="57e36-113">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-113">Description</span></span>|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-114">151</span><span class="sxs-lookup"><span data-stu-id="57e36-114">151</span></span>|<span data-ttu-id="57e36-115">モジュールがアプリケーション ドメインに読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="57e36-115">Raised when a module is loaded for an application domain.</span></span>|

## <a name="moduleload_v2-event"></a><span data-ttu-id="57e36-116">ModuleLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-116">ModuleLoad_V2 event</span></span>

|<span data-ttu-id="57e36-117">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-117">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-118">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-118">Event</span></span>|<span data-ttu-id="57e36-119">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-119">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-120">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-120">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-121">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-121">Informational (4)</span></span>|

|<span data-ttu-id="57e36-122">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-122">Event</span></span>|<span data-ttu-id="57e36-123">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-123">Event ID</span></span>|<span data-ttu-id="57e36-124">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-124">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|<span data-ttu-id="57e36-125">152</span><span class="sxs-lookup"><span data-stu-id="57e36-125">152</span></span>|<span data-ttu-id="57e36-126">プロセスの有効期間中にモジュールが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="57e36-126">Raised when a module is loaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="57e36-127">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-127">Field name</span></span>|<span data-ttu-id="57e36-128">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-128">Data type</span></span>|<span data-ttu-id="57e36-129">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-129">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="57e36-130">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-130">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-131">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-131">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="57e36-132">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-132">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="57e36-133">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-133">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-134">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-134">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="57e36-135">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-135">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="57e36-136">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="57e36-136">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="57e36-137">モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="57e36-137">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="57e36-138">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="57e36-138">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-139">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="57e36-140">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="57e36-140">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="57e36-141">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="57e36-141">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-142">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-142">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="57e36-143">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-143">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="57e36-144">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-144">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="57e36-145">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-145">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-146">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-146">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="57e36-147">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-147">In some cases, this may just be a file name.</span></span>|

## <a name="moduleunload_v2-event"></a><span data-ttu-id="57e36-148">ModuleUnload_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-148">ModuleUnload_V2 event</span></span>

|<span data-ttu-id="57e36-149">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-149">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-150">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-150">Event</span></span>|<span data-ttu-id="57e36-151">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-151">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-152">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-152">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-153">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-153">Informational (4)</span></span>|

|<span data-ttu-id="57e36-154">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-154">Event</span></span>|<span data-ttu-id="57e36-155">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-155">Event ID</span></span>|<span data-ttu-id="57e36-156">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-156">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|<span data-ttu-id="57e36-157">153</span><span class="sxs-lookup"><span data-stu-id="57e36-157">153</span></span>|<span data-ttu-id="57e36-158">プロセスの有効期間中にモジュールがアンロードされるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="57e36-158">Raised when a module is unloaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="57e36-159">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-159">Field name</span></span>|<span data-ttu-id="57e36-160">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-160">Data type</span></span>|<span data-ttu-id="57e36-161">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-161">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="57e36-162">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-162">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-163">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-163">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="57e36-164">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-164">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="57e36-165">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-165">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-166">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-166">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="57e36-167">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-167">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="57e36-168">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="57e36-168">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="57e36-169">モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="57e36-169">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="57e36-170">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="57e36-170">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|``win:UInt16``|<span data-ttu-id="57e36-171">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-171">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="57e36-172">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="57e36-172">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="57e36-173">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="57e36-173">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-174">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-174">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="57e36-175">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-175">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="57e36-176">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-176">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="57e36-177">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-177">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-178">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-178">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="57e36-179">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-179">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcstart_v2-event"></a><span data-ttu-id="57e36-180">ModuleDCStart_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-180">ModuleDCStart_V2 event</span></span>

|<span data-ttu-id="57e36-181">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-181">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-182">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-182">Event</span></span>|<span data-ttu-id="57e36-183">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-183">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-184">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-184">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-185">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-185">Informational (4)</span></span>

|<span data-ttu-id="57e36-186">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-186">Event</span></span>|<span data-ttu-id="57e36-187">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-187">Event ID</span></span>|<span data-ttu-id="57e36-188">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-188">Description</span></span>
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|<span data-ttu-id="57e36-189">153</span><span class="sxs-lookup"><span data-stu-id="57e36-189">153</span></span>|<span data-ttu-id="57e36-190">開始ランダウン中にモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="57e36-190">Enumerates modules during a start rundown.</span></span>|

|<span data-ttu-id="57e36-191">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-191">Field name</span></span>|<span data-ttu-id="57e36-192">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-192">Data type</span></span>|<span data-ttu-id="57e36-193">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-193">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="57e36-194">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-194">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-195">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-195">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="57e36-196">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-196">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="57e36-197">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-197">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-198">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-198">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="57e36-199">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-199">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="57e36-200">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="57e36-200">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="57e36-201">モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="57e36-201">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="57e36-202">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="57e36-202">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-203">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="57e36-204">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="57e36-204">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="57e36-205">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="57e36-205">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-206">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-206">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="57e36-207">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-207">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="57e36-208">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-208">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="57e36-209">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-209">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-210">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-210">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="57e36-211">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-211">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcend_v2-event"></a><span data-ttu-id="57e36-212">ModuleDCEnd_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-212">ModuleDCEnd_V2 event</span></span>

|<span data-ttu-id="57e36-213">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-213">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-214">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-214">Event</span></span>|<span data-ttu-id="57e36-215">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-215">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-216">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-216">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-217">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-217">Informational (4)</span></span>|

|<span data-ttu-id="57e36-218">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-218">Event</span></span>|<span data-ttu-id="57e36-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-219">Event ID</span></span>|<span data-ttu-id="57e36-220">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-220">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|<span data-ttu-id="57e36-221">154</span><span class="sxs-lookup"><span data-stu-id="57e36-221">154</span></span>|<span data-ttu-id="57e36-222">終了ランダウン中にモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="57e36-222">Enumerates modules during an end rundown.</span></span>|

|<span data-ttu-id="57e36-223">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-223">Field name</span></span>|<span data-ttu-id="57e36-224">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-224">Data type</span></span>|<span data-ttu-id="57e36-225">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-225">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="57e36-226">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-226">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-227">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-227">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="57e36-228">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-228">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="57e36-229">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-229">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-230">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-230">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="57e36-231">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="57e36-231">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="57e36-232">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="57e36-232">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="57e36-233">モジュールの Common Intermediate Language (CIL) のイメージのパス、またはそれが動的アセンブリ (null で終わる) である場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="57e36-233">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="57e36-234">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="57e36-234">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-235">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="57e36-236">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="57e36-236">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="57e36-237">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="57e36-237">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-238">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-238">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="57e36-239">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-239">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="57e36-240">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-240">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="57e36-241">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-241">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="57e36-242">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="57e36-242">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="57e36-243">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="57e36-243">In some cases, this may just be a file name.</span></span>|

## <a name="assemblyload_v1-event"></a><span data-ttu-id="57e36-244">AssemblyLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-244">AssemblyLoad_V1 event</span></span>

|<span data-ttu-id="57e36-245">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-245">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-246">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-246">Event</span></span>|<span data-ttu-id="57e36-247">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-247">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-248">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-248">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-249">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-249">Informational (4)</span></span>|

|<span data-ttu-id="57e36-250">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-250">Event</span></span>|<span data-ttu-id="57e36-251">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-251">Event ID</span></span>|<span data-ttu-id="57e36-252">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-252">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|<span data-ttu-id="57e36-253">154</span><span class="sxs-lookup"><span data-stu-id="57e36-253">154</span></span>|<span data-ttu-id="57e36-254">アセンブリが読み込まれたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="57e36-254">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="57e36-255">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-255">Field name</span></span>|<span data-ttu-id="57e36-256">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-256">Data type</span></span>|<span data-ttu-id="57e36-257">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-257">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-258">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-258">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="57e36-259">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-259">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="57e36-260">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-260">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="57e36-261">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-261">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="57e36-262">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-262">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="57e36-263">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-263">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-264">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-264">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-265">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="57e36-265">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-266">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-266">Unique ID for the instance of CoreCLR.</span></span>

## <a name="assemblyunload_v1-event"></a><span data-ttu-id="57e36-267">AssemblyUnload_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-267">AssemblyUnload_V1 event</span></span>

|<span data-ttu-id="57e36-268">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-268">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-269">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-269">Event</span></span>|<span data-ttu-id="57e36-270">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-270">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-271">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-271">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-272">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-272">Informational (4)</span></span>|

|<span data-ttu-id="57e36-273">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-273">Event</span></span>|<span data-ttu-id="57e36-274">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-274">Event ID</span></span>|<span data-ttu-id="57e36-275">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-275">Description</span></span>|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|<span data-ttu-id="57e36-276">155</span><span class="sxs-lookup"><span data-stu-id="57e36-276">155</span></span>|<span data-ttu-id="57e36-277">アセンブリが読み込まれたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="57e36-277">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="57e36-278">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-278">Field name</span></span>|<span data-ttu-id="57e36-279">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-279">Data type</span></span>|<span data-ttu-id="57e36-280">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-280">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-281">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-281">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="57e36-282">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-282">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="57e36-283">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-283">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="57e36-284">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-284">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="57e36-285">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-285">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="57e36-286">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-286">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-287">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-287">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-288">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="57e36-288">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-289">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-289">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblydcstart_v1-event"></a><span data-ttu-id="57e36-290">AssemblyDCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-290">AssemblyDCStart_V1 event</span></span>

|<span data-ttu-id="57e36-291">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-291">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-292">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-292">Event</span></span>|<span data-ttu-id="57e36-293">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-293">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-294">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="57e36-294">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="57e36-295">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-295">Informational (4)</span></span>|

|<span data-ttu-id="57e36-296">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-296">Event</span></span>|<span data-ttu-id="57e36-297">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-297">Event ID</span></span>|<span data-ttu-id="57e36-298">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-298">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|<span data-ttu-id="57e36-299">155</span><span class="sxs-lookup"><span data-stu-id="57e36-299">155</span></span>|<span data-ttu-id="57e36-300">開始ランダウン中にアセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="57e36-300">Enumerates assemblies during a start rundown.</span></span>|

|<span data-ttu-id="57e36-301">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-301">Field name</span></span>|<span data-ttu-id="57e36-302">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-302">Data type</span></span>|<span data-ttu-id="57e36-303">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-303">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="57e36-304">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-304">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="57e36-305">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-305">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="57e36-306">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-306">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="57e36-307">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-307">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="57e36-308">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-308">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="57e36-309">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="57e36-309">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="57e36-310">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-310">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-311">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="57e36-311">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-312">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-312">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstart-event"></a><span data-ttu-id="57e36-313">AssemblyLoadStart イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-313">AssemblyLoadStart event</span></span>

|<span data-ttu-id="57e36-314">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-314">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-315">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-315">Event</span></span>|<span data-ttu-id="57e36-316">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-316">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-317">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-317">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="57e36-318">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-318">Informational (4)</span></span>|

|<span data-ttu-id="57e36-319">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-319">Event</span></span>|<span data-ttu-id="57e36-320">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-320">Event ID</span></span>|<span data-ttu-id="57e36-321">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-321">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="57e36-322">290</span><span class="sxs-lookup"><span data-stu-id="57e36-322">290</span></span>|<span data-ttu-id="57e36-323">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="57e36-323">An assembly load has been requested.</span></span>

|<span data-ttu-id="57e36-324">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-324">Field name</span></span>|<span data-ttu-id="57e36-325">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-325">Data type</span></span>|<span data-ttu-id="57e36-326">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-326">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-327">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-327">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-328">アセンブリ名のパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-328">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="57e36-329">要求している ("親") アセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-329">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-330">アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-330">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-331">要求している ("親") アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-331">Load context of the requesting ("parent") assembly.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-332">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-332">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstop-event"></a><span data-ttu-id="57e36-333">AssemblyLoadStop イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-333">AssemblyLoadStop event</span></span>

|<span data-ttu-id="57e36-334">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-334">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-335">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-335">Event</span></span>|<span data-ttu-id="57e36-336">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-336">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-337">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-337">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="57e36-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-338">Informational (4)</span></span>|

|<span data-ttu-id="57e36-339">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-339">Event</span></span>|<span data-ttu-id="57e36-340">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-340">Event ID</span></span>|<span data-ttu-id="57e36-341">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-341">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="57e36-342">291</span><span class="sxs-lookup"><span data-stu-id="57e36-342">291</span></span>|<span data-ttu-id="57e36-343">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="57e36-343">An assembly load has been requested.</span></span>

|<span data-ttu-id="57e36-344">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-344">Field name</span></span>|<span data-ttu-id="57e36-345">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-345">Data type</span></span>|<span data-ttu-id="57e36-346">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-346">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-347">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-347">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-348">アセンブリ名のパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-348">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="57e36-349">要求している ("親") アセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-349">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-350">アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-350">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-351">要求している ("親") アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-351">Load context of the requesting ("parent") assembly.</span></span>|
|`Success`|`win:Boolean`|<span data-ttu-id="57e36-352">アセンブリの読み込みが成功したかどうか。</span><span class="sxs-lookup"><span data-stu-id="57e36-352">Whether the assembly load succeeded.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-353">読み込まれたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-353">The name of assembly that was loaded.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-354">読み込まれたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-354">The path of the assembly that was loaded from.</span></span>|
|`Cached`|`win:UnicodeString`|<span data-ttu-id="57e36-355">読み込みがキャッシュされたかどうか。</span><span class="sxs-lookup"><span data-stu-id="57e36-355">Whether the load was cached.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-356">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-356">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="resolutionattempted-event"></a><span data-ttu-id="57e36-357">ResolutionAttempted イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-357">ResolutionAttempted event</span></span>

|<span data-ttu-id="57e36-358">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-358">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-359">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-359">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-360">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-360">`Binder` (0x4)</span></span>|<span data-ttu-id="57e36-361">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-361">Informational (4)</span></span>|

|<span data-ttu-id="57e36-362">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-362">Event</span></span>|<span data-ttu-id="57e36-363">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-363">Event ID</span></span>|<span data-ttu-id="57e36-364">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-364">Description</span></span>|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|<span data-ttu-id="57e36-365">292</span><span class="sxs-lookup"><span data-stu-id="57e36-365">292</span></span>|<span data-ttu-id="57e36-366">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="57e36-366">An assembly load has been requested.</span></span>

|<span data-ttu-id="57e36-367">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-367">Field name</span></span>|<span data-ttu-id="57e36-368">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-368">Data type</span></span>|<span data-ttu-id="57e36-369">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-369">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-370">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-370">Name of assembly name.</span></span>|
|`Stage`|`win:UInt16`|<span data-ttu-id="57e36-371">解決段階。</span><span class="sxs-lookup"><span data-stu-id="57e36-371">The resolution stage.</span></span><br/><br/><span data-ttu-id="57e36-372">0: 読み込み中の検索。</span><span class="sxs-lookup"><span data-stu-id="57e36-372">0: Find in load.</span></span><br/><br/><span data-ttu-id="57e36-373">1: アセンブリの読み込みコンテキスト</span><span class="sxs-lookup"><span data-stu-id="57e36-373">1: Assembly Load Context</span></span></br><br/><span data-ttu-id="57e36-374">2: アプリケーション アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-374">2: Application assemblies.</span></span><br/><br/><span data-ttu-id="57e36-375">3: 既定のアセンブリ読み込みコンテキストのフォールバック。</span><span class="sxs-lookup"><span data-stu-id="57e36-375">3: Default assembly load context fallback.</span></span> <br/><br/><span data-ttu-id="57e36-376">4: サテライト アセンブリの解決。</span><span class="sxs-lookup"><span data-stu-id="57e36-376">4: Resolve satellite assembly.</span></span> <br/><br/><span data-ttu-id="57e36-377">5: アセンブリの読み込みコンテキストの解決中。</span><span class="sxs-lookup"><span data-stu-id="57e36-377">5: Assembly load context resolving.</span></span><br/><br/><span data-ttu-id="57e36-378">6: AppDomain アセンブリの解決中。</span><span class="sxs-lookup"><span data-stu-id="57e36-378">6: AppDomain assembly resolving.</span></span>
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-379">アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-379">Load context of the assembly.</span></span>|
|`Result`|`win:UInt16`|<span data-ttu-id="57e36-380">解決の試行結果。</span><span class="sxs-lookup"><span data-stu-id="57e36-380">The result of resolution attempt.</span></span><br/><br/><span data-ttu-id="57e36-381">0: 成功</span><span class="sxs-lookup"><span data-stu-id="57e36-381">0: Success</span></span><br/><br/><span data-ttu-id="57e36-382">1: アセンブリ非検出</span><span class="sxs-lookup"><span data-stu-id="57e36-382">1: Assembly NotFound</span></span><br/><br/><span data-ttu-id="57e36-383">2: 互換性のないバージョン</span><span class="sxs-lookup"><span data-stu-id="57e36-383">2: Incompatible Version</span></span><br/><br/><span data-ttu-id="57e36-384">3: アセンブリ名不一致</span><span class="sxs-lookup"><span data-stu-id="57e36-384">3: Mismatched Assembly Name</span></span><br/><br/><span data-ttu-id="57e36-385">4: 失敗</span><span class="sxs-lookup"><span data-stu-id="57e36-385">4: Failure</span></span><br/><br/><span data-ttu-id="57e36-386">5: 例外</span><span class="sxs-lookup"><span data-stu-id="57e36-386">5: Exception</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-387">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-387">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-388">解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-388">The path of the assembly that was resolved from.</span></span>|
|`ErrorMessage`|`win:UnicodeString`|<span data-ttu-id="57e36-389">例外が発生した場合のエラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="57e36-389">Error message if there is an exception.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-390">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-390">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a><span data-ttu-id="57e36-391">AssemblyLoadContextResolvingHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-391">AssemblyLoadContextResolvingHandlerInvoked event</span></span>

|<span data-ttu-id="57e36-392">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-392">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-393">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-393">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-394">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-394">`Binder` (0x4)</span></span>|<span data-ttu-id="57e36-395">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-395">Informational (4)</span></span>|

|<span data-ttu-id="57e36-396">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-396">Event</span></span>|<span data-ttu-id="57e36-397">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-397">Event ID</span></span>|<span data-ttu-id="57e36-398">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-398">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|<span data-ttu-id="57e36-399">293</span><span class="sxs-lookup"><span data-stu-id="57e36-399">293</span></span>|<span data-ttu-id="57e36-400">[AssemblyLoadContext.Resolving](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) ハンドラーが呼び出された。</span><span class="sxs-lookup"><span data-stu-id="57e36-400">An [AssemblyLoadContext.Resolving](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) handler has been invoked.</span></span>|

|<span data-ttu-id="57e36-401">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-401">Field name</span></span>|<span data-ttu-id="57e36-402">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-402">Data type</span></span>|<span data-ttu-id="57e36-403">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-403">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-404">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-404">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="57e36-405">呼び出されたハンドラーの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-405">Name of the handler invoked.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="57e36-406">アセンブリの読み込みコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e36-406">Load context of the assembly.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-407">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-407">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-408">解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-408">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-409">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-409">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a><span data-ttu-id="57e36-410">AppDomainAssemblyResolveHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-410">AppDomainAssemblyResolveHandlerInvoked event</span></span>

|<span data-ttu-id="57e36-411">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-411">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-412">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-412">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-413">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-413">`Binder` (0x4)</span></span>|<span data-ttu-id="57e36-414">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-414">Informational (4)</span></span>|

|<span data-ttu-id="57e36-415">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-415">Event</span></span>|<span data-ttu-id="57e36-416">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-416">Event ID</span></span>|<span data-ttu-id="57e36-417">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-417">Description</span></span>|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|<span data-ttu-id="57e36-418">294</span><span class="sxs-lookup"><span data-stu-id="57e36-418">294</span></span>|<span data-ttu-id="57e36-419"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> ハンドラーが呼び出された。</span><span class="sxs-lookup"><span data-stu-id="57e36-419">An <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="57e36-420">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-420">Field name</span></span>|<span data-ttu-id="57e36-421">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-421">Data type</span></span>|<span data-ttu-id="57e36-422">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-422">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-423">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-423">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="57e36-424">呼び出されたハンドラーの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-424">Name of the handler invoked.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-425">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-425">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-426">解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-426">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-427">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-427">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a><span data-ttu-id="57e36-428">AssemblyLoadFromResolveHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-428">AssemblyLoadFromResolveHandlerInvoked event</span></span>

|<span data-ttu-id="57e36-429">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-429">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-430">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-430">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-431">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-431">`Binder` (0x4)</span></span>|<span data-ttu-id="57e36-432">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-432">Informational (4)</span></span>|

|<span data-ttu-id="57e36-433">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-433">Event</span></span>|<span data-ttu-id="57e36-434">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-434">Event ID</span></span>|<span data-ttu-id="57e36-435">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-435">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|<span data-ttu-id="57e36-436">295</span><span class="sxs-lookup"><span data-stu-id="57e36-436">295</span></span>|<span data-ttu-id="57e36-437"><xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ハンドラーが呼び出された。</span><span class="sxs-lookup"><span data-stu-id="57e36-437">An <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="57e36-438">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-438">Field name</span></span>|<span data-ttu-id="57e36-439">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-439">Data type</span></span>|<span data-ttu-id="57e36-440">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-440">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="57e36-441">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="57e36-441">Name of assembly name.</span></span>|
|`IsTrackedLoad`|`win:Boolean`|<span data-ttu-id="57e36-442">アセンブリの読み込みを追跡するかどうか。</span><span class="sxs-lookup"><span data-stu-id="57e36-442">Whether the assembly load is tracked.</span></span>|
|`RequestingAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-443">要求しているアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-443">The path of the requesting assembly.</span></span>|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="57e36-444">要求されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-444">The path of the assembly that was requested.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-445">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-445">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="knownpathprobed-event"></a><span data-ttu-id="57e36-446">KnownPathProbed イベント</span><span class="sxs-lookup"><span data-stu-id="57e36-446">KnownPathProbed event</span></span>

|<span data-ttu-id="57e36-447">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="57e36-447">Keyword for raising the event</span></span>|<span data-ttu-id="57e36-448">Level</span><span class="sxs-lookup"><span data-stu-id="57e36-448">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="57e36-449">`Binder` (0x4)</span><span class="sxs-lookup"><span data-stu-id="57e36-449">`Binder` (0x4)</span></span>|<span data-ttu-id="57e36-450">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="57e36-450">Informational (4)</span></span>|

|<span data-ttu-id="57e36-451">Event</span><span class="sxs-lookup"><span data-stu-id="57e36-451">Event</span></span>|<span data-ttu-id="57e36-452">イベント ID</span><span class="sxs-lookup"><span data-stu-id="57e36-452">Event ID</span></span>|<span data-ttu-id="57e36-453">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-453">Description</span></span>|
|-----------|--------------|-----------------|
|`KnownPathProbed`|<span data-ttu-id="57e36-454">296</span><span class="sxs-lookup"><span data-stu-id="57e36-454">296</span></span>|<span data-ttu-id="57e36-455">既知のパスがアセンブリのためにプローブされた。</span><span class="sxs-lookup"><span data-stu-id="57e36-455">A known path was probed for an assembly.</span></span>|

|<span data-ttu-id="57e36-456">フィールド名</span><span class="sxs-lookup"><span data-stu-id="57e36-456">Field Name</span></span>|<span data-ttu-id="57e36-457">データ型</span><span class="sxs-lookup"><span data-stu-id="57e36-457">Data Type</span></span>|<span data-ttu-id="57e36-458">説明</span><span class="sxs-lookup"><span data-stu-id="57e36-458">Description</span></span>|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|<span data-ttu-id="57e36-459">プローブされたパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-459">Path probed.</span></span>|
|`Source`|`win:UInt16`|<span data-ttu-id="57e36-460">プローブされたパスのソース。</span><span class="sxs-lookup"><span data-stu-id="57e36-460">Source of the path probed.</span></span><br/><br/><span data-ttu-id="57e36-461">0x0: アプリケーション アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-461">0x0:Application Assemblies.</span></span><br/><br/><span data-ttu-id="57e36-462">0x1: アプリ ネイティブ イメージ パス。</span><span class="sxs-lookup"><span data-stu-id="57e36-462">0x1:App native image path.</span></span><br/><br/><span data-ttu-id="57e36-463">0x2: アプリのパス。</span><span class="sxs-lookup"><span data-stu-id="57e36-463">0x2:App path.</span></span></br><br/><span data-ttu-id="57e36-464">0x3: プラットフォーム リソース ルート。</span><span class="sxs-lookup"><span data-stu-id="57e36-464">0x3:Platform resource roots.</span></span><br/><br/><span data-ttu-id="57e36-465">0x4: サテライト サブディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="57e36-465">0x4:Satellite Subdirectory.</span></span></br>|
|`Result`|`win:UInt32`|<span data-ttu-id="57e36-466">プローブの HRESULT。</span><span class="sxs-lookup"><span data-stu-id="57e36-466">HRESULT for the probe.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="57e36-467">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="57e36-467">Unique ID for the instance of CoreCLR.</span></span>|
