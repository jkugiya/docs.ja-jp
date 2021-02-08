---
description: 詳細については、「IEnumIDENTITY_ATTRIBUTE インターフェイス」を参照してください。
title: IEnumIDENTITY_ATTRIBUTE インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: b621a722e35d5b31f487e8823b1627fdfe1e7888
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800150"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="1f8e5-103">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f8e5-103">IEnumIDENTITY_ATTRIBUTE Interface</span></span>

<span data-ttu-id="1f8e5-104">現在のスコープ内のコードオブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-104">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f8e5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1f8e5-105">Methods</span></span>  
  
|<span data-ttu-id="1f8e5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1f8e5-106">Method</span></span>|<span data-ttu-id="1f8e5-107">説明</span><span class="sxs-lookup"><span data-stu-id="1f8e5-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="1f8e5-108">このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-108">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="1f8e5-109">このの要素に格納されているデータ `IEnumIDENTITY_ATTRIBUTE` を、指定したデータバッファーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-109">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="1f8e5-110">指定した数の属性を、現在の位置から開始して取得します。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-110">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="1f8e5-111">命令ポインターをこのの先頭に移動し `IEnumIDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-111">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="1f8e5-112">現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f8e5-113">要件</span><span class="sxs-lookup"><span data-stu-id="1f8e5-113">Requirements</span></span>  

 <span data-ttu-id="1f8e5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f8e5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f8e5-115">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="1f8e5-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1f8e5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f8e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8e5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f8e5-117">See also</span></span>

- [<span data-ttu-id="1f8e5-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f8e5-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
