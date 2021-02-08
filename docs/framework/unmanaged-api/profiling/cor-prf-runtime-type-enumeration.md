---
description: '詳細情報: COR_PRF_RUNTIME_TYPE 列挙型'
title: COR_PRF_RUNTIME_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: 8f4b4a0c51c43b1db97b511387eaee1aee79f523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789046"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="75ab7-103">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="75ab7-103">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="75ab7-104">Silverlight で使用される共通言語ランタイム (CLR) のバージョンを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="75ab7-104">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ab7-105">構文</span><span class="sxs-lookup"><span data-stu-id="75ab7-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="75ab7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="75ab7-106">Members</span></span>  
  
|<span data-ttu-id="75ab7-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="75ab7-107">Member</span></span>|<span data-ttu-id="75ab7-108">説明</span><span class="sxs-lookup"><span data-stu-id="75ab7-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="75ab7-109">CLR のデスクトップバージョン。</span><span class="sxs-lookup"><span data-stu-id="75ab7-109">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="75ab7-110">Silverlight で使用される CLR のコアバージョン。</span><span class="sxs-lookup"><span data-stu-id="75ab7-110">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75ab7-111">解説</span><span class="sxs-lookup"><span data-stu-id="75ab7-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ab7-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="75ab7-112">Requirements</span></span>  

 <span data-ttu-id="75ab7-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75ab7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ab7-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75ab7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75ab7-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75ab7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75ab7-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ab7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ab7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="75ab7-117">See also</span></span>

- [<span data-ttu-id="75ab7-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="75ab7-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
