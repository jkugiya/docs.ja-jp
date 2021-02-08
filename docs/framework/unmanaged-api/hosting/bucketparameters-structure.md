---
description: '詳細については、次を参照してください: BucketParameters 構造体'
title: BucketParameters 構造体
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: e2d701caa0e2374cb6b44d5fb5537f2ecc7e34fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799968"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="8cbe8-103">BucketParameters 構造体</span><span class="sxs-lookup"><span data-stu-id="8cbe8-103">BucketParameters Structure</span></span>

<span data-ttu-id="8cbe8-104">イベントの型名と、イベントに関連付けられている現在の例外のパラメーターを格納します。</span><span class="sxs-lookup"><span data-stu-id="8cbe8-104">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbe8-105">構文</span><span class="sxs-lookup"><span data-stu-id="8cbe8-105">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="8cbe8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8cbe8-106">Members</span></span>  
  
|<span data-ttu-id="8cbe8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8cbe8-107">Member</span></span>|<span data-ttu-id="8cbe8-108">説明</span><span class="sxs-lookup"><span data-stu-id="8cbe8-108">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="8cbe8-109">`true`この構造体の残りの部分が有効な場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="8cbe8-109">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="8cbe8-110">イベントの種類の名前。</span><span class="sxs-lookup"><span data-stu-id="8cbe8-110">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="8cbe8-111">文字列の配列。各文字列は、イベントに関連付けられている現在の例外のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cbe8-111">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cbe8-112">要件</span><span class="sxs-lookup"><span data-stu-id="8cbe8-112">Requirements</span></span>  

 <span data-ttu-id="8cbe8-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cbe8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbe8-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8cbe8-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="8cbe8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbe8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cbe8-116">See also</span></span>

- [<span data-ttu-id="8cbe8-117">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="8cbe8-117">Hosting Structures</span></span>](hosting-structures.md)
