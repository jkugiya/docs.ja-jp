---
description: '詳細について: IHostMemoryManager:: VirtualFree メソッド'
title: IHostMemoryManager::VirtualFree メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: 987661ce1b7bfd08f757f53082313b8eb60ff282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707537"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="a0d5e-103">IHostMemoryManager::VirtualFree メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d5e-103">IHostMemoryManager::VirtualFree Method</span></span>

<span data-ttu-id="a0d5e-104">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="a0d5e-105">`VirtualFree`リリース、デ、またはリリースの Win32 実装では、呼び出しプロセスの仮想アドレス空間内のページの領域をデします。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-105">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d5e-106">構文</span><span class="sxs-lookup"><span data-stu-id="a0d5e-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0d5e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0d5e-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="a0d5e-108">から解放される仮想メモリページのベースアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-108">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="a0d5e-109">から解放する領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-109">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="a0d5e-110">から解放操作の種類。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-110">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0d5e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0d5e-111">Return Value</span></span>  
  
|<span data-ttu-id="a0d5e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0d5e-112">HRESULT</span></span>|<span data-ttu-id="a0d5e-113">説明</span><span class="sxs-lookup"><span data-stu-id="a0d5e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0d5e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0d5e-114">S_OK</span></span>|<span data-ttu-id="a0d5e-115">`VirtualFree` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-115">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="a0d5e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0d5e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0d5e-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0d5e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0d5e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0d5e-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-119">The call timed out.</span></span>|  
|<span data-ttu-id="a0d5e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0d5e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0d5e-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0d5e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0d5e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0d5e-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0d5e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0d5e-124">E_FAIL</span></span>|<span data-ttu-id="a0d5e-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0d5e-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0d5e-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0d5e-128">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a0d5e-128">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a0d5e-129">ホストを通じて割り当てられていないメモリを解放しようとしました。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-129">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d5e-130">解説</span><span class="sxs-lookup"><span data-stu-id="a0d5e-130">Remarks</span></span>  

 <span data-ttu-id="a0d5e-131">`VirtualFree``lpAddress` [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md)関数の以前の呼び出しによって、パラメーターに関連付けられた仮想メモリページを解放します。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-131">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="a0d5e-132">ホストを通じて割り当てられていないメモリを解放しようとすると HOST_E_INVALIDOPERATION が返されます。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-132">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="a0d5e-133">セマンティクスは、の Win32 実装のセマンティクスと同じです `VirtualFree` 。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-133">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="a0d5e-134">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-134">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d5e-135">要件</span><span class="sxs-lookup"><span data-stu-id="a0d5e-135">Requirements</span></span>  

 <span data-ttu-id="a0d5e-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0d5e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d5e-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a0d5e-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0d5e-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a0d5e-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0d5e-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d5e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d5e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d5e-140">See also</span></span>

- [<span data-ttu-id="a0d5e-141">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d5e-141">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="a0d5e-142">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d5e-142">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
