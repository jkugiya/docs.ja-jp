---
description: '詳細について: ICLRAppDomainResourceMonitor:: Getcurrentcpu 時間メソッド'
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: ce36bf4ab88f953834d3ff12404bcaadcb42812d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753929"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="81886-103">ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="81886-103">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>

<span data-ttu-id="81886-104">アプリケーションドメインが作成されてから、現在のアプリケーションドメインでの実行中にすべてのスレッドによって使用された合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="81886-104">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81886-105">構文</span><span class="sxs-lookup"><span data-stu-id="81886-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81886-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81886-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="81886-107">から要求されたアプリケーションドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="81886-107">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="81886-108">入出力アプリケーションドメインが作成されてから現在のアプリケーションドメインで実行中に、すべてのスレッドによって使用された合計プロセッサ時間を示すポインター。</span><span class="sxs-lookup"><span data-stu-id="81886-108">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="81886-109">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="81886-109">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81886-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="81886-110">Return Value</span></span>  
  
|<span data-ttu-id="81886-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81886-111">HRESULT</span></span>|<span data-ttu-id="81886-112">説明</span><span class="sxs-lookup"><span data-stu-id="81886-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81886-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="81886-113">S_OK</span></span>|<span data-ttu-id="81886-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="81886-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="81886-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="81886-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="81886-116">アプリケーションドメインがアンロードされているか、または存在しません。</span><span class="sxs-lookup"><span data-stu-id="81886-116">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="81886-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81886-117">E_FAIL</span></span>|<span data-ttu-id="81886-118">アプリケーションドメインのリソース監視が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="81886-118">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="81886-119">\- または -</span><span class="sxs-lookup"><span data-stu-id="81886-119">-or-</span></span><br /><br /> <span data-ttu-id="81886-120">その他のすべてのエラー。</span><span class="sxs-lookup"><span data-stu-id="81886-120">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81886-121">解説</span><span class="sxs-lookup"><span data-stu-id="81886-121">Remarks</span></span>  

 <span data-ttu-id="81886-122">このメソッドは、マネージプロパティに相当するアンマネージドです <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81886-122">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81886-123">要件</span><span class="sxs-lookup"><span data-stu-id="81886-123">Requirements</span></span>  

 <span data-ttu-id="81886-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81886-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81886-125">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="81886-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="81886-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="81886-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81886-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81886-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81886-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="81886-128">See also</span></span>

- [<span data-ttu-id="81886-129">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81886-129">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="81886-130">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81886-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="81886-131">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="81886-131">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="81886-132">ホスティング</span><span class="sxs-lookup"><span data-stu-id="81886-132">Hosting</span></span>](index.md)
