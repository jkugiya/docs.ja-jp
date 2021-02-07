---
description: '詳細については、次を参照してください: CorDebugStateChange 列挙型'
title: CorDebugStateChange 列挙体
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 1900baa77432daa10d0f1a32dd9cb25198b86ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661819"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="5f50a-103">CorDebugStateChange 列挙体</span><span class="sxs-lookup"><span data-stu-id="5f50a-103">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="5f50a-104">プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。</span><span class="sxs-lookup"><span data-stu-id="5f50a-104">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f50a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f50a-105">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="5f50a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5f50a-106">Members</span></span>

| <span data-ttu-id="5f50a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="5f50a-107">Member</span></span>            | <span data-ttu-id="5f50a-108">説明</span><span class="sxs-lookup"><span data-stu-id="5f50a-108">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="5f50a-109">プロセスはフォワード実行によって新しいメモリ状態に達しています。</span><span class="sxs-lookup"><span data-stu-id="5f50a-109">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="5f50a-110">プロセスのメモリは、以前とは異なる状態になっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f50a-110">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5f50a-111">解説</span><span class="sxs-lookup"><span data-stu-id="5f50a-111">Remarks</span></span>

 <span data-ttu-id="5f50a-112">`CorDebugStateChange`デバッガーが `ProcessStateChanged` [ICorDebugProcess4::P Rocessstatechanged](icordebugprocess4-processstatechanged-method.md)または[ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)を使用してメソッドを呼び出すと、列挙体のメンバーが引数として提供されます。</span><span class="sxs-lookup"><span data-stu-id="5f50a-112">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="5f50a-113">要件</span><span class="sxs-lookup"><span data-stu-id="5f50a-113">Requirements</span></span>

 <span data-ttu-id="5f50a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f50a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5f50a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f50a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="5f50a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f50a-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="5f50a-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f50a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5f50a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f50a-118">See also</span></span>

- [<span data-ttu-id="5f50a-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="5f50a-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5f50a-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5f50a-120">Debugging</span></span>](index.md)
