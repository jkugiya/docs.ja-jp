---
description: '詳細情報: MALLOC_TYPE 列挙型'
title: MALLOC_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: 47eb58107d79309c34af5f0acdf614804d1f208f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679802"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="488d4-103">MALLOC_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="488d4-103">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="488d4-104">割り当てられているメモリの特性を指定する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="488d4-104">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488d4-105">構文</span><span class="sxs-lookup"><span data-stu-id="488d4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="488d4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="488d4-106">Members</span></span>  
  
|<span data-ttu-id="488d4-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="488d4-107">Member</span></span>|<span data-ttu-id="488d4-108">説明</span><span class="sxs-lookup"><span data-stu-id="488d4-108">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="488d4-109">割り当てられたメモリには、実行可能ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="488d4-109">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="488d4-110">割り当てられたメモリはスレッドセーフです。</span><span class="sxs-lookup"><span data-stu-id="488d4-110">The allocated memory is thread-safe.</span></span> <span data-ttu-id="488d4-111">つまり、メモリには、同期を行わずに複数のスレッドからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="488d4-111">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="488d4-112">このフラグが設定されていない場合は、オブジェクトに対する呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="488d4-112">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="488d4-113">要件</span><span class="sxs-lookup"><span data-stu-id="488d4-113">Requirements</span></span>  

 <span data-ttu-id="488d4-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="488d4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488d4-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="488d4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="488d4-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="488d4-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="488d4-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488d4-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="488d4-118">See also</span></span>

- [<span data-ttu-id="488d4-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="488d4-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
