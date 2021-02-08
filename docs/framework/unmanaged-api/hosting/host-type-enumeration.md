---
description: '詳細情報: HOST_TYPE 列挙型'
title: HOST_TYPE 列挙型
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 6a0baf3050f99885953ddec06342cbe19accfef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785238"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="537e2-103">HOST_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="537e2-103">HOST_TYPE Enumeration</span></span>

<span data-ttu-id="537e2-104">アプリケーションを起動しているホストの種類を指定する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="537e2-104">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="537e2-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="537e2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="537e2-106">Members</span></span>  
  
|<span data-ttu-id="537e2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="537e2-107">Member</span></span>|<span data-ttu-id="537e2-108">説明</span><span class="sxs-lookup"><span data-stu-id="537e2-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="537e2-109">AppLaunch.exe からアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="537e2-109">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="537e2-110">部分的に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="537e2-110">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="537e2-111">アプリケーションを直接起動します。</span><span class="sxs-lookup"><span data-stu-id="537e2-111">Launch the application directly.</span></span> <span data-ttu-id="537e2-112">つまり、アプリケーションを独自の .exe ファイルから起動します。</span><span class="sxs-lookup"><span data-stu-id="537e2-112">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="537e2-113">この値は、完全に信頼されたアプリケーションに使用します。</span><span class="sxs-lookup"><span data-stu-id="537e2-113">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="537e2-114">HOST_TYPE_APPLAUNCH と同じです。</span><span class="sxs-lookup"><span data-stu-id="537e2-114">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="537e2-115">要件</span><span class="sxs-lookup"><span data-stu-id="537e2-115">Requirements</span></span>  

 <span data-ttu-id="537e2-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="537e2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="537e2-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="537e2-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="537e2-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="537e2-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="537e2-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="537e2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537e2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="537e2-120">See also</span></span>

- [<span data-ttu-id="537e2-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="537e2-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
