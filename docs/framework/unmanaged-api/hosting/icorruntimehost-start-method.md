---
description: '詳細について: ICorRuntimeHost:: Start メソッド'
title: ICorRuntimeHost::Start メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: d07c0144c7192bc2f57927c294ea472cd6b47f9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789607"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="0f588-103">ICorRuntimeHost::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="0f588-103">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="0f588-104">共通言語ランタイム (CLR) を開始します。</span><span class="sxs-lookup"><span data-stu-id="0f588-104">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f588-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f588-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0f588-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f588-106">Return Value</span></span>  
  
|<span data-ttu-id="0f588-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f588-107">HRESULT</span></span>|<span data-ttu-id="0f588-108">説明</span><span class="sxs-lookup"><span data-stu-id="0f588-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f588-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f588-109">S_OK</span></span>|<span data-ttu-id="0f588-110">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="0f588-110">The operation was successful.</span></span>|  
|<span data-ttu-id="0f588-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0f588-111">S_FALSE</span></span>|<span data-ttu-id="0f588-112">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="0f588-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0f588-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f588-113">E_FAIL</span></span>|<span data-ttu-id="0f588-114">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0f588-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0f588-115">メソッドによって E_FAIL が返された場合、CLR はプロセスで使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0f588-115">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="0f588-116">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0f588-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f588-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f588-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f588-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0f588-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f588-119">解説</span><span class="sxs-lookup"><span data-stu-id="0f588-119">Remarks</span></span>  

 <span data-ttu-id="0f588-120">通常は、 `Start` マネージコードを実行する最初の要求で CLR が自動的に起動するため、メソッドを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0f588-120">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f588-121">要件</span><span class="sxs-lookup"><span data-stu-id="0f588-121">Requirements</span></span>  

 <span data-ttu-id="0f588-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f588-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f588-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0f588-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f588-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0f588-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f588-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="0f588-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f588-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f588-126">See also</span></span>

- [<span data-ttu-id="0f588-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f588-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
