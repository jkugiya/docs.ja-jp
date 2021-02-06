---
description: 詳細については、「WCF での承認」を参照してください。
title: WCF での承認
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 3fda699a33d8b512d047232398e9cfac63661a85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643710"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="d62da-103">WCF での承認</span><span class="sxs-lookup"><span data-stu-id="d62da-103">Authorization in WCF</span></span>

<span data-ttu-id="d62da-104">承認は、サービスやファイルなどのリソースへのアクセスと権限を制御するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d62da-104">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="d62da-105">このセクションのトピックでは、さまざまな方法で Windows Communication Foundation (WCF) でこの基本的なタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d62da-105">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d62da-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d62da-106">In This Section</span></span>  

 [<span data-ttu-id="d62da-107">Access Control のメカニズム</span><span class="sxs-lookup"><span data-stu-id="d62da-107">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="d62da-108">WCF の承認メカニズムの概要と、推奨される使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d62da-108">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="d62da-109">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="d62da-109">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="d62da-110"><xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用してサービスへのアクセスを制限するプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="d62da-110">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="d62da-111">方法: ASP.NET のロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="d62da-111">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="d62da-112">サービスの構成に従って、ASP.NET のロールプロバイダー機能を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d62da-112">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="d62da-113">方法: ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="d62da-113">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="d62da-114">ASP.NET は、承認マネージャーを使用して、Web サイトの承認を管理できます。</span><span class="sxs-lookup"><span data-stu-id="d62da-114">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="d62da-115">WCF では、クライアントの承認に ASP.NET/Authorization Manager の組み合わせを利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d62da-115">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="d62da-116">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="d62da-116">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="d62da-117">ID モデル インフラストラクチャをクレーム ベースの承認に使用する際の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="d62da-117">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="d62da-118">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="d62da-118">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="d62da-119">委任と偽装の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d62da-119">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d62da-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d62da-120">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="d62da-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d62da-121">Related Sections</span></span>  

 [<span data-ttu-id="d62da-122">認証</span><span class="sxs-lookup"><span data-stu-id="d62da-122">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="d62da-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d62da-123">See also</span></span>

- [<span data-ttu-id="d62da-124">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="d62da-124">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="d62da-125">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d62da-125">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
