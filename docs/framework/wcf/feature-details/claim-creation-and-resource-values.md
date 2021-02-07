---
description: 詳細については、「要求の作成とリソースの値」を参照してください。
title: クレームの作成とリソース値
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 20763c683c5bf5734a21a4315576a8f9f354ff35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734985"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="c4024-103">クレームの作成とリソース値</span><span class="sxs-lookup"><span data-stu-id="c4024-103">Claim Creation and Resource Values</span></span>

<span data-ttu-id="c4024-104"><xref:System.IdentityModel.Claims.Claim> クラスには、組み込みのクレームの種類のインスタンスを作成するためのメソッドが複数用意されています。</span><span class="sxs-lookup"><span data-stu-id="c4024-104">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="c4024-105">これらのメソッドの中でも、次のものは指定されたリソースに対してセマンティックまたは形式のチェックを行いません。</span><span class="sxs-lookup"><span data-stu-id="c4024-105">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="c4024-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (長さまたはバイト配列のコンテンツは検査されません)</span><span class="sxs-lookup"><span data-stu-id="c4024-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="c4024-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (長さまたはバイト配列のコンテンツは検査されません)</span><span class="sxs-lookup"><span data-stu-id="c4024-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="c4024-108">上記のメソッドを使用する場合は、渡されるリソース値が正しい形式である、または正しい情報を含んでいること (あるいは両方) を確認するように注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4024-108">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="c4024-109">次のメソッドは、特定の型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c4024-109">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="c4024-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4024-110">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="c4024-111">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="c4024-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
