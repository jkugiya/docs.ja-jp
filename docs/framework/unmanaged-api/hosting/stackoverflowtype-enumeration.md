---
description: '詳細については、次を参照してください: StackOverflowType 列挙型'
title: StackOverflowType 列挙型
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: d39ccd99331a3e839236f1ede21254edb92b2dfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679356"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="adfa0-103">StackOverflowType 列挙型</span><span class="sxs-lookup"><span data-stu-id="adfa0-103">StackOverflowType Enumeration</span></span>

<span data-ttu-id="adfa0-104">スタックオーバーフローイベントの根底にある原因を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="adfa0-104">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adfa0-105">構文</span><span class="sxs-lookup"><span data-stu-id="adfa0-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="adfa0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="adfa0-106">Members</span></span>  
  
|<span data-ttu-id="adfa0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="adfa0-107">Member</span></span>|<span data-ttu-id="adfa0-108">説明</span><span class="sxs-lookup"><span data-stu-id="adfa0-108">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="adfa0-109">スタックオーバーフローは、実行エンジンによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="adfa0-109">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="adfa0-110">スタックオーバーフローは、マネージコードによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="adfa0-110">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="adfa0-111">スタックオーバーフローは、アンマネージコードによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="adfa0-111">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adfa0-112">解説</span><span class="sxs-lookup"><span data-stu-id="adfa0-112">Remarks</span></span>  

 <span data-ttu-id="adfa0-113">この情報は、 [Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md) メソッドの呼び出しによってホストに渡されます。</span><span class="sxs-lookup"><span data-stu-id="adfa0-113">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adfa0-114">要件</span><span class="sxs-lookup"><span data-stu-id="adfa0-114">Requirements</span></span>  

 <span data-ttu-id="adfa0-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adfa0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adfa0-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="adfa0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adfa0-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adfa0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adfa0-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adfa0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adfa0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="adfa0-119">See also</span></span>

- [<span data-ttu-id="adfa0-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="adfa0-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
