---
description: '詳細情報: CLRDATA_ADDRESS_RANGE 構造'
title: CLRDATA_ADDRESS_RANGE 構造体
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5d671a08064781b71756efc3c753468e6769d4ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662339"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="12de2-103">CLRDATA_ADDRESS_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="12de2-103">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="12de2-104">アドレス範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="12de2-104">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="12de2-105">構文</span><span class="sxs-lookup"><span data-stu-id="12de2-105">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="12de2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="12de2-106">Members</span></span>

| <span data-ttu-id="12de2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="12de2-107">Member</span></span>         | <span data-ttu-id="12de2-108">説明</span><span class="sxs-lookup"><span data-stu-id="12de2-108">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="12de2-109">範囲の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="12de2-109">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="12de2-110">範囲の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="12de2-110">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="12de2-111">解説</span><span class="sxs-lookup"><span data-stu-id="12de2-111">Remarks</span></span>

<span data-ttu-id="12de2-112">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="12de2-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="12de2-113">これを使用するには、上で指定したように構造体を定義し `CLRDATA_ADDRESS` ます。は、64ビットの符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="12de2-113">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="12de2-114">要件</span><span class="sxs-lookup"><span data-stu-id="12de2-114">Requirements</span></span>

<span data-ttu-id="12de2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12de2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="12de2-116">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="12de2-116">**Header:** None</span></span>  
<span data-ttu-id="12de2-117">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="12de2-117">**Library:** None</span></span>  
<span data-ttu-id="12de2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12de2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="12de2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="12de2-119">See also</span></span>

- [<span data-ttu-id="12de2-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="12de2-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="12de2-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="12de2-121">Debugging Structures</span></span>](debugging-structures.md)
