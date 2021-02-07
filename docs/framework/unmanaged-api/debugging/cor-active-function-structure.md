---
description: '詳細情報: COR_ACTIVE_FUNCTION 構造'
title: COR_ACTIVE_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: 7cc4a314c11ca4e2cdb4fe2b4090c471bcda26d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747226"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="b9365-103">COR_ACTIVE_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="b9365-103">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="b9365-104">スレッドのフレームで現在アクティブな機能に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9365-104">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="b9365-105">この構造体は、 [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9365-105">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9365-106">構文</span><span class="sxs-lookup"><span data-stu-id="b9365-106">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="b9365-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b9365-107">Members</span></span>  
  
|<span data-ttu-id="b9365-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="b9365-108">Member</span></span>|<span data-ttu-id="b9365-109">説明</span><span class="sxs-lookup"><span data-stu-id="b9365-109">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="b9365-110">フィールドのアプリケーションドメイン所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="b9365-110">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="b9365-111">フィールドのモジュール所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="b9365-111">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="b9365-112">フィールドの関数所有者へのポインター `ilOffset` 。</span><span class="sxs-lookup"><span data-stu-id="b9365-112">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="b9365-113">フレームの MSIL (Microsoft 中間言語) オフセット。</span><span class="sxs-lookup"><span data-stu-id="b9365-113">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="b9365-114">将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="b9365-114">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9365-115">要件</span><span class="sxs-lookup"><span data-stu-id="b9365-115">Requirements</span></span>  

 <span data-ttu-id="b9365-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9365-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9365-117">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="b9365-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b9365-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9365-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9365-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9365-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9365-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9365-120">See also</span></span>

- [<span data-ttu-id="b9365-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="b9365-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b9365-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b9365-122">Debugging</span></span>](index.md)
