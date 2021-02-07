---
description: 詳細については、「ServiceAuthorizationBehavior」を参照してください。
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: dc398621103774a04934aa23ae3d7208f4389717
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715588"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="3b2e0-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3b2e0-103">ServiceAuthorizationBehavior</span></span>

<span data-ttu-id="3b2e0-104">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3b2e0-104">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b2e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="3b2e0-105">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3b2e0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3b2e0-106">Methods</span></span>  

 <span data-ttu-id="3b2e0-107">ServiceAuthorizationBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-107">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b2e0-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3b2e0-108">Properties</span></span>  

 <span data-ttu-id="3b2e0-109">ServiceAuthorizationBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-109">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="3b2e0-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="3b2e0-110">ImpersonateCallerForAllOperations</span></span>  

 <span data-ttu-id="3b2e0-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3b2e0-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b2e0-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b2e0-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b2e0-113">受信メッセージによって提供される資格情報を使用してサービスが偽装を試みるかどうかを制御する値。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-113">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="3b2e0-114">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="3b2e0-114">PrincipalPermissionMode</span></span>  

 <span data-ttu-id="3b2e0-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3b2e0-115">Data type: string</span></span>  
  
 <span data-ttu-id="3b2e0-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b2e0-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b2e0-117">サーバーでの操作を実行するために使用されるプリンシパル。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-117">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="3b2e0-118">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="3b2e0-118">RoleProvider</span></span>  

 <span data-ttu-id="3b2e0-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3b2e0-119">Data type: string</span></span>  
  
 <span data-ttu-id="3b2e0-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b2e0-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b2e0-121">ASP.NET ロール プロバイダーの名前。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-121">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="3b2e0-122">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="3b2e0-122">ServiceAuthorizationManager</span></span>  

 <span data-ttu-id="3b2e0-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3b2e0-123">Data type: string</span></span>  
  
 <span data-ttu-id="3b2e0-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b2e0-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b2e0-125">カスタム承認で使用される承認マネージャー。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-125">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b2e0-126">要件</span><span class="sxs-lookup"><span data-stu-id="3b2e0-126">Requirements</span></span>  
  
|<span data-ttu-id="3b2e0-127">MOF</span><span class="sxs-lookup"><span data-stu-id="3b2e0-127">MOF</span></span>|<span data-ttu-id="3b2e0-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3b2e0-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3b2e0-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="3b2e0-129">Namespace</span></span>|<span data-ttu-id="3b2e0-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3b2e0-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b2e0-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b2e0-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
