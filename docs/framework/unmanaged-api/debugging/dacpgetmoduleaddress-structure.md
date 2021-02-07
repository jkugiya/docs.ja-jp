---
description: '詳細については、次を参照してください: DacpGetModuleAddress 構造体'
title: DacpGetModuleAddress 構造体
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3de76cc4f15bffd35d7a43ae25a313eb2fe59b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661598"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="693e9-103">DacpGetModuleAddress 構造体</span><span class="sxs-lookup"><span data-stu-id="693e9-103">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="693e9-104">モジュールアドレス要求のコンテナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="693e9-104">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="693e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="693e9-105">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="693e9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="693e9-106">Members</span></span>

| <span data-ttu-id="693e9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="693e9-107">Member</span></span>      | <span data-ttu-id="693e9-108">説明</span><span class="sxs-lookup"><span data-stu-id="693e9-108">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="693e9-109">モジュールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="693e9-109">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="693e9-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="693e9-110">Methods</span></span>

| <span data-ttu-id="693e9-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="693e9-111">Method</span></span>                                                                                               | <span data-ttu-id="693e9-112">説明</span><span class="sxs-lookup"><span data-stu-id="693e9-112">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="693e9-113">Request</span><span class="sxs-lookup"><span data-stu-id="693e9-113">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="693e9-114">指定されたランタイム構造体を構造体に設定する要求を実行します。</span><span class="sxs-lookup"><span data-stu-id="693e9-114">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="693e9-115">解説</span><span class="sxs-lookup"><span data-stu-id="693e9-115">Remarks</span></span>

<span data-ttu-id="693e9-116">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="693e9-116">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="693e9-117">これを使用するには、上で指定したように構造体を定義し `CLRDATA_ADDRESS` ます。は、64ビットの符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="693e9-117">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="693e9-118">要件</span><span class="sxs-lookup"><span data-stu-id="693e9-118">Requirements</span></span>

<span data-ttu-id="693e9-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="693e9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="693e9-120">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="693e9-120">**Header:** None</span></span>  
<span data-ttu-id="693e9-121">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="693e9-121">**Library:** None</span></span>  
<span data-ttu-id="693e9-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="693e9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="693e9-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="693e9-123">See also</span></span>

- [<span data-ttu-id="693e9-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="693e9-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="693e9-125">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="693e9-125">Debugging Structures</span></span>](debugging-structures.md)
