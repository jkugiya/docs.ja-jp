---
description: '詳細について: IHostMemoryManager:: GetMemoryLoad メソッド'
title: IHostMemoryManager::GetMemoryLoad メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 82288e6a705b014c2768c75e15376f7e6a0af428
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707846"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="21bca-103">IHostMemoryManager::GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="21bca-103">IHostMemoryManager::GetMemoryLoad Method</span></span>

<span data-ttu-id="21bca-104">ホストによって報告された、現在使用中の物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="21bca-104">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bca-105">構文</span><span class="sxs-lookup"><span data-stu-id="21bca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21bca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21bca-106">Parameters</span></span>  

 `pMemoryLoad`  
 <span data-ttu-id="21bca-107">入出力現在使用されている合計物理メモリのおおよその割合を示すポインター。</span><span class="sxs-lookup"><span data-stu-id="21bca-107">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="21bca-108">入出力共通言語ランタイム (CLR) で使用可能なバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="21bca-108">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21bca-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="21bca-109">Return Value</span></span>  
  
|<span data-ttu-id="21bca-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21bca-110">HRESULT</span></span>|<span data-ttu-id="21bca-111">説明</span><span class="sxs-lookup"><span data-stu-id="21bca-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21bca-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="21bca-112">S_OK</span></span>|<span data-ttu-id="21bca-113">`GetMemoryLoad` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="21bca-113">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="21bca-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21bca-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21bca-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="21bca-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21bca-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21bca-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21bca-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="21bca-117">The call timed out.</span></span>|  
|<span data-ttu-id="21bca-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21bca-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21bca-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="21bca-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21bca-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21bca-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21bca-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="21bca-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21bca-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21bca-122">E_FAIL</span></span>|<span data-ttu-id="21bca-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="21bca-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21bca-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="21bca-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21bca-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="21bca-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21bca-126">解説</span><span class="sxs-lookup"><span data-stu-id="21bca-126">Remarks</span></span>  

 <span data-ttu-id="21bca-127">`GetMemoryLoad` Win32 関数をラップ `GlobalMemoryStatus` します。</span><span class="sxs-lookup"><span data-stu-id="21bca-127">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="21bca-128">の値 `pMemoryLoad` は、 `dwMemoryLoad` `MEMORYSTATUS` から返された構造体のフィールドに相当し `GlobalMemoryStatus` ます。</span><span class="sxs-lookup"><span data-stu-id="21bca-128">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="21bca-129">ランタイムは、ガベージコレクターのヒューリスティックとして戻り値を使用します。</span><span class="sxs-lookup"><span data-stu-id="21bca-129">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="21bca-130">たとえば、ホストが大量のメモリを使用していることを報告した場合、ガベージコレクターは複数の世代から収集して、使用可能になる可能性があるメモリの量を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="21bca-130">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21bca-131">要件</span><span class="sxs-lookup"><span data-stu-id="21bca-131">Requirements</span></span>  

 <span data-ttu-id="21bca-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21bca-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21bca-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="21bca-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21bca-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="21bca-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21bca-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21bca-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bca-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="21bca-136">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="21bca-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21bca-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
