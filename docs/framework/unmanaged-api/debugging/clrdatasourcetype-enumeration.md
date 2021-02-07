---
description: '詳細については、次を参照してください: CLRDataSourceType 列挙型'
title: CLRDataSourceType 列挙型
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 06590e21aa4cdf6e89977a79da36a413d5ff4f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747243"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="48ad7-103">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="48ad7-103">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="48ad7-104">CLRDATA_IL_ADDRESS_MAP 構造体によって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="48ad7-104">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="48ad7-105">構文</span><span class="sxs-lookup"><span data-stu-id="48ad7-105">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="48ad7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="48ad7-106">Members</span></span>

| <span data-ttu-id="48ad7-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="48ad7-107">Member</span></span>                        | <span data-ttu-id="48ad7-108">説明</span><span class="sxs-lookup"><span data-stu-id="48ad7-108">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="48ad7-109">他に何も適用されないことを示すには</span><span class="sxs-lookup"><span data-stu-id="48ad7-109">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="48ad7-110">解説</span><span class="sxs-lookup"><span data-stu-id="48ad7-110">Remarks</span></span>

<span data-ttu-id="48ad7-111">この列挙体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="48ad7-111">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="48ad7-112">これを使用するには、コードで前述したように、列挙型を定義します。</span><span class="sxs-lookup"><span data-stu-id="48ad7-112">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="48ad7-113">これは、「 `CLRDATA_ENUM` [Common Data Types](../common-data-types-unmanaged-api-reference.md)」で説明されているように、という別名でもあります。</span><span class="sxs-lookup"><span data-stu-id="48ad7-113">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="48ad7-114">要件</span><span class="sxs-lookup"><span data-stu-id="48ad7-114">Requirements</span></span>

<span data-ttu-id="48ad7-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ad7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="48ad7-116">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="48ad7-116">**Header:** None</span></span>  
<span data-ttu-id="48ad7-117">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="48ad7-117">**Library:** None</span></span>  
<span data-ttu-id="48ad7-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="48ad7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="48ad7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="48ad7-119">See also</span></span>

- [<span data-ttu-id="48ad7-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="48ad7-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="48ad7-121">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="48ad7-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
