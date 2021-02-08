---
description: 詳細については、「ICLRDomainManager インターフェイス」を参照してください。
title: ICLRDomainManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: d719e89d81e8c7abb1f238ce50b4e236de17ac72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790010"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="152b1-103">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="152b1-103">ICLRDomainManager Interface</span></span>

<span data-ttu-id="152b1-104">既定のアプリケーションドメインを初期化し、初期化プロパティを指定するために使用されるアプリケーションドメインマネージャーをホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="152b1-104">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="152b1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="152b1-105">Methods</span></span>  
  
|<span data-ttu-id="152b1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="152b1-106">Method</span></span>|<span data-ttu-id="152b1-107">説明</span><span class="sxs-lookup"><span data-stu-id="152b1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="152b1-108">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="152b1-108">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="152b1-109"><xref:System.AppDomainManager?displayProperty=nameWithType>既定のアプリケーションドメインを初期化するために使用されるアプリケーションドメインマネージャーのクラスから派生した型を指定します。</span><span class="sxs-lookup"><span data-stu-id="152b1-109">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="152b1-110">SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="152b1-110">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="152b1-111">既定のアプリケーションドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="152b1-111">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="152b1-112">解説</span><span class="sxs-lookup"><span data-stu-id="152b1-112">Remarks</span></span>  

 <span data-ttu-id="152b1-113">このインターフェイスのインスタンスを取得するには、マネージャーの型 IID で [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) メソッドを呼び出し `IID_ICLRDomainManager` ます。</span><span class="sxs-lookup"><span data-stu-id="152b1-113">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152b1-114">要件</span><span class="sxs-lookup"><span data-stu-id="152b1-114">Requirements</span></span>  

 <span data-ttu-id="152b1-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="152b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152b1-116">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="152b1-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="152b1-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="152b1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="152b1-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152b1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="152b1-119">See also</span></span>

- [<span data-ttu-id="152b1-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="152b1-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="152b1-121">ホスティング</span><span class="sxs-lookup"><span data-stu-id="152b1-121">Hosting</span></span>](index.md)
