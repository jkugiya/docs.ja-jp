---
description: '詳細情報: ICLRMetaHostPolicy インターフェイス'
title: ICLRMetaHostPolicy インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: b14ad417617c32242f8a59844f7c1f1a8d05c78d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637418"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="e6e58-103">ICLRMetaHostPolicy インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6e58-103">ICLRMetaHostPolicy Interface</span></span>

<span data-ttu-id="e6e58-104">ポリシー条件、マネージド アセンブリ、バージョン、および構成ファイルに基づいて、共通言語ランタイム (CLR) インターフェイスへのポインターを返す [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e6e58-104">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6e58-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6e58-105">Methods</span></span>  
  
|<span data-ttu-id="e6e58-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6e58-106">Method</span></span>|<span data-ttu-id="e6e58-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6e58-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6e58-108">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="e6e58-108">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="e6e58-109">ポリシー条件、マネージド アセンブリ、バージョン、および構成ファイルに基づいて、優先される CLR インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e6e58-109">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6e58-110">解説</span><span class="sxs-lookup"><span data-stu-id="e6e58-110">Remarks</span></span>  

 <span data-ttu-id="e6e58-111">このインターフェイスへの参照を取得するには、次のコードに示すように [CLRCreateInstance](clrcreateinstance-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e6e58-111">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="e6e58-112">このインターフェイスでは、実際には CLR の読み込みもアクティブ化も行われず、インストールまたは読み込まれている使用可能なバージョンに基づいて、優先される CLR バージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="e6e58-112">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="e6e58-113">.NET Framework 4 のホスティング API では、特定のニーズを持つホストが意図しないペナルティを伴うことなく基本的な機能を使用できるようにするために、ポリシーが統合されています。</span><span class="sxs-lookup"><span data-stu-id="e6e58-113">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="e6e58-114">たとえば、MSCorEE.dll エクスポートの多くは特定の CLR にバインドされますが、メソッドでは論理的に要求されない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e6e58-114">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="e6e58-115">[METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) 列挙体では、ほとんどのホストに共通するバインド ポリシーが提供されています。</span><span class="sxs-lookup"><span data-stu-id="e6e58-115">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6e58-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="e6e58-116">Requirements</span></span>  

 <span data-ttu-id="e6e58-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6e58-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e58-118">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e6e58-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e6e58-119">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="e6e58-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e58-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e58-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6e58-121">See also</span></span>

- [<span data-ttu-id="e6e58-122">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6e58-122">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="e6e58-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6e58-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e6e58-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="e6e58-124">Hosting</span></span>](index.md)
