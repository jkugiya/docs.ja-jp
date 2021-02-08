---
description: '詳細については、次を参照してください: CorDebugIlToNativeMappingTypes 列挙型'
title: CorDebugIlToNativeMappingTypes 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: bcca11bf3c7574fe76684f6786d7408c80acfa43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801632"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="489c6-103">CorDebugIlToNativeMappingTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="489c6-103">CorDebugIlToNativeMappingTypes Enumeration</span></span>

<span data-ttu-id="489c6-104">COR_DEBUG_IL_TO_NATIVE_MAP 構造体のインスタンスによって表されるネイティブ命令の特定の範囲が、特別なコード領域に対応するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="489c6-104">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="489c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="489c6-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="489c6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="489c6-106">Members</span></span>  
  
|<span data-ttu-id="489c6-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="489c6-107">Member</span></span>|<span data-ttu-id="489c6-108">説明</span><span class="sxs-lookup"><span data-stu-id="489c6-108">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="489c6-109">ネイティブ命令の範囲は、特別なコード領域には対応していません。</span><span class="sxs-lookup"><span data-stu-id="489c6-109">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="489c6-110">ネイティブ命令の範囲は、プロローグに対応しています。</span><span class="sxs-lookup"><span data-stu-id="489c6-110">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="489c6-111">ネイティブ命令の範囲は、エピローグに相当します。</span><span class="sxs-lookup"><span data-stu-id="489c6-111">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="489c6-112">要件</span><span class="sxs-lookup"><span data-stu-id="489c6-112">Requirements</span></span>  

 <span data-ttu-id="489c6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="489c6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="489c6-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="489c6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="489c6-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="489c6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="489c6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="489c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489c6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="489c6-117">See also</span></span>

- [<span data-ttu-id="489c6-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="489c6-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="489c6-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="489c6-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
