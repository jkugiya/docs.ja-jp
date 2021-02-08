---
description: '詳細については、次を参照してください: DacpReJitData 構造体'
title: DacpReJitData 構造体
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8e8d506856dbc6579ac6ea0eee2b2088a980a315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801437"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="a3412-103">DacpReJitData 構造体</span><span class="sxs-lookup"><span data-stu-id="a3412-103">DacpReJitData Structure</span></span>

<span data-ttu-id="a3412-104">プロファイラーによってインストルメント化された特定のメソッドに関する基本情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3412-104">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a3412-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3412-105">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="a3412-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a3412-106">Members</span></span>

| <span data-ttu-id="a3412-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a3412-107">Member</span></span>           | <span data-ttu-id="a3412-108">説明</span><span class="sxs-lookup"><span data-stu-id="a3412-108">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="a3412-109">メソッドの ReJit リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="a3412-109">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="a3412-110">指定されたバージョンのメソッドの ReJit インストルメンテーションの現在の状態を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="a3412-110">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="a3412-111">メソッドの rejitted 実装のベースアドレス。</span><span class="sxs-lookup"><span data-stu-id="a3412-111">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="a3412-112">解説</span><span class="sxs-lookup"><span data-stu-id="a3412-112">Remarks</span></span>

<span data-ttu-id="a3412-113">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a3412-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a3412-114">これを使用するには、前に示したように構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3412-114">To use it, define the structure as specified above.</span></span> <span data-ttu-id="a3412-115">`ms_struct`Microsoft コンパイラを使用していない場合は、パッキングを使用して構造体を定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a3412-115">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3412-116">要件</span><span class="sxs-lookup"><span data-stu-id="a3412-116">Requirements</span></span>

<span data-ttu-id="a3412-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3412-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a3412-118">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="a3412-118">**Header:** None</span></span>  
<span data-ttu-id="a3412-119">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="a3412-119">**Library:** None</span></span>  
<span data-ttu-id="a3412-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3412-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a3412-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3412-121">See also</span></span>

- [<span data-ttu-id="a3412-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a3412-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="a3412-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a3412-123">Debugging Structures</span></span>](debugging-structures.md)
