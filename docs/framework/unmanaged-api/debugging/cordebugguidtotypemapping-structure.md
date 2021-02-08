---
description: 詳細については、CorDebugGuidToTypeMapping 構造体
title: CorDebugGuidToTypeMapping 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: 5f6e99a17483b4fc16eb36ebb5fb5fd81380944b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801619"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="f4fbf-103">CorDebugGuidToTypeMapping 構造体</span><span class="sxs-lookup"><span data-stu-id="f4fbf-103">CorDebugGuidToTypeMapping Structure</span></span>

<span data-ttu-id="f4fbf-104">Windows ランタイム GUID を対応するテキストオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="f4fbf-104">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4fbf-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4fbf-105">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="f4fbf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f4fbf-106">Members</span></span>  
  
|<span data-ttu-id="f4fbf-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f4fbf-107">Member</span></span>|<span data-ttu-id="f4fbf-108">説明</span><span class="sxs-lookup"><span data-stu-id="f4fbf-108">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="f4fbf-109">キャッシュされた Windows ランタイムの種類の GUID。</span><span class="sxs-lookup"><span data-stu-id="f4fbf-109">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="f4fbf-110">キャッシュされた型に関する情報を提供する、テキストオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f4fbf-110">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4fbf-111">要件</span><span class="sxs-lookup"><span data-stu-id="f4fbf-111">Requirements</span></span>  

 <span data-ttu-id="f4fbf-112">**プラットフォーム:** Windows ランタイム。</span><span class="sxs-lookup"><span data-stu-id="f4fbf-112">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="f4fbf-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4fbf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4fbf-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4fbf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4fbf-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4fbf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fbf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4fbf-116">See also</span></span>

- [<span data-ttu-id="f4fbf-117">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="f4fbf-117">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f4fbf-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f4fbf-118">Debugging</span></span>](index.md)
