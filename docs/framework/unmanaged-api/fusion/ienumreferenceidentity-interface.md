---
description: 詳細については、「IEnumReferenceIdentity インターフェイス」を参照してください。
title: IEnumReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: a7f17793fd737b5153c27dae59fb2aa87b46cf48
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465302"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="a1e59-103">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1e59-103">IEnumReferenceIdentity Interface</span></span>

<span data-ttu-id="a1e59-104">オブジェクトのコレクションの列挙子として機能し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="a1e59-104">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1e59-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a1e59-105">Methods</span></span>  
  
|<span data-ttu-id="a1e59-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a1e59-106">Method</span></span>|<span data-ttu-id="a1e59-107">説明</span><span class="sxs-lookup"><span data-stu-id="a1e59-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="a1e59-108">このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumReferenceIdentity` `IEnumReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="a1e59-108">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="a1e59-109">現在の位置から開始して、指定した数の `IReferenceIdentity` オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a1e59-109">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="a1e59-110">命令ポインターをこのの先頭に移動し `IEnumReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="a1e59-110">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="a1e59-111">現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="a1e59-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1e59-112">要件</span><span class="sxs-lookup"><span data-stu-id="a1e59-112">Requirements</span></span>  

 <span data-ttu-id="a1e59-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e59-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e59-114">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="a1e59-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a1e59-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e59-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1e59-116">See also</span></span>

- [<span data-ttu-id="a1e59-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1e59-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="a1e59-118">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1e59-118">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
