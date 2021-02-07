---
description: 詳細については、「IHostAssemblyManager インターフェイス」を参照してください。
title: IHostAssemblyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 649771f79e65039adfa8c0ade9f167b1679bb917
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708997"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="20206-103">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20206-103">IHostAssemblyManager Interface</span></span>

<span data-ttu-id="20206-104">共通言語ランタイム (CLR) またはホストによって読み込まれる必要があるアセンブリのセットをホストが指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="20206-104">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20206-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="20206-105">Methods</span></span>  
  
|<span data-ttu-id="20206-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="20206-106">Method</span></span>|<span data-ttu-id="20206-107">説明</span><span class="sxs-lookup"><span data-stu-id="20206-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20206-108">GetAssemblyStore メソッド</span><span class="sxs-lookup"><span data-stu-id="20206-108">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="20206-109">ホストによって読み込まれたアセンブリの一覧を表す [IHostAssemblyStore](ihostassemblystore-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="20206-109">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="20206-110">GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="20206-110">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="20206-111">ホストが CLR を読み込むことを想定しているアセンブリの一覧を表す [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="20206-111">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20206-112">解説</span><span class="sxs-lookup"><span data-stu-id="20206-112">Remarks</span></span>  

 <span data-ttu-id="20206-113">ホストがまたはを実装する必要はありません `IHostAssemblyManager` `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="20206-113">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="20206-114">ホストがを実装している場合は `IHostAssemblyManager` 、も実装する必要があり `IHostAssemblyStore` ます。</span><span class="sxs-lookup"><span data-stu-id="20206-114">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="20206-115">ランタイムは、 `IHostAssemblyManager` 初期化時に IID_IHostAssemblyManager のを使用して [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) を呼び出すことにより、を照会し `IID` ます。</span><span class="sxs-lookup"><span data-stu-id="20206-115">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20206-116">要件</span><span class="sxs-lookup"><span data-stu-id="20206-116">Requirements</span></span>  

 <span data-ttu-id="20206-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20206-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20206-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="20206-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20206-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="20206-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20206-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20206-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20206-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="20206-121">See also</span></span>

- [<span data-ttu-id="20206-122">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20206-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="20206-123">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20206-123">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="20206-124">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20206-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="20206-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20206-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
