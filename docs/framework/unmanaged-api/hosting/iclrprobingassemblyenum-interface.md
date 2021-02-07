---
description: 詳細については、「ICLRProbingAssemblyEnum インターフェイス」を参照してください。
title: ICLRProbingAssemblyEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: 1fd11e237f02bab85ec2b41df49d7d8a2f27e1e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716511"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="6b492-103">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b492-103">ICLRProbingAssemblyEnum Interface</span></span>

<span data-ttu-id="6b492-104">共通言語ランタイム (CLR) の内部にあるアセンブリの id 情報を使用して、ホストがアセンブリのプローブ id を取得できるようにするメソッドを提供します。このメソッドは、その id を作成または理解する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6b492-104">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b492-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6b492-105">Methods</span></span>  
  
|<span data-ttu-id="6b492-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6b492-106">Method</span></span>|<span data-ttu-id="6b492-107">説明</span><span class="sxs-lookup"><span data-stu-id="6b492-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b492-108">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="6b492-108">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="6b492-109">指定したインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="6b492-109">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b492-110">解説</span><span class="sxs-lookup"><span data-stu-id="6b492-110">Remarks</span></span>  

 <span data-ttu-id="6b492-111">[ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)などのメソッドは、 `ICLRProbingAssemblyEnum` インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="6b492-111">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b492-112">要件</span><span class="sxs-lookup"><span data-stu-id="6b492-112">Requirements</span></span>  

 <span data-ttu-id="6b492-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b492-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b492-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6b492-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b492-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b492-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b492-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b492-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b492-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b492-117">See also</span></span>

- [<span data-ttu-id="6b492-118">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b492-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6b492-119">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b492-119">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6b492-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b492-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
