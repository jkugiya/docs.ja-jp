---
description: 詳細については、「Corthreadsaf Etyoptions 列挙型」を参照してください。
title: CorThreadSafetyOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707320"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="4c567-103">CorThreadSafetyOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="4c567-103">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="4c567-104">スレッド セーフのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c567-104">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c567-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c567-105">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="4c567-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4c567-106">Members</span></span>

|<span data-ttu-id="4c567-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4c567-107">Member</span></span>|<span data-ttu-id="4c567-108">説明</span><span class="sxs-lookup"><span data-stu-id="4c567-108">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="4c567-109">既定値です。</span><span class="sxs-lookup"><span data-stu-id="4c567-109">Default value.</span></span> <span data-ttu-id="4c567-110">`MDThreadSafetyOff` と同じ。</span><span class="sxs-lookup"><span data-stu-id="4c567-110">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="4c567-111">リーダー/ライターロックを設定できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4c567-111">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="4c567-112">リーダー/ライターロックを設定できることを示します。</span><span class="sxs-lookup"><span data-stu-id="4c567-112">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="4c567-113">要件</span><span class="sxs-lookup"><span data-stu-id="4c567-113">Requirements</span></span>

<span data-ttu-id="4c567-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c567-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4c567-115">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="4c567-115">**Header:** CorHdr.h</span></span>

<span data-ttu-id="4c567-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c567-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4c567-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c567-117">See also</span></span>

- [<span data-ttu-id="4c567-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="4c567-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
