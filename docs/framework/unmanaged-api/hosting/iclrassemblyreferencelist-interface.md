---
description: 詳細については、「ICLRAssemblyReferenceList インターフェイス」を参照してください。
title: ICLRAssemblyReferenceList インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f5ef4efd343ebc18c443482f4697a3d299c5aac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716810"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="08e14-103">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08e14-103">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="08e14-104">ホストではなく、共通言語ランタイム (CLR) によって読み込まれるアセンブリの一覧を管理します。</span><span class="sxs-lookup"><span data-stu-id="08e14-104">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08e14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="08e14-105">Methods</span></span>  
  
|<span data-ttu-id="08e14-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="08e14-106">Method</span></span>|<span data-ttu-id="08e14-107">説明</span><span class="sxs-lookup"><span data-stu-id="08e14-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08e14-108">IsAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="08e14-108">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="08e14-109">指定されたポインターがリスト内のアセンブリを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="08e14-109">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="08e14-110">IsStringAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="08e14-110">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="08e14-111">指定された名前がリスト内のアセンブリの名前と一致するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="08e14-111">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08e14-112">解説</span><span class="sxs-lookup"><span data-stu-id="08e14-112">Remarks</span></span>  

 <span data-ttu-id="08e14-113">[ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)メソッドを呼び出して、のインスタンスへのポインターを取得 `ICLRAssemblyReferenceList` します。</span><span class="sxs-lookup"><span data-stu-id="08e14-113">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08e14-114">要件</span><span class="sxs-lookup"><span data-stu-id="08e14-114">Requirements</span></span>  

 <span data-ttu-id="08e14-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08e14-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08e14-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="08e14-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08e14-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="08e14-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08e14-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08e14-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e14-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="08e14-119">See also</span></span>

- [<span data-ttu-id="08e14-120">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08e14-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="08e14-121">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08e14-121">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="08e14-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08e14-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
