---
description: '詳細情報: CLRDATA_IL_ADDRESS_MAP 構造'
title: CLRDATA_IL_ADDRESS_MAP 構造体
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 02ee14154de0c1609e58cf6a2ad1ca62710567f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801853"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="eac0e-103">CLRDATA_IL_ADDRESS_MAP 構造体</span><span class="sxs-lookup"><span data-stu-id="eac0e-103">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="eac0e-104">アドレスマッピングの IL を定義します。</span><span class="sxs-lookup"><span data-stu-id="eac0e-104">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="eac0e-105">構文</span><span class="sxs-lookup"><span data-stu-id="eac0e-105">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="eac0e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="eac0e-106">Members</span></span>

| <span data-ttu-id="eac0e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="eac0e-107">Member</span></span>         | <span data-ttu-id="eac0e-108">説明</span><span class="sxs-lookup"><span data-stu-id="eac0e-108">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="eac0e-109">含まれているアドレス範囲の IL オフセット</span><span class="sxs-lookup"><span data-stu-id="eac0e-109">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="eac0e-110">範囲の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="eac0e-110">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="eac0e-111">範囲の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="eac0e-111">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="eac0e-112">データの型。</span><span class="sxs-lookup"><span data-stu-id="eac0e-112">The type of the data.</span></span> <span data-ttu-id="eac0e-113">この値は現在使用されていません</span><span class="sxs-lookup"><span data-stu-id="eac0e-113">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="eac0e-114">解説</span><span class="sxs-lookup"><span data-stu-id="eac0e-114">Remarks</span></span>

<span data-ttu-id="eac0e-115">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="eac0e-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="eac0e-116">これを使用するには、上で指定したように構造体を定義し `CLRDATA_ADDRESS` ます。は、64ビットの符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="eac0e-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="eac0e-117">要件</span><span class="sxs-lookup"><span data-stu-id="eac0e-117">Requirements</span></span>

<span data-ttu-id="eac0e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eac0e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="eac0e-119">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="eac0e-119">**Header:** None</span></span>  
<span data-ttu-id="eac0e-120">**ライブラリ:** なし **.NET Framework バージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eac0e-120">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="eac0e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="eac0e-121">See also</span></span>

- [<span data-ttu-id="eac0e-122">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="eac0e-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="eac0e-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="eac0e-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="eac0e-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="eac0e-124">Debugging Structures</span></span>](debugging-structures.md)
