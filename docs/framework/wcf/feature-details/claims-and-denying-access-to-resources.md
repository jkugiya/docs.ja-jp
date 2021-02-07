---
description: '詳細情報: リソースへのアクセスの要求と拒否'
title: リソースへのアクセスのクレームと拒否
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 0bbef26b0df06305db4ce460da4ba6177c79f56a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734972"
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="3e16e-103">リソースへのアクセスのクレームと拒否</span><span class="sxs-lookup"><span data-stu-id="3e16e-103">Claims and Denying Access to Resources</span></span>

<span data-ttu-id="3e16e-104">Windows Communication Foundation (WCF) は、クレームベースの承認メカニズムをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3e16e-104">Windows Communication Foundation (WCF) supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="3e16e-105">クレームの有無に応じてリソースへのアクセスが許可されるばかりでなく、クレームの有無に応じてリソースへのアクセスがシステムによって拒否される場合もよくあります。</span><span class="sxs-lookup"><span data-stu-id="3e16e-105">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="3e16e-106">このようなシステムでは、アクセスが許可された要求を探す前に、アクセスが拒否されたクレームの <xref:System.IdentityModel.Policy.AuthorizationContext> を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e16e-106">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="3e16e-107">たとえば、`Age` 型、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限、`Under 21` リソース値というクレームを持つ任意のユーザーに対してリソースへのアクセスを拒否し、ID が `Name` 型、<xref:System.IdentityModel.Claims.Rights.Identity%2A> 権限、`Mallory` リソース値というクレームを持っている場合にのみ、リソースへのアクセスを許可するとします。</span><span class="sxs-lookup"><span data-stu-id="3e16e-107">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="3e16e-108">言い換えると、年齢が 21 歳以下の任意のユーザーはシステムによってアクセスが拒否され、名前が Mallory である任意のユーザーにはアクセスが許可されるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e16e-108">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="3e16e-109">この意味を正しく実装するには、`Age` クレームを最初に探して、ユーザーが 21 歳以下であるかどうかを判断することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3e16e-109">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="3e16e-110">そうしないと、Mallory が 21 歳以下である場合、このリソースには、`Name` クレームのみに基づいてアクセスが許可されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="3e16e-110">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e16e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e16e-111">See also</span></span>

- [<span data-ttu-id="3e16e-112">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="3e16e-112">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="3e16e-113">クレームとトークン</span><span class="sxs-lookup"><span data-stu-id="3e16e-113">Claims and Tokens</span></span>](claims-and-tokens.md)
