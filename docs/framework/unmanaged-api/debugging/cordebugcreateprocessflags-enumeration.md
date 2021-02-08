---
description: '詳細については、次を参照してください: CorDebugCreateProcessFlags 列挙型'
title: CorDebugCreateProcessFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: 29363510c83873c7f367079857809c165bc55b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801736"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="5bf28-103">CorDebugCreateProcessFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="5bf28-103">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="5bf28-104">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md)メソッドの呼び出しで使用できる追加のデバッグオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="5bf28-104">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf28-105">構文</span><span class="sxs-lookup"><span data-stu-id="5bf28-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5bf28-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5bf28-106">Members</span></span>  
  
|<span data-ttu-id="5bf28-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="5bf28-107">Member</span></span>|<span data-ttu-id="5bf28-108">説明</span><span class="sxs-lookup"><span data-stu-id="5bf28-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="5bf28-109">特別なオプションは設定されていません。</span><span class="sxs-lookup"><span data-stu-id="5bf28-109">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bf28-110">要件</span><span class="sxs-lookup"><span data-stu-id="5bf28-110">Requirements</span></span>  

 <span data-ttu-id="5bf28-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bf28-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf28-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bf28-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bf28-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bf28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bf28-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf28-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bf28-115">See also</span></span>

- [<span data-ttu-id="5bf28-116">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="5bf28-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
