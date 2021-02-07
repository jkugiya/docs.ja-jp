---
description: '詳細については、次を参照してください: ICLRAppDomainResourceMonitor:: GetCurrentAllocated メソッド'
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: d7aaf31f775a9d6e2af95cf1a832c78587a85fe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753953"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="363e9-103">ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="363e9-103">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>

<span data-ttu-id="363e9-104">アプリケーションドメインが作成されてからアプリケーションドメインによって行われたすべてのメモリ割り当ての合計サイズ (バイト単位) を取得します。ガベージコレクトされたメモリは減算されません。</span><span class="sxs-lookup"><span data-stu-id="363e9-104">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="363e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="363e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="363e9-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="363e9-107">から要求されたアプリケーションドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="363e9-107">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="363e9-108">入出力すべてのメモリ割り当ての合計サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="363e9-108">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="363e9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="363e9-109">Return Value</span></span>  

 <span data-ttu-id="363e9-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="363e9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="363e9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="363e9-111">HRESULT</span></span>|<span data-ttu-id="363e9-112">説明</span><span class="sxs-lookup"><span data-stu-id="363e9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="363e9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="363e9-113">S_OK</span></span>|<span data-ttu-id="363e9-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="363e9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="363e9-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="363e9-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="363e9-116">アプリケーションドメインがアンロードされているか、または存在しません。</span><span class="sxs-lookup"><span data-stu-id="363e9-116">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="363e9-117">解説</span><span class="sxs-lookup"><span data-stu-id="363e9-117">Remarks</span></span>  

 <span data-ttu-id="363e9-118">このメソッドは、マネージプロパティに相当するアンマネージドです <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="363e9-118">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363e9-119">要件</span><span class="sxs-lookup"><span data-stu-id="363e9-119">Requirements</span></span>  

 <span data-ttu-id="363e9-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="363e9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363e9-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="363e9-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="363e9-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="363e9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="363e9-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363e9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363e9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="363e9-124">See also</span></span>

- [<span data-ttu-id="363e9-125">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="363e9-125">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="363e9-126">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="363e9-126">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="363e9-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="363e9-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="363e9-128">ホスティング</span><span class="sxs-lookup"><span data-stu-id="363e9-128">Hosting</span></span>](index.md)
