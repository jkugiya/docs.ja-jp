---
description: '詳細について: ICorRuntimeHost:: UnloadDomain メソッド'
title: ICorRuntimeHost::UnloadDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: b191f2342778b2f2ed7ddb7b1fb548c73be96599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799398"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="5e352-103">ICorRuntimeHost::UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="5e352-103">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="5e352-104">現在のプロセスから、指定されたアプリケーションドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="5e352-104">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e352-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e352-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e352-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e352-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="5e352-107">から <xref:System._AppDomain?displayProperty=nameWithType> アンロードするドメインを表す型のポインター。</span><span class="sxs-lookup"><span data-stu-id="5e352-107">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e352-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5e352-108">Return Value</span></span>  
  
|<span data-ttu-id="5e352-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e352-109">HRESULT</span></span>|<span data-ttu-id="5e352-110">説明</span><span class="sxs-lookup"><span data-stu-id="5e352-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e352-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e352-111">S_OK</span></span>|<span data-ttu-id="5e352-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="5e352-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5e352-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5e352-113">S_FALSE</span></span>|<span data-ttu-id="5e352-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="5e352-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5e352-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e352-115">E_FAIL</span></span>|<span data-ttu-id="5e352-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5e352-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5e352-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5e352-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5e352-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5e352-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e352-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e352-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e352-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5e352-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e352-121">要件</span><span class="sxs-lookup"><span data-stu-id="5e352-121">Requirements</span></span>  

 <span data-ttu-id="5e352-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e352-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e352-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5e352-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e352-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5e352-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e352-125">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="5e352-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e352-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e352-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5e352-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5e352-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
