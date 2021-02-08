---
description: '詳細については、次を参照してください: CorDeclSecurity 列挙型'
title: CorDeclSecurity 列挙型
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 4c4b57c09ea8b3ec1b98ff120d72a5920dc5aa4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784549"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="00ef8-103">CorDeclSecurity 列挙型</span><span class="sxs-lookup"><span data-stu-id="00ef8-103">CorDeclSecurity Enumeration</span></span>

<span data-ttu-id="00ef8-104">宣言型セキュリティを使用して実行できるセキュリティ アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="00ef8-104">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ef8-105">構文</span><span class="sxs-lookup"><span data-stu-id="00ef8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="00ef8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="00ef8-106">Members</span></span>  
  
|<span data-ttu-id="00ef8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="00ef8-107">Member</span></span>|<span data-ttu-id="00ef8-108">説明</span><span class="sxs-lookup"><span data-stu-id="00ef8-108">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="00ef8-109">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-109">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="00ef8-110">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-110">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="00ef8-111">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-111">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="00ef8-112">呼び出し履歴の上位にあるすべての呼び出し元には、現在のアクセス許可オブジェクトで指定されたアクセス許可が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ef8-112">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="00ef8-113">スタック内の上位の呼び出し元にリソースへのアクセス許可が付与されていない場合でも、呼び出し元のコードは、現在のアクセス許可オブジェクトによって識別されるリソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-113">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="00ef8-114">現在のアクセス許可オブジェクトによって指定されたリソースにアクセスする権限は、呼び出し元に対してアクセス許可が付与されている場合でも、拒否されます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-114">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="00ef8-115">他のリソースにアクセスできるアクセス許可がコードに付与されていても、このアクセス許可オブジェクトで指定されたリソースにしかアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="00ef8-115">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="00ef8-116">直前の呼び出し元には、指定された期間の指定したアクセス許可が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ef8-116">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="00ef8-117">別のクラスを継承する派生クラス、またはメソッドをオーバーライドする派生クラスには、指定されたアクセス許可が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ef8-117">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="00ef8-118">呼び出し元は、コードを実行するために必要な最小限のアクセス許可を要求できます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-118">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="00ef8-119">この操作は、アセンブリのスコープ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-119">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="00ef8-120">呼び出し元は、オプションである (実行に必須ではない) 追加のアクセス許可を要求できます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-120">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="00ef8-121">この要求は、個別に要求されていない、他のすべてのアクセス許可を暗黙的に拒否します。</span><span class="sxs-lookup"><span data-stu-id="00ef8-121">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="00ef8-122">この操作は、アセンブリのスコープ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-122">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="00ef8-123">誤用される可能性のあるアクセス許可に対する呼び出し元の要求は付与されません。</span><span class="sxs-lookup"><span data-stu-id="00ef8-123">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="00ef8-124">この操作は、アセンブリのスコープ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="00ef8-124">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="00ef8-125">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-125">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="00ef8-126">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-126">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="00ef8-127">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-127">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="00ef8-128">直接の呼び出し元には、指定したアクセス許可が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ef8-128">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="00ef8-129">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-129">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="00ef8-130">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-130">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="00ef8-131">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-131">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="00ef8-132">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-132">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="00ef8-133">予約済み。</span><span class="sxs-lookup"><span data-stu-id="00ef8-133">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00ef8-134">要件</span><span class="sxs-lookup"><span data-stu-id="00ef8-134">Requirements</span></span>  

 <span data-ttu-id="00ef8-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ef8-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ef8-136">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="00ef8-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00ef8-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ef8-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ef8-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="00ef8-138">See also</span></span>

- [<span data-ttu-id="00ef8-139">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="00ef8-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
