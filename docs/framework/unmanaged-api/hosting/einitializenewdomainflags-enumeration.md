---
description: '詳細については、次を参照してください: EInitializeNewDomainFlags 列挙型'
title: EInitializeNewDomainFlags 列挙体
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: b856d061e86c0c79b35f842975378307b79a37e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785466"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="04f2c-103">EInitializeNewDomainFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="04f2c-103">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="04f2c-104">ホストがアプリケーションドメインの初期化に関する情報をランタイムに提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="04f2c-104">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="04f2c-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="04f2c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="04f2c-106">Members</span></span>  
  
|<span data-ttu-id="04f2c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="04f2c-107">Member</span></span>|<span data-ttu-id="04f2c-108">説明</span><span class="sxs-lookup"><span data-stu-id="04f2c-108">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="04f2c-109">フラグなし。</span><span class="sxs-lookup"><span data-stu-id="04f2c-109">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="04f2c-110">ホストがメソッド内のアプリケーションドメインのセキュリティ状態に変更を加えないことを、共通言語ランタイム (CLR) に通知し <xref:System.AppDomainManager.InitializeNewDomain%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="04f2c-110">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04f2c-111">解説</span><span class="sxs-lookup"><span data-stu-id="04f2c-111">Remarks</span></span>  

 <span data-ttu-id="04f2c-112">[ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)メソッドは、型のパラメーターを受け取り `EInitializeNewDomainFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="04f2c-112">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f2c-113">要件</span><span class="sxs-lookup"><span data-stu-id="04f2c-113">Requirements</span></span>  

 <span data-ttu-id="04f2c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f2c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f2c-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="04f2c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04f2c-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04f2c-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04f2c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f2c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f2c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="04f2c-118">See also</span></span>

- [<span data-ttu-id="04f2c-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="04f2c-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="04f2c-120">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="04f2c-120">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
