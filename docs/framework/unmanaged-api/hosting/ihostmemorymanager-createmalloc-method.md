---
description: '詳細について: IHostMemoryManager:: CreateMAlloc メソッド'
title: IHostMemoryManager::CreateMAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: de73490a5c8b4e1672beb4750bcc617c2371f07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707888"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="d08f4-103">IHostMemoryManager::CreateMAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="d08f4-103">IHostMemoryManager::CreateMAlloc Method</span></span>

<span data-ttu-id="d08f4-104">ホストによって作成されたヒープから割り当て要求を行うために使用される [IHostMAlloc](ihostmalloc-interface.md) インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d08f4-104">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08f4-105">構文</span><span class="sxs-lookup"><span data-stu-id="d08f4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d08f4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d08f4-106">Parameters</span></span>  

 `dwMallocType`  
 <span data-ttu-id="d08f4-107">から割り当てられるメモリの特性を指定する [MALLOC_TYPE](malloc-type-enumeration.md) フラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="d08f4-107">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="d08f4-108">入出力 `IHostMAlloc` ホストによって提供されるインスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d08f4-108">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d08f4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d08f4-109">Return Value</span></span>  
  
|<span data-ttu-id="d08f4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d08f4-110">HRESULT</span></span>|<span data-ttu-id="d08f4-111">説明</span><span class="sxs-lookup"><span data-stu-id="d08f4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d08f4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d08f4-112">S_OK</span></span>|<span data-ttu-id="d08f4-113">`CreateMAlloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d08f4-113">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="d08f4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d08f4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d08f4-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d08f4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d08f4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d08f4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d08f4-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d08f4-117">The call timed out.</span></span>|  
|<span data-ttu-id="d08f4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d08f4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d08f4-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d08f4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d08f4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d08f4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d08f4-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d08f4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d08f4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d08f4-122">E_FAIL</span></span>|<span data-ttu-id="d08f4-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d08f4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d08f4-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d08f4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d08f4-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d08f4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d08f4-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d08f4-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d08f4-127">割り当て要求を完了するために必要な物理メモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d08f4-127">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08f4-128">解説</span><span class="sxs-lookup"><span data-stu-id="d08f4-128">Remarks</span></span>  

 <span data-ttu-id="d08f4-129">`CreateMAlloc` CLR が標準の Win32 関数を使用する代わりに、ホストを通じて割り当て要求を行うことができるようにするオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="d08f4-129">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08f4-130">要件</span><span class="sxs-lookup"><span data-stu-id="d08f4-130">Requirements</span></span>  

 <span data-ttu-id="d08f4-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d08f4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08f4-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d08f4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d08f4-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d08f4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d08f4-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08f4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08f4-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="d08f4-135">See also</span></span>

- [<span data-ttu-id="d08f4-136">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d08f4-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="d08f4-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d08f4-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
