---
description: '詳細情報: ICorRuntimeHost:: NextDomain メソッド'
title: ICorRuntimeHost::NextDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: cfced9d1d3c91f4ec9508b86157ceebae9f95a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789620"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="e2171-103">ICorRuntimeHost::NextDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e2171-103">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="e2171-104">列挙体の次のドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e2171-104">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2171-105">構文</span><span class="sxs-lookup"><span data-stu-id="e2171-105">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2171-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2171-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="e2171-107">から [Enumdomains](icorruntimehost-enumdomains-method.md)の呼び出しによって取得された列挙子。</span><span class="sxs-lookup"><span data-stu-id="e2171-107">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e2171-108">入出力列挙体の次のドメインを表す型へのインターフェイスポインター <xref:System._AppDomain?displayProperty=nameWithType> 。または、他のドメインが存在しない場合は null。</span><span class="sxs-lookup"><span data-stu-id="e2171-108">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2171-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="e2171-109">Return Value</span></span>  
  
|<span data-ttu-id="e2171-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2171-110">HRESULT</span></span>|<span data-ttu-id="e2171-111">説明</span><span class="sxs-lookup"><span data-stu-id="e2171-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2171-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2171-112">S_OK</span></span>|<span data-ttu-id="e2171-113">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="e2171-113">The operation was successful.</span></span>|  
|<span data-ttu-id="e2171-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e2171-114">S_FALSE</span></span>|<span data-ttu-id="e2171-115">操作を完了できなかったか、列挙にドメインがありません。</span><span class="sxs-lookup"><span data-stu-id="e2171-115">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="e2171-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2171-116">E_FAIL</span></span>|<span data-ttu-id="e2171-117">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e2171-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e2171-118">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e2171-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e2171-119">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e2171-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e2171-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2171-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2171-121">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e2171-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2171-122">要件</span><span class="sxs-lookup"><span data-stu-id="e2171-122">Requirements</span></span>  

 <span data-ttu-id="e2171-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2171-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2171-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e2171-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2171-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e2171-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2171-126">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="e2171-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2171-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2171-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e2171-128">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2171-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
