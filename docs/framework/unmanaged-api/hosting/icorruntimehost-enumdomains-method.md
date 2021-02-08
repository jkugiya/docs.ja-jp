---
description: '詳細情報: ICorRuntimeHost:: EnumDomains メソッド'
title: ICorRuntimeHost::EnumDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
ms.openlocfilehash: e581fe95a78a4f55d50a99e4925e03a1777268a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784874"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="1e937-103">ICorRuntimeHost::EnumDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="1e937-103">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="1e937-104">現在のプロセス内のドメインの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e937-104">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e937-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e937-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e937-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e937-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="1e937-107">入出力ドメインの列挙子。</span><span class="sxs-lookup"><span data-stu-id="1e937-107">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e937-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e937-108">Return Value</span></span>  
  
|<span data-ttu-id="1e937-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e937-109">HRESULT</span></span>|<span data-ttu-id="1e937-110">説明</span><span class="sxs-lookup"><span data-stu-id="1e937-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e937-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e937-111">S_OK</span></span>|<span data-ttu-id="1e937-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e937-112">The operation was successful.</span></span>|  
|<span data-ttu-id="1e937-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1e937-113">S_FALSE</span></span>|<span data-ttu-id="1e937-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1e937-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1e937-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e937-115">E_FAIL</span></span>|<span data-ttu-id="1e937-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1e937-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1e937-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1e937-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1e937-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e937-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1e937-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e937-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e937-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="1e937-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e937-121">要件</span><span class="sxs-lookup"><span data-stu-id="1e937-121">Requirements</span></span>  

 <span data-ttu-id="1e937-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e937-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e937-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1e937-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e937-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1e937-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e937-125">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="1e937-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e937-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e937-126">See also</span></span>

- [<span data-ttu-id="1e937-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e937-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
