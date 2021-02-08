---
description: '詳細については、次を参照してください: CorDebugDecodeEventFlagsWindows 列挙型'
title: CorDebugDecodeEventFlagsWindows 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: 765ce4b967d00bd70becca666e2ed418614d6fe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801697"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="10857-103">CorDebugDecodeEventFlagsWindows 列挙体</span><span class="sxs-lookup"><span data-stu-id="10857-103">CorDebugDecodeEventFlagsWindows Enumeration</span></span>

<span data-ttu-id="10857-104">Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="10857-104">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10857-105">構文</span><span class="sxs-lookup"><span data-stu-id="10857-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="10857-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="10857-106">Members</span></span>  
  
|<span data-ttu-id="10857-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="10857-107">Member</span></span>|<span data-ttu-id="10857-108">説明</span><span class="sxs-lookup"><span data-stu-id="10857-108">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="10857-109">デバッグ イベントが初回例外であることを示します。</span><span class="sxs-lookup"><span data-stu-id="10857-109">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10857-110">解説</span><span class="sxs-lookup"><span data-stu-id="10857-110">Remarks</span></span>  

 <span data-ttu-id="10857-111">[ICorDebugProcess6::D ecodeevent](icordebugprocess6-decodeevent-method.md)メソッドには、 `dwFlags` デバッグイベントに関する追加情報を提供し、ターゲットアーキテクチャに依存する値を持つパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="10857-111">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="10857-112">`CorDebugDecodeEventFlagsWindows` 列挙体は、Windows プラットフォームでデバッグ イベントと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="10857-112">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10857-113">この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="10857-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10857-114">要件</span><span class="sxs-lookup"><span data-stu-id="10857-114">Requirements</span></span>  

 <span data-ttu-id="10857-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10857-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10857-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10857-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10857-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10857-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10857-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10857-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10857-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="10857-119">See also</span></span>

- [<span data-ttu-id="10857-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="10857-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
