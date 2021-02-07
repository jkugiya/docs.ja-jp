---
description: '詳細情報: COR_DEBUG_IL_TO_NATIVE_MAP 構造'
title: COR_DEBUG_IL_TO_NATIVE_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: ec722b86f95e75d4ac00e04e8a602c6b6da64de5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747193"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="91591-103">COR_DEBUG_IL_TO_NATIVE_MAP 構造体</span><span class="sxs-lookup"><span data-stu-id="91591-103">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>

<span data-ttu-id="91591-104">Microsoft intermediate language (MSIL) コードをネイティブ コードにマップするために使用するオフセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="91591-104">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91591-105">構文</span><span class="sxs-lookup"><span data-stu-id="91591-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="91591-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="91591-106">Members</span></span>  
  
|<span data-ttu-id="91591-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="91591-107">Member</span></span>|<span data-ttu-id="91591-108">説明</span><span class="sxs-lookup"><span data-stu-id="91591-108">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="91591-109">MSIL コードのオフセット。</span><span class="sxs-lookup"><span data-stu-id="91591-109">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="91591-110">ネイティブコードの開始位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="91591-110">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="91591-111">ネイティブコードの末尾のオフセット。</span><span class="sxs-lookup"><span data-stu-id="91591-111">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91591-112">要件</span><span class="sxs-lookup"><span data-stu-id="91591-112">Requirements</span></span>  

 <span data-ttu-id="91591-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91591-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91591-114">**ヘッダー:** Corprof.idl、CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="91591-114">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="91591-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91591-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91591-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91591-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91591-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="91591-117">See also</span></span>

- [<span data-ttu-id="91591-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="91591-118">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="91591-119">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="91591-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="91591-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="91591-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="91591-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="91591-121">Debugging</span></span>](index.md)
