---
description: '詳細情報: IAssemblyCacheItem インターフェイス'
title: IAssemblyCacheItem インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 2dcb721f6b65ecca93262f9af2ba355d94bb774d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760864"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="1f668-103">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f668-103">IAssemblyCacheItem Interface</span></span>

<span data-ttu-id="1f668-104">グローバルアセンブリキャッシュ内の1つのアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="1f668-104">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f668-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1f668-105">Methods</span></span>  
  
|<span data-ttu-id="1f668-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1f668-106">Method</span></span>|<span data-ttu-id="1f668-107">説明</span><span class="sxs-lookup"><span data-stu-id="1f668-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f668-108">AbortItem メソッド</span><span class="sxs-lookup"><span data-stu-id="1f668-108">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="1f668-109">アセンブリが解放される前に、グローバルアセンブリキャッシュ内のアセンブリでクリーンアップ操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1f668-109">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="1f668-110">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="1f668-110">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="1f668-111">キャッシュされたアセンブリ参照をメモリにコミットします。</span><span class="sxs-lookup"><span data-stu-id="1f668-111">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="1f668-112">CreateStream メソッド</span><span class="sxs-lookup"><span data-stu-id="1f668-112">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="1f668-113">指定された名前と形式を使用してストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="1f668-113">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f668-114">要件</span><span class="sxs-lookup"><span data-stu-id="1f668-114">Requirements</span></span>  

 <span data-ttu-id="1f668-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f668-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f668-116">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1f668-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1f668-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f668-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f668-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f668-118">See also</span></span>

- [<span data-ttu-id="1f668-119">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f668-119">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1f668-120">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="1f668-120">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="1f668-121">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f668-121">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
