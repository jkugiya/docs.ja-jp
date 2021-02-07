---
description: '詳細について: ICLRErrorReportingManager:: BeginCustomDump メソッド'
title: ICLRErrorReportingManager::BeginCustomDump メソッド
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 3f8498068d50ffc6ea00cf4f08f969c92f010d6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689483"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="01f15-103">ICLRErrorReportingManager::BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="01f15-103">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="01f15-104">エラー報告のためのカスタムヒープダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="01f15-104">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f15-105">構文</span><span class="sxs-lookup"><span data-stu-id="01f15-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f15-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01f15-106">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="01f15-107">からカスタムヒープダンプを構築するときに使用するヒープダンプの種類を示す [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="01f15-107">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="01f15-108">から配列の長さ `items` 。</span><span class="sxs-lookup"><span data-stu-id="01f15-108">[in] The length of the `items` array.</span></span> <span data-ttu-id="01f15-109">`dwFlavor`が DUMP_FLAVOR_Mini でない場合は、を `dwNumItems` 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01f15-109">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="01f15-110">からミニダンプに追加する項目を指定する、 [Customdumpitem](customdumpitem-structure.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="01f15-110">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="01f15-111">`dwFlavor`が DUMP_FLAVOR_Mini でない場合は、を `items` null にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01f15-111">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="01f15-112">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="01f15-112">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f15-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="01f15-113">Return Value</span></span>  
  
|<span data-ttu-id="01f15-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01f15-114">HRESULT</span></span>|<span data-ttu-id="01f15-115">説明</span><span class="sxs-lookup"><span data-stu-id="01f15-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01f15-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="01f15-116">S_OK</span></span>|<span data-ttu-id="01f15-117">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="01f15-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="01f15-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01f15-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01f15-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="01f15-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01f15-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01f15-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01f15-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="01f15-121">The call timed out.</span></span>|  
|<span data-ttu-id="01f15-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01f15-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01f15-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="01f15-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01f15-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01f15-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01f15-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="01f15-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01f15-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01f15-126">E_FAIL</span></span>|<span data-ttu-id="01f15-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="01f15-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01f15-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="01f15-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01f15-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="01f15-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01f15-130">解説</span><span class="sxs-lookup"><span data-stu-id="01f15-130">Remarks</span></span>  

 <span data-ttu-id="01f15-131">メソッドは、 `BeginCustomDump` カスタムヒープダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="01f15-131">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="01f15-132">[Endcustomdump](iclrerrorreportingmanager-endcustomdump-method.md)メソッドは、カスタムヒープダンプ構成をクリアし、関連付けられているすべての状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="01f15-132">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="01f15-133">カスタムヒープダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="01f15-133">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01f15-134">を呼び出さない `EndCustomDump` と、メモリがリークします。</span><span class="sxs-lookup"><span data-stu-id="01f15-134">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f15-135">要件</span><span class="sxs-lookup"><span data-stu-id="01f15-135">Requirements</span></span>  

 <span data-ttu-id="01f15-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01f15-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f15-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="01f15-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01f15-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="01f15-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01f15-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f15-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f15-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="01f15-140">See also</span></span>

- [<span data-ttu-id="01f15-141">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="01f15-141">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="01f15-142">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="01f15-142">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="01f15-143">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01f15-143">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
