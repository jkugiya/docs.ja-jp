---
description: 詳細については、「ICLRAppDomainResourceMonitor インターフェイス」を参照してください。
title: ICLRAppDomainResourceMonitor インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 85321eabedb6912efabe57553732f8c6a4063155
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753901"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="92e3a-103">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92e3a-103">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="92e3a-104">アプリケーションドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="92e3a-104">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92e3a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="92e3a-105">Methods</span></span>  
  
|<span data-ttu-id="92e3a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="92e3a-106">Method</span></span>|<span data-ttu-id="92e3a-107">説明</span><span class="sxs-lookup"><span data-stu-id="92e3a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92e3a-108">GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="92e3a-108">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="92e3a-109">アプリケーションドメインが作成されてからアプリケーションドメインによって行われたすべてのメモリ割り当ての合計サイズ (バイト単位) を取得します。ガベージコレクトされたメモリは減算されません。</span><span class="sxs-lookup"><span data-stu-id="92e3a-109">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="92e3a-110">GetCurrentSurvived メソッド</span><span class="sxs-lookup"><span data-stu-id="92e3a-110">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="92e3a-111">最後の完全なブロッキングガベージコレクションの後に残った、現在のアプリケーションドメインによって参照されているバイト数を取得します。</span><span class="sxs-lookup"><span data-stu-id="92e3a-111">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="92e3a-112">GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="92e3a-112">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="92e3a-113">アプリケーションドメインが作成されてから、現在のアプリケーションドメインでの実行中にすべてのスレッドによって使用された合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="92e3a-113">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92e3a-114">解説</span><span class="sxs-lookup"><span data-stu-id="92e3a-114">Remarks</span></span>  

 <span data-ttu-id="92e3a-115">インターフェイスには、 `ICLRAppDomainResourceMonitor` 次のマネージプロパティと同様の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="92e3a-115">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="92e3a-116">要件</span><span class="sxs-lookup"><span data-stu-id="92e3a-116">Requirements</span></span>  

 <span data-ttu-id="92e3a-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e3a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e3a-118">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="92e3a-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="92e3a-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="92e3a-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92e3a-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e3a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e3a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="92e3a-121">See also</span></span>

- [<span data-ttu-id="92e3a-122">\<appDomainResourceMonitoring> 要素</span><span class="sxs-lookup"><span data-stu-id="92e3a-122">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="92e3a-123">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="92e3a-123">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="92e3a-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92e3a-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="92e3a-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="92e3a-125">Hosting</span></span>](index.md)
