---
description: 詳細については、「CorDebugDebugEventKind 列挙型」を参照してください。
title: CorDebugDebugEventKind 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: 62094c934873a74fdab01fad87c42126e28cb0f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801710"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="b8a03-103">CorDebugDebugEventKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="b8a03-103">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="b8a03-104">[DecodeEvent](icordebugprocess6-decodeevent-method.md)メソッドによって情報がデコードされるイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b8a03-104">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a03-105">構文</span><span class="sxs-lookup"><span data-stu-id="b8a03-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="b8a03-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b8a03-106">Members</span></span>  
  
|<span data-ttu-id="b8a03-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b8a03-107">Member</span></span>|<span data-ttu-id="b8a03-108">説明</span><span class="sxs-lookup"><span data-stu-id="b8a03-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="b8a03-109">モジュールの読み込みイベント。</span><span class="sxs-lookup"><span data-stu-id="b8a03-109">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="b8a03-110">モジュールのアンロード イベント。</span><span class="sxs-lookup"><span data-stu-id="b8a03-110">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="b8a03-111">初回例外。</span><span class="sxs-lookup"><span data-stu-id="b8a03-111">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="b8a03-112">ユーザーの初回例外。</span><span class="sxs-lookup"><span data-stu-id="b8a03-112">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="b8a03-113">`catch` ハンドラーが存在する例外。</span><span class="sxs-lookup"><span data-stu-id="b8a03-113">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="b8a03-114">未処理の例外。</span><span class="sxs-lookup"><span data-stu-id="b8a03-114">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8a03-115">解説</span><span class="sxs-lookup"><span data-stu-id="b8a03-115">Remarks</span></span>  

 <span data-ttu-id="b8a03-116">この列挙体のメンバーは、 `CorDebugDebugEventKind` によっては、の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドを呼び出すことによって返されます。</span><span class="sxs-lookup"><span data-stu-id="b8a03-116">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8a03-117">この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="b8a03-117">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a03-118">要件</span><span class="sxs-lookup"><span data-stu-id="b8a03-118">Requirements</span></span>  

 <span data-ttu-id="b8a03-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a03-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a03-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8a03-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8a03-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8a03-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8a03-122">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a03-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a03-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8a03-123">See also</span></span>

- [<span data-ttu-id="b8a03-124">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b8a03-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
