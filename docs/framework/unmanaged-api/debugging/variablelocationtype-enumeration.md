---
description: '詳細については、次を参照してください: VariableLocationType 列挙型'
title: VariableLocationType 列挙型
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 8561077b9f3f4d318eeb743d51538b2a9a22a217
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800527"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="2b1d2-103">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="2b1d2-103">VariableLocationType Enumeration</span></span>

<span data-ttu-id="2b1d2-104">変数のネイティブな場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-104">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b1d2-105">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="2b1d2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2b1d2-106">Members</span></span>  
  
|<span data-ttu-id="2b1d2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="2b1d2-107">Member</span></span>|<span data-ttu-id="2b1d2-108">説明</span><span class="sxs-lookup"><span data-stu-id="2b1d2-108">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="2b1d2-109">変数はレジスタにあります。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-109">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="2b1d2-110">変数は、レジスタ相対メモリの場所にあります。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-110">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="2b1d2-111">変数はレジスタまたはレジスタの相対メモリ位置に格納されません。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-111">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b1d2-112">解説</span><span class="sxs-lookup"><span data-stu-id="2b1d2-112">Remarks</span></span>  

 <span data-ttu-id="2b1d2-113">列挙体のメンバー `VariableLocationType` は、 [GetLocationType](icordebugvariablehome-getlocationtype-method.md) メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-113">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b1d2-114">要件</span><span class="sxs-lookup"><span data-stu-id="2b1d2-114">Requirements</span></span>  

 <span data-ttu-id="2b1d2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b1d2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b1d2-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b1d2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b1d2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b1d2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b1d2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b1d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1d2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b1d2-119">See also</span></span>

- [<span data-ttu-id="2b1d2-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2b1d2-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
