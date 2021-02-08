---
description: '詳細について: ICorRuntimeHost:: CloseEnum メソッド'
title: ICorRuntimeHost::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: 1fc18ff3e00f85a4f047417f880ec2b0e06496b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789724"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="4525e-103">ICorRuntimeHost::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="4525e-103">ICorRuntimeHost::CloseEnum Method</span></span>

<span data-ttu-id="4525e-104">ドメイン列挙子をドメインリストの先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="4525e-104">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4525e-105">構文</span><span class="sxs-lookup"><span data-stu-id="4525e-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4525e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4525e-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="4525e-107">からリセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="4525e-107">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4525e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4525e-108">Return Value</span></span>  
  
|<span data-ttu-id="4525e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4525e-109">HRESULT</span></span>|<span data-ttu-id="4525e-110">説明</span><span class="sxs-lookup"><span data-stu-id="4525e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4525e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4525e-111">S_OK</span></span>|<span data-ttu-id="4525e-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="4525e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="4525e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4525e-113">S_FALSE</span></span>|<span data-ttu-id="4525e-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="4525e-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4525e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4525e-115">E_FAIL</span></span>|<span data-ttu-id="4525e-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4525e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4525e-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4525e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4525e-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4525e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4525e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4525e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4525e-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4525e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4525e-121">要件</span><span class="sxs-lookup"><span data-stu-id="4525e-121">Requirements</span></span>  

 <span data-ttu-id="4525e-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4525e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4525e-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4525e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4525e-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4525e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4525e-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="4525e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4525e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4525e-126">See also</span></span>

- [<span data-ttu-id="4525e-127">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="4525e-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="4525e-128">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4525e-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
