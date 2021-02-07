---
description: 詳細については、「IMetaDataDispenser インターフェイス」を参照してください。
title: IMetaDataDispenser インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: 5ba37fc05a4e1897b100967d32b268f91a0e4402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721009"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="cac4d-103">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cac4d-103">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="cac4d-104">新しいメタデータスコープを作成したり、既存のメタデータスコープを開いたりするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cac4d-104">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cac4d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cac4d-105">Methods</span></span>  
  
|<span data-ttu-id="cac4d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cac4d-106">Method</span></span>|<span data-ttu-id="cac4d-107">説明</span><span class="sxs-lookup"><span data-stu-id="cac4d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cac4d-108">DefineScope メソッド</span><span class="sxs-lookup"><span data-stu-id="cac4d-108">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="cac4d-109">新しいメタデータを作成できる新しい領域をメモリに作成します。</span><span class="sxs-lookup"><span data-stu-id="cac4d-109">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="cac4d-110">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="cac4d-110">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="cac4d-111">ディスク上の既存のファイルを開き、そのメタデータをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="cac4d-111">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="cac4d-112">OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="cac4d-112">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="cac4d-113">既存のメタデータを含むメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="cac4d-113">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="cac4d-114">つまり、このメソッドは、既存のデータがメタデータとして扱われる、指定されたメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="cac4d-114">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cac4d-115">要件</span><span class="sxs-lookup"><span data-stu-id="cac4d-115">Requirements</span></span>  

 <span data-ttu-id="cac4d-116">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cac4d-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac4d-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cac4d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cac4d-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cac4d-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cac4d-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cac4d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac4d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cac4d-120">See also</span></span>

- [<span data-ttu-id="cac4d-121">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cac4d-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="cac4d-122">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cac4d-122">Metadata Interfaces</span></span>](metadata-interfaces.md)
