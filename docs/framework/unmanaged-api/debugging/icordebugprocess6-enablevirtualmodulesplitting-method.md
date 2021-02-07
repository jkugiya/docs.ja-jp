---
description: '詳細について: ICorDebugProcess6:: EnableVirtualModuleSplitting メソッド'
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: e56e66744ab971deba18f3bdc66d0cfb2053087f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722023"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="76905-103">ICorDebugProcess6::EnableVirtualModuleSplitting メソッド</span><span class="sxs-lookup"><span data-stu-id="76905-103">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>

<span data-ttu-id="76905-104">仮想モジュール分割を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="76905-104">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76905-105">構文</span><span class="sxs-lookup"><span data-stu-id="76905-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76905-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76905-106">Parameters</span></span>  

 `enableSplitting`  
 <span data-ttu-id="76905-107">仮想モジュール分割を有効にするには、`true`。無効にするには、`false`。</span><span class="sxs-lookup"><span data-stu-id="76905-107">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76905-108">解説</span><span class="sxs-lookup"><span data-stu-id="76905-108">Remarks</span></span>  

 <span data-ttu-id="76905-109">仮想モジュール分割により、 [ICorDebug](icordebug-interface.md) は、ビルド処理中にマージされたモジュールを認識し、1つの大きなモジュールではなく個別のモジュールのグループとして表示します。</span><span class="sxs-lookup"><span data-stu-id="76905-109">Virtual module splitting causes [ICorDebug](icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="76905-110">これにより、以下で説明するさまざまな [ICorDebug](icordebug-interface.md) メソッドの動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="76905-110">Doing this changes the behavior of various [ICorDebug](icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76905-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="76905-111">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="76905-112">このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="76905-112">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="76905-113">このメソッドは、 [ICorDebug](icordebug-interface.md) オブジェクトでステートフルな機能変更を発生させません。これは、 [仮想モジュール分割とアンマネージデバッグ api](#APIs) セクションに示されているメソッドの動作を、呼び出されたときに変更することではありません。</span><span class="sxs-lookup"><span data-stu-id="76905-113">It does not cause any stateful functional changes in an [ICorDebug](icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="76905-114">仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。</span><span class="sxs-lookup"><span data-stu-id="76905-114">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="76905-115">また、 [IMetaDataImport](../metadata/imetadataimport-interface.md) api を正しく実装するために、仮想化されたメタデータの大量のメモリ内キャッシュが必要になる場合があります。これらのキャッシュは、仮想モジュールの分割がオフになった後でも保持される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="76905-115">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="76905-116">用語</span><span class="sxs-lookup"><span data-stu-id="76905-116">Terminology</span></span>  

 <span data-ttu-id="76905-117">仮想モジュール分割について説明する場合には、次の用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="76905-117">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="76905-118">コンテナー モジュールまたはコンテナー</span><span class="sxs-lookup"><span data-stu-id="76905-118">container modules, or containers</span></span>  
 <span data-ttu-id="76905-119">集計モジュール。</span><span class="sxs-lookup"><span data-stu-id="76905-119">The aggregate modules.</span></span>  
  
 <span data-ttu-id="76905-120">サブモジュール、または仮想モジュール</span><span class="sxs-lookup"><span data-stu-id="76905-120">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="76905-121">コンテナー内にあるモジュール。</span><span class="sxs-lookup"><span data-stu-id="76905-121">The modules found in a container.</span></span>  
  
 <span data-ttu-id="76905-122">標準モジュール</span><span class="sxs-lookup"><span data-stu-id="76905-122">regular modules</span></span>  
 <span data-ttu-id="76905-123">ビルド時にマージされなかったモジュール。</span><span class="sxs-lookup"><span data-stu-id="76905-123">Modules that were not merged at build time.</span></span> <span data-ttu-id="76905-124">コンテナー モジュールでもサブモジュールでもありません。</span><span class="sxs-lookup"><span data-stu-id="76905-124">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="76905-125">コンテナー モジュールとサブモジュールは、どちらも ICorDebugModuleインターフェイス オブジェクトによって表されます。</span><span class="sxs-lookup"><span data-stu-id="76905-125">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="76905-126">ただし、このセクションで説明するように、インターフェイスの動作は、各ケースで少し異なり \<x-ref to section> ます。</span><span class="sxs-lookup"><span data-stu-id="76905-126">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="76905-127">モジュールとアセンブリ</span><span class="sxs-lookup"><span data-stu-id="76905-127">Modules and assemblies</span></span>  

 <span data-ttu-id="76905-128">アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="76905-128">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="76905-129">各 ICorDebugModule オブジェクトには、コンテナー モジュールを表すかサブモジュールを表すかに関係なく、対応する ICorDebugAssembly オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="76905-129">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="76905-130">のモジュール [:: GetAssembly](icordebugmodule-getassembly-method.md) メソッドは、モジュールからアセンブリに変換します。</span><span class="sxs-lookup"><span data-stu-id="76905-130">The [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="76905-131">他の方向にマップするために、"コードの [アセンブリ:: 列挙体](icordebugassembly-enumeratemodules-method.md) " メソッドは1つのモジュールのみを列挙します。</span><span class="sxs-lookup"><span data-stu-id="76905-131">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="76905-132">この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。</span><span class="sxs-lookup"><span data-stu-id="76905-132">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="76905-133">動作の違い</span><span class="sxs-lookup"><span data-stu-id="76905-133">Behavioral differences</span></span>  

 <span data-ttu-id="76905-134">コンテナー モジュールには、次の動作と特性があります。</span><span class="sxs-lookup"><span data-stu-id="76905-134">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="76905-135">構成要素であるすべてのサブモジュールのメタデータはマージされます。</span><span class="sxs-lookup"><span data-stu-id="76905-135">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="76905-136">型名は変形する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="76905-136">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="76905-137">[モジュール:: GetName](icordebugmodule-getname-method.md)メソッドは、ディスク上のモジュールへのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-137">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="76905-138">[モジュール:: GetSize](icordebugmodule-getsize-method.md)メソッドは、そのイメージのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-138">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="76905-139">ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="76905-139">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="76905-140">ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。</span><span class="sxs-lookup"><span data-stu-id="76905-140">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="76905-141">サブモジュールには、次の動作と特性があります。</span><span class="sxs-lookup"><span data-stu-id="76905-141">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="76905-142">マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="76905-142">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="76905-143">メタデータ名は、変形しません。</span><span class="sxs-lookup"><span data-stu-id="76905-143">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="76905-144">メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="76905-144">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="76905-145">[モジュール:: GetName](icordebugmodule-getname-method.md)メソッドは、ファイルパスではなく、アセンブリ名を返します。</span><span class="sxs-lookup"><span data-stu-id="76905-145">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="76905-146">は、マージさ [れてい](icordebugmodule-getsize-method.md) ない元のイメージのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-146">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="76905-147">ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。</span><span class="sxs-lookup"><span data-stu-id="76905-147">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="76905-148">ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-148">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="76905-149">モジュールから取得されるインターフェイス</span><span class="sxs-lookup"><span data-stu-id="76905-149">Interfaces retrieved from modules</span></span>  

 <span data-ttu-id="76905-150">さまざまなインターフェイスをモジュールから作成または取得できます。</span><span class="sxs-lookup"><span data-stu-id="76905-150">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="76905-151">たとえば、次のようなシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="76905-151">Some of these include:</span></span>  
  
- <span data-ttu-id="76905-152">には、 [モジュール:: GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) メソッドによって返される、のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="76905-152">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="76905-153">[モジュール:: GetAssembly](icordebugmodule-getassembly-method.md)メソッドによって返される、オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="76905-153">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="76905-154">これらのオブジェクトは常に [ICorDebug](icordebug-interface.md)によってキャッシュされ、コンテナーモジュールまたはサブモジュールで作成または照会されたかどうかに関係なく、同じポインター id を持ちます。</span><span class="sxs-lookup"><span data-stu-id="76905-154">These objects are always cached by [ICorDebug](icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="76905-155">サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="76905-155">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>

## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="76905-156">仮想モジュール分割とアンマネージ デバッグ API</span><span class="sxs-lookup"><span data-stu-id="76905-156">Virtual module splitting and the unmanaged debugging APIs</span></span>  

 <span data-ttu-id="76905-157">次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="76905-157">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="76905-158">メソッド</span><span class="sxs-lookup"><span data-stu-id="76905-158">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="76905-159">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="76905-159">ICorDebugFunction::GetModule</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="76905-160">この関数が最初に定義されたサブモジュールを返します</span><span class="sxs-lookup"><span data-stu-id="76905-160">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="76905-161">この関数がマージされたコンテナー モジュールを返します</span><span class="sxs-lookup"><span data-stu-id="76905-161">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="76905-162">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="76905-162">ICorDebugClass::GetModule</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="76905-163">このクラスが最初に定義されたサブモジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-163">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="76905-164">このクラスがマージされたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-164">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="76905-165">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="76905-165">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="76905-166">読み込まれたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-166">Returns the container module that was loaded.</span></span> <span data-ttu-id="76905-167">サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。</span><span class="sxs-lookup"><span data-stu-id="76905-167">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="76905-168">読み込まれたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="76905-168">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="76905-169">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="76905-169">ICorDebugAppDomain::EnumerateAssemblies</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="76905-170">サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。</span><span class="sxs-lookup"><span data-stu-id="76905-170">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="76905-171">**注:**  いずれかのコンテナーアセンブリにシンボルがない場合、そのサブアセンブリは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="76905-171">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="76905-172">いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="76905-172">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="76905-173">コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。</span><span class="sxs-lookup"><span data-stu-id="76905-173">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="76905-174">**注:**  通常のアセンブリにシンボルがない場合は、そのアセンブリが列挙される場合と列挙されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="76905-174">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="76905-175">[GetCode code::](icordebugcode-getcode-method.md) (IL コードのみを参照している場合)</span><span class="sxs-lookup"><span data-stu-id="76905-175">[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="76905-176">マージ前のアセンブリ イメージ内で有効な IL を返します。</span><span class="sxs-lookup"><span data-stu-id="76905-176">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="76905-177">具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。</span><span class="sxs-lookup"><span data-stu-id="76905-177">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="76905-178">これらの TypeRef または MemberRef トークンは、対応する仮想 IMetaDataImport モジュールオブジェクトの[](../metadata/imetadataimport-interface.md)オブジェクトで検索できます。</span><span class="sxs-lookup"><span data-stu-id="76905-178">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="76905-179">マージ後のアセンブリ イメージ内の IL を返します。</span><span class="sxs-lookup"><span data-stu-id="76905-179">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76905-180">要件</span><span class="sxs-lookup"><span data-stu-id="76905-180">Requirements</span></span>  

 <span data-ttu-id="76905-181">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76905-181">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76905-182">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76905-182">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76905-183">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76905-183">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76905-184">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76905-184">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76905-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="76905-185">See also</span></span>

- [<span data-ttu-id="76905-186">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76905-186">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="76905-187">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="76905-187">Debugging Interfaces</span></span>](debugging-interfaces.md)
