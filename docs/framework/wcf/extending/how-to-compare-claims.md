---
description: '詳細については、「方法: 要求を比較する」を参照してください。'
title: '方法: クレームを比較する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: c2088ad3992852bdc12e7bcd71d5f3598a237b45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653850"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="de715-103">方法: クレームを比較する</span><span class="sxs-lookup"><span data-stu-id="de715-103">How to: Compare Claims</span></span>

<span data-ttu-id="de715-104">認証チェックを実行するには、Windows Communication Foundation (WCF) の Id モデルインフラストラクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="de715-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="de715-105">この場合、一般的なタスクとして、承認コンテキスト内のクレームが、要求されたアクションの実行や要求されたリソースへのアクセスに必要なクレームと比較されます。</span><span class="sxs-lookup"><span data-stu-id="de715-105">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="de715-106">このトピックでは、組み込みとカスタム クレームの型を含め、クレームの比較方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de715-106">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="de715-107">Id モデルインフラストラクチャの詳細については、「 [Id モデルを使用したクレームと承認の管理](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de715-107">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="de715-108">クレームの比較では、クレーム間で 3 つの部分 (型、権限、およびリソース) の比較が行われ、等しいかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="de715-108">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="de715-109">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de715-109">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="de715-110">いずれのクレームにも、クレームの型として <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、権限として <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>、および文字列リソースとして "someone" が設定されています。</span><span class="sxs-lookup"><span data-stu-id="de715-110">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="de715-111">クレームの 3 つの部分のすべてが等しいため、この 2 つのクレームは等しくなります。</span><span class="sxs-lookup"><span data-stu-id="de715-111">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="de715-112">組み込みのクレームの型の比較には、<xref:System.IdentityModel.Claims.Claim.Equals%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="de715-112">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="de715-113">必要に応じて、クレーム固有の比較コードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="de715-113">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="de715-114">たとえば、次の 2 つのユーザー プリンシパル名 (UPN) クレームがあるとします。</span><span class="sxs-lookup"><span data-stu-id="de715-114">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="de715-115">メソッドの比較コードはを <xref:System.IdentityModel.Claims.Claim.Equals%2A> 返し `true` ます。これは、 `example\someone` と同じドメインユーザーが "" として識別されることを前提として someone@example.com います。</span><span class="sxs-lookup"><span data-stu-id="de715-115">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="de715-116">カスタム クレームの型の比較にも、<xref:System.IdentityModel.Claims.Claim.Equals%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="de715-116">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="de715-117">ただし、クレームの <xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティから返された型がプリミティブ型ではない場合、<xref:System.IdentityModel.Claims.Claim.Equals%2A> が `true` を返すのは、`Resource` プロパティから返された値どうしが等しいと <xref:System.IdentityModel.Claims.Claim.Equals%2A> メソッドが見なした場合のみです。</span><span class="sxs-lookup"><span data-stu-id="de715-117">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="de715-118">これに該当しない場合は、`Resource` プロパティから返されたカスタム型で <xref:System.IdentityModel.Claims.Claim.Equals%2A> メソッドと <xref:System.Object.GetHashCode%2A> メソッドをオーバーライドし、必要なカスタム処理を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de715-118">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="de715-119">組み込みのクレームの比較</span><span class="sxs-lookup"><span data-stu-id="de715-119">Comparing built-in claims</span></span>

1. <span data-ttu-id="de715-120"><xref:System.IdentityModel.Claims.Claim> クラスの 2 つのインスタンスがある場合、次に示すコードのように、<xref:System.IdentityModel.Claims.Claim.Equals%2A> を使用して比較します。</span><span class="sxs-lookup"><span data-stu-id="de715-120">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="de715-121">カスタム クレームとプリミティブ リソース型の比較</span><span class="sxs-lookup"><span data-stu-id="de715-121">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="de715-122">プリミティブ リソース型を含むカスタム クレームでは、次のコードのように、組み込みのクレームとして比較を実行できます。</span><span class="sxs-lookup"><span data-stu-id="de715-122">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="de715-123">構造体またはクラスをベースとしたリソース型を含むカスタム クレームでは、そのリソース型で <xref:System.IdentityModel.Claims.Claim.Equals%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de715-123">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="de715-124">まず、`obj` パラメーターが `null` であるかどうかを確認し、null である場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="de715-124">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="de715-125">次に、<xref:System.Object.ReferenceEquals%2A> を呼び出し、パラメーターとして `this` と `obj` を渡します。</span><span class="sxs-lookup"><span data-stu-id="de715-125">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="de715-126">`true` が返されたら、`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="de715-126">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="de715-127">さらに、`obj` をクラスの型のローカル変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de715-127">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="de715-128">この処理が失敗すると、参照が `null` になります。</span><span class="sxs-lookup"><span data-stu-id="de715-128">If this fails, the reference is `null`.</span></span> <span data-ttu-id="de715-129">この場合、`false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="de715-129">In such cases, return `false`.</span></span>

6. <span data-ttu-id="de715-130">現在のクレームと提供されたクレームを正しく比較するために必要なカスタム比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="de715-130">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="de715-131">例</span><span class="sxs-lookup"><span data-stu-id="de715-131">Example</span></span>

<span data-ttu-id="de715-132">次の例では、クレームの型がプリミティブ型以外のカスタム クレームを比較します。</span><span class="sxs-lookup"><span data-stu-id="de715-132">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="de715-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="de715-133">See also</span></span>

- [<span data-ttu-id="de715-134">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="de715-134">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="de715-135">方法: カスタム クレームを作成する</span><span class="sxs-lookup"><span data-stu-id="de715-135">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
