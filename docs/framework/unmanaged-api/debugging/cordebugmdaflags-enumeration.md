---
description: 詳細については、「CorDebugMDAFlags 列挙型」を参照してください。
title: CorDebugMDAFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: d7e9178d76286b112035729e997b1f68e2a93fb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661936"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="f8676-103">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8676-103">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="f8676-104">マネージド デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8676-104">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8676-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8676-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f8676-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f8676-106">Members</span></span>  
  
|<span data-ttu-id="f8676-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f8676-107">Member</span></span>|<span data-ttu-id="f8676-108">説明</span><span class="sxs-lookup"><span data-stu-id="f8676-108">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="f8676-109">Mda が起動されてから、MDA が起動されたスレッドが遅れています。</span><span class="sxs-lookup"><span data-stu-id="f8676-109">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8676-110">解説</span><span class="sxs-lookup"><span data-stu-id="f8676-110">Remarks</span></span>  

 <span data-ttu-id="f8676-111">呼び出し履歴で、MDA が最初に発生した場所が記述されなくなった場合、スレッドは *遅れ* ていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="f8676-111">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="f8676-112">これは、スレッドが終了時に無効な操作を実行したことによって発生する異常な状況です。</span><span class="sxs-lookup"><span data-stu-id="f8676-112">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8676-113">要件</span><span class="sxs-lookup"><span data-stu-id="f8676-113">Requirements</span></span>  

 <span data-ttu-id="f8676-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8676-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8676-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8676-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8676-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8676-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8676-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8676-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8676-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8676-118">See also</span></span>

- [<span data-ttu-id="f8676-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f8676-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
