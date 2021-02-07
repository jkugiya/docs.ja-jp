---
description: '詳細について: IHostMemoryManager:: VirtualProtect メソッド'
title: IHostMemoryManager::VirtualProtect メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
ms.openlocfilehash: 66e1fb5afdc3aa5c400ed0ffa9cea569d300e6a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707439"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="e7f72-103">IHostMemoryManager::VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="e7f72-103">IHostMemoryManager::VirtualProtect Method</span></span>

<span data-ttu-id="e7f72-104">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="e7f72-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="e7f72-105">の Win32 実装では、 `VirtualProtect` 呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域の保護が変更されます。</span><span class="sxs-lookup"><span data-stu-id="e7f72-105">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f72-106">構文</span><span class="sxs-lookup"><span data-stu-id="e7f72-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7f72-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7f72-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="e7f72-108">から保護属性が変更される仮想メモリのベースアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e7f72-108">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="e7f72-109">から変更するメモリページの領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e7f72-109">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="e7f72-110">から適用するメモリ保護の種類。</span><span class="sxs-lookup"><span data-stu-id="e7f72-110">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="e7f72-111">入出力以前のメモリ保護値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e7f72-111">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7f72-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7f72-112">Return Value</span></span>  
  
|<span data-ttu-id="e7f72-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7f72-113">HRESULT</span></span>|<span data-ttu-id="e7f72-114">説明</span><span class="sxs-lookup"><span data-stu-id="e7f72-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7f72-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7f72-115">S_OK</span></span>|<span data-ttu-id="e7f72-116">`VirtualProtect` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e7f72-116">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="e7f72-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7f72-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7f72-118">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e7f72-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7f72-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7f72-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7f72-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e7f72-120">The call timed out.</span></span>|  
|<span data-ttu-id="e7f72-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7f72-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7f72-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e7f72-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7f72-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7f72-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7f72-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e7f72-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7f72-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7f72-125">E_FAIL</span></span>|<span data-ttu-id="e7f72-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e7f72-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7f72-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e7f72-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7f72-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e7f72-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7f72-129">解説</span><span class="sxs-lookup"><span data-stu-id="e7f72-129">Remarks</span></span>  

 <span data-ttu-id="e7f72-130">のこの実装 `VirtualProtect` は HRESULT 値を返しますが、Win32 実装は成功を示す0以外の値を返し、エラーを示す0の値を返します。</span><span class="sxs-lookup"><span data-stu-id="e7f72-130">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="e7f72-131">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f72-131">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f72-132">要件</span><span class="sxs-lookup"><span data-stu-id="e7f72-132">Requirements</span></span>  

 <span data-ttu-id="e7f72-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7f72-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f72-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e7f72-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7f72-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e7f72-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7f72-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f72-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f72-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7f72-137">See also</span></span>

- [<span data-ttu-id="e7f72-138">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7f72-138">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
