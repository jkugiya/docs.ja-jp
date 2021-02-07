---
description: '詳細情報: IAssemblyCache インターフェイス'
title: IAssemblyCache インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: 29c042fc101180085a697e02376b91b0e1ffd19f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760928"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="a55ba-103">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a55ba-103">IAssemblyCache Interface</span></span>

<span data-ttu-id="a55ba-104">Fusion テクノロジによって使用されるグローバルアセンブリキャッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="a55ba-104">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a55ba-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-105">Methods</span></span>  
  
|<span data-ttu-id="a55ba-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-106">Method</span></span>|<span data-ttu-id="a55ba-107">説明</span><span class="sxs-lookup"><span data-stu-id="a55ba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a55ba-108">CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-108">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="a55ba-109">新しい [Iassemblycacheitem](iassemblycacheitem-interface.md)への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="a55ba-109">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="a55ba-110">CreateAssemblyScavenger メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-110">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="a55ba-111">Fusion テクノロジによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a55ba-111">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="a55ba-112">InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-112">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="a55ba-113">指定したアセンブリをグローバルアセンブリキャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="a55ba-113">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="a55ba-114">QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-114">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="a55ba-115">指定したアセンブリに関する要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="a55ba-115">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="a55ba-116">UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="a55ba-116">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="a55ba-117">指定したアセンブリをグローバルアセンブリキャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a55ba-117">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a55ba-118">要件</span><span class="sxs-lookup"><span data-stu-id="a55ba-118">Requirements</span></span>  

 <span data-ttu-id="a55ba-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a55ba-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a55ba-120">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a55ba-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a55ba-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a55ba-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55ba-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a55ba-122">See also</span></span>

- [<span data-ttu-id="a55ba-123">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a55ba-123">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="a55ba-124">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="a55ba-124">Global Assembly Cache</span></span>](../../app-domains/gac.md)
