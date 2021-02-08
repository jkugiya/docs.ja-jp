---
description: '詳細情報: 動作のセキュリティ'
title: 動作のセキュリティ
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: ba245a2c9558d40f22b9126ee0cf1560ed700ce8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778712"
---
# <a name="behavior-security"></a><span data-ttu-id="29f24-103">動作のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="29f24-103">Behavior Security</span></span>

<span data-ttu-id="29f24-104">このセクションには、サービスの動作に対するセキュリティの構成を示すサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="29f24-104">This section includes samples that demonstrate configuring security for service behaviors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29f24-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="29f24-105">In This Section</span></span>  

 [<span data-ttu-id="29f24-106">サービス監査動作</span><span class="sxs-lookup"><span data-stu-id="29f24-106">Service Auditing Behavior</span></span>](service-auditing-behavior.md)  
 <span data-ttu-id="29f24-107">このサンプルでは、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を使用して、サービス操作中にセキュリティ イベントの監査を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29f24-107">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span>  
  
 [<span data-ttu-id="29f24-108">メンバーシップとロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="29f24-108">Membership and Role Provider</span></span>](membership-and-role-provider.md)  
 <span data-ttu-id="29f24-109">このサンプルでは、サービスが ASP.NET のメンバーシップとロールプロバイダーを使用して、クライアントを認証および承認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29f24-109">This sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 [<span data-ttu-id="29f24-110">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="29f24-110">Authorizing Access to Service Operations</span></span>](authorizing-access-to-service-operations.md)  
 <span data-ttu-id="29f24-111">このサンプルでは、を使用して、 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) サービス操作へのアクセスを承認するために属性を使用できるようにする方法を示し <xref:System.Security.Permissions.PrincipalPermissionAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="29f24-111">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span>  
  
 [<span data-ttu-id="29f24-112">クライアントの偽装</span><span class="sxs-lookup"><span data-stu-id="29f24-112">Impersonating the Client</span></span>](impersonating-the-client.md)  
 <span data-ttu-id="29f24-113">サービスで呼び出し元のアプリケーションを偽装し、サービスが呼び出し元の代わりにシステム リソースにアクセスできるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29f24-113">This sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>
