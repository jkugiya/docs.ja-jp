---
description: '詳細については、次を参照してください: EContextType 列挙型'
title: EContextType 列挙型
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: b7d6ddb385386bb0616a01ef6fcc432f2c925d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785533"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="280ab-103">EContextType 列挙型</span><span class="sxs-lookup"><span data-stu-id="280ab-103">EContextType Enumeration</span></span>

<span data-ttu-id="280ab-104">現在実行中のスレッドのセキュリティコンテキストを記述します。</span><span class="sxs-lookup"><span data-stu-id="280ab-104">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="280ab-105">構文</span><span class="sxs-lookup"><span data-stu-id="280ab-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="280ab-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="280ab-106">Members</span></span>  
  
|<span data-ttu-id="280ab-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="280ab-107">Member</span></span>|<span data-ttu-id="280ab-108">説明</span><span class="sxs-lookup"><span data-stu-id="280ab-108">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="280ab-109">共通言語ランタイム (CLR) が [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) メソッドを呼び出す時点での現在のスレッドのコンテキスト、または [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) メソッドの呼び出しで CLR によって要求されたコンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="280ab-109">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="280ab-110">ホストが低い特権 (ガベージコレクター、クラスまたはモジュールコンストラクターなど) を持つコンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="280ab-110">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="280ab-111">解説</span><span class="sxs-lookup"><span data-stu-id="280ab-111">Remarks</span></span>  

 <span data-ttu-id="280ab-112">CLR は、 `EContextType` メソッドとメソッドの呼び出しで、値の1つをパラメーター値として提供し `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` ます。</span><span class="sxs-lookup"><span data-stu-id="280ab-112">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="280ab-113">要件</span><span class="sxs-lookup"><span data-stu-id="280ab-113">Requirements</span></span>  

 <span data-ttu-id="280ab-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="280ab-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="280ab-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="280ab-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="280ab-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="280ab-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="280ab-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="280ab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="280ab-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="280ab-118">See also</span></span>

- [<span data-ttu-id="280ab-119">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="280ab-119">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="280ab-120">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="280ab-120">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="280ab-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="280ab-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
