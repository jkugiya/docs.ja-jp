---
description: '詳細については、次を参照してください: CorDebugHandleType 列挙型'
title: CorDebugHandleType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 294fd7b04018331489e51d12930bcbbb81ec340a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662118"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="894f0-103">CorDebugHandleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="894f0-103">CorDebugHandleType Enumeration</span></span>

<span data-ttu-id="894f0-104">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="894f0-104">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="894f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="894f0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="894f0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="894f0-106">Members</span></span>  
  
|<span data-ttu-id="894f0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="894f0-107">Member</span></span>|<span data-ttu-id="894f0-108">説明</span><span class="sxs-lookup"><span data-stu-id="894f0-108">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="894f0-109">ハンドルは strong であり、ガベージコレクションによってオブジェクトが解放されるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="894f0-109">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="894f0-110">ハンドルは脆弱であり、ガベージコレクションによってオブジェクトが解放されるのを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="894f0-110">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="894f0-111">オブジェクトが収集されると、ハンドルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="894f0-111">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="894f0-112">要件</span><span class="sxs-lookup"><span data-stu-id="894f0-112">Requirements</span></span>  

 <span data-ttu-id="894f0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="894f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="894f0-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="894f0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="894f0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="894f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="894f0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894f0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="894f0-117">See also</span></span>

- [<span data-ttu-id="894f0-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="894f0-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
