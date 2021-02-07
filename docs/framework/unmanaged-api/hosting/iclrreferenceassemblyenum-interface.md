---
description: 詳細については、「ICLRReferenceAssemblyEnum インターフェイス」を参照してください。
title: ICLRReferenceAssemblyEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
ms.openlocfilehash: a7e522623c254940a6dbb8d22bf7f2fec76a1072
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689002"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="8d892-103">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d892-103">ICLRReferenceAssemblyEnum Interface</span></span>

<span data-ttu-id="8d892-104">共通言語ランタイム (CLR) の内部にあるアセンブリ id データを使用して、ファイルまたはストリームによって参照されるアセンブリのセットをホストが操作できるようにするメソッドを提供します。これらの id を作成したり、理解したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8d892-104">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d892-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d892-105">Methods</span></span>  
  
|<span data-ttu-id="8d892-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d892-106">Method</span></span>|<span data-ttu-id="8d892-107">説明</span><span class="sxs-lookup"><span data-stu-id="8d892-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d892-108">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="8d892-108">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="8d892-109">指定されたインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d892-109">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d892-110">要件</span><span class="sxs-lookup"><span data-stu-id="8d892-110">Requirements</span></span>  

 <span data-ttu-id="8d892-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d892-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d892-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8d892-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d892-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8d892-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d892-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d892-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d892-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d892-115">See also</span></span>

- [<span data-ttu-id="8d892-116">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d892-116">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8d892-117">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d892-117">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8d892-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d892-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
