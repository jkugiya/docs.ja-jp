---
description: 詳細については、「IHostControl インターフェイス」を参照してください。
title: IHostControl インターフェイス
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: e7a242ed0fdaa734425bec9b48f01fe45cba5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789464"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="b582c-103">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b582c-103">IHostControl Interface</span></span>

<span data-ttu-id="b582c-104">アセンブリの読み込みを構成し、ホストがサポートするホストインターフェイスを決定するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b582c-104">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b582c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b582c-105">Methods</span></span>  
  
|<span data-ttu-id="b582c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b582c-106">Method</span></span>|<span data-ttu-id="b582c-107">説明</span><span class="sxs-lookup"><span data-stu-id="b582c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b582c-108">GetHostManager メソッド</span><span class="sxs-lookup"><span data-stu-id="b582c-108">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="b582c-109">指定したを使用して、ホストのインターフェイスの実装へのインターフェイスポインターを取得し `IID` ます。</span><span class="sxs-lookup"><span data-stu-id="b582c-109">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="b582c-110">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="b582c-110">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="b582c-111">アプリケーションドメインが作成されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="b582c-111">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b582c-112">要件</span><span class="sxs-lookup"><span data-stu-id="b582c-112">Requirements</span></span>  

 <span data-ttu-id="b582c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b582c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b582c-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b582c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b582c-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b582c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b582c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b582c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b582c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b582c-117">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="b582c-118">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b582c-118">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="b582c-119">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b582c-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b582c-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b582c-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
