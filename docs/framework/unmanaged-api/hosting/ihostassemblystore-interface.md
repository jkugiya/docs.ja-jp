---
description: 詳細については、「IHostAssemblyStore インターフェイス」を参照してください。
title: IHostAssemblyStore インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: a05fee7916911687143d5953e26187162a2fa544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709036"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="08039-103">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08039-103">IHostAssemblyStore Interface</span></span>

<span data-ttu-id="08039-104">共通言語ランタイム (CLR) とは独立して、ホストがアセンブリとモジュールを読み込むことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="08039-104">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08039-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="08039-105">Methods</span></span>  
  
|<span data-ttu-id="08039-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="08039-106">Method</span></span>|<span data-ttu-id="08039-107">説明</span><span class="sxs-lookup"><span data-stu-id="08039-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08039-108">ProvideAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="08039-108">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="08039-109">[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)の呼び出しから返された[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)によって参照されていないアセンブリへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="08039-109">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="08039-110">ProvideModule メソッド</span><span class="sxs-lookup"><span data-stu-id="08039-110">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="08039-111">アセンブリ内のモジュール、またはリンクされた (埋め込まれていない) リソースファイル内のモジュールを解決します。</span><span class="sxs-lookup"><span data-stu-id="08039-111">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08039-112">解説</span><span class="sxs-lookup"><span data-stu-id="08039-112">Remarks</span></span>  

 <span data-ttu-id="08039-113">`IHostAssemblyStore` ホストがアセンブリ id に基づいてアセンブリを効率的に読み込む方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="08039-113">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="08039-114">ホストは、 `IStream` バイトを直接指し示すインスタンスを返すことによって、アセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="08039-114">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="08039-115">CLR は、 `IHostAssemblyStore` 初期化時にを呼び出すことによってホストが実装されているかどうかを判断し `IHostAssemblyManager::GetNonHostAssemblyStores` ます。</span><span class="sxs-lookup"><span data-stu-id="08039-115">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="08039-116">これにより、ホストは、たとえば、ユーザーアセンブリへのバインドを制御できますが、ランタイムに依存して .NET Framework アセンブリにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="08039-116">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08039-117">の実装を提供 `IHostAssemblyStore` する場合、ホストはから返されたによって参照されていないすべてのアセンブリを解決するための目的を指定し `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` ます。</span><span class="sxs-lookup"><span data-stu-id="08039-117">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08039-118">.NET Framework バージョン2.0 では、 [ネイティブイメージジェネレーター (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) ユーティリティによって提供されるように、アセンブリのネイティブイメージをホストが読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="08039-118">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08039-119">要件</span><span class="sxs-lookup"><span data-stu-id="08039-119">Requirements</span></span>  

 <span data-ttu-id="08039-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08039-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08039-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="08039-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08039-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="08039-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08039-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08039-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08039-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="08039-124">See also</span></span>

- [<span data-ttu-id="08039-125">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08039-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="08039-126">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08039-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="08039-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08039-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
