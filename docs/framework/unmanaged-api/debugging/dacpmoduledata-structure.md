---
description: '詳細情報: DacpModuleData 構造体'
title: DacpModuleData 構造体
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 376a49ab78db08e5906e8d33389cdc45fe76e81e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661585"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="3b05c-103">DacpModuleData 構造体</span><span class="sxs-lookup"><span data-stu-id="3b05c-103">DacpModuleData Structure</span></span>

<span data-ttu-id="3b05c-104">モジュールのランタイム情報のトランスポートバッファーを定義します。</span><span class="sxs-lookup"><span data-stu-id="3b05c-104">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3b05c-105">構文</span><span class="sxs-lookup"><span data-stu-id="3b05c-105">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="3b05c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3b05c-106">Members</span></span>

| <span data-ttu-id="3b05c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="3b05c-107">Member</span></span>    | <span data-ttu-id="3b05c-108">説明</span><span class="sxs-lookup"><span data-stu-id="3b05c-108">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="3b05c-109">モジュールオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3b05c-109">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="3b05c-110">ポータブル実行可能 (PE) ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3b05c-110">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="3b05c-111">読み込まれたイメージのベースのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3b05c-111">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="3b05c-112">ランタイムによって使用される追加のモジュール情報のペイロードバッファー。</span><span class="sxs-lookup"><span data-stu-id="3b05c-112">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3b05c-113">解説</span><span class="sxs-lookup"><span data-stu-id="3b05c-113">Remarks</span></span>

<span data-ttu-id="3b05c-114">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="3b05c-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3b05c-115">これを使用するには、前に示したように構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="3b05c-115">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b05c-116">要件</span><span class="sxs-lookup"><span data-stu-id="3b05c-116">Requirements</span></span>

<span data-ttu-id="3b05c-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b05c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3b05c-118">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="3b05c-118">**Header:** None</span></span>  
<span data-ttu-id="3b05c-119">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="3b05c-119">**Library:** None</span></span>  
<span data-ttu-id="3b05c-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3b05c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3b05c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b05c-121">See also</span></span>

- [<span data-ttu-id="3b05c-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3b05c-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="3b05c-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="3b05c-123">Debugging Structures</span></span>](debugging-structures.md)
