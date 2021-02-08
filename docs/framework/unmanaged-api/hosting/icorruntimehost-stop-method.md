---
description: '詳細について: ICorRuntimeHost:: Stop メソッド'
title: ICorRuntimeHost::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: b44c77b7d0fe3a078efa11756f5fac7ba400ca5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789594"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="1d7a9-103">ICorRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="1d7a9-103">ICorRuntimeHost::Stop Method</span></span>

<span data-ttu-id="1d7a9-104">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-104">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7a9-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d7a9-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1d7a9-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="1d7a9-106">Return Value</span></span>  
  
|<span data-ttu-id="1d7a9-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d7a9-107">HRESULT</span></span>|<span data-ttu-id="1d7a9-108">説明</span><span class="sxs-lookup"><span data-stu-id="1d7a9-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d7a9-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d7a9-109">S_OK</span></span>|<span data-ttu-id="1d7a9-110">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-110">The operation was successful.</span></span>|  
|<span data-ttu-id="1d7a9-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1d7a9-111">S_FALSE</span></span>|<span data-ttu-id="1d7a9-112">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1d7a9-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d7a9-113">E_FAIL</span></span>|<span data-ttu-id="1d7a9-114">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1d7a9-115">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-115">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1d7a9-116">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1d7a9-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d7a9-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d7a9-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d7a9-119">解説</span><span class="sxs-lookup"><span data-stu-id="1d7a9-119">Remarks</span></span>  

 <span data-ttu-id="1d7a9-120">通常、メソッドを呼び出す必要はありません。これは、 `Stop` プロセスが終了したときにコードが実行を停止するためです。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-120">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d7a9-121">を呼び出した後 `Stop` 、CLR を同じプロセスに再初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-121">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d7a9-122">要件</span><span class="sxs-lookup"><span data-stu-id="1d7a9-122">Requirements</span></span>  

 <span data-ttu-id="1d7a9-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d7a9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d7a9-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1d7a9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d7a9-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1d7a9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d7a9-126">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="1d7a9-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7a9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d7a9-127">See also</span></span>

- [<span data-ttu-id="1d7a9-128">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d7a9-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
