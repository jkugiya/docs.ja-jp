---
description: '詳細については、「方法: カスタム承認ポリシーを作成する」を参照してください。'
title: '方法: カスタム承認ポリシーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 41158944aec9b0a5b8cb28c51922b8a1b103317c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743708"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="22bf7-103">方法: カスタム承認ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="22bf7-103">How to: Create a Custom Authorization Policy</span></span>

<span data-ttu-id="22bf7-104">Windows Communication Foundation (WCF) の Id モデルインフラストラクチャでは、クレームベースの承認モデルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22bf7-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="22bf7-105">クレームは、トークンから抽出され、状況に応じてカスタム承認ポリシーによって処理されてから、承認決定を行う際に確認できる <xref:System.IdentityModel.Policy.AuthorizationContext> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-105">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="22bf7-106">カスタム ポリシーを使用して、入力トークンからのクレームを、アプリケーションが要求するクレームに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-106">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="22bf7-107">このようにして、アプリケーション層は、WCF がサポートするさまざまなトークンの種類によって処理されるさまざまな要求の詳細から分離できます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-107">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="22bf7-108">このトピックでは、カスタム承認ポリシーの実装方法と、サービスで使用するポリシーのコレクションにカスタム承認ポリシーを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-108">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="22bf7-109">カスタム承認ポリシーを実装するには</span><span class="sxs-lookup"><span data-stu-id="22bf7-109">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="22bf7-110"><xref:System.IdentityModel.Policy.IAuthorizationPolicy> から派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-110">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="22bf7-111">クラスのコンストラクター内で一意の文字列を生成し、プロパティがアクセスされたときにその文字列を返すことによって、読み取り専用の <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="22bf7-112">ポリシーの発行者を表す <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> を返すことによって、読み取り専用の <xref:System.IdentityModel.Claims.ClaimSet> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-112">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="22bf7-113">これは、アプリケーションを表す `ClaimSet`、または組み込み `ClaimSet` (静的な `ClaimSet` プロパティから返される <xref:System.IdentityModel.Claims.ClaimSet.System%2A> など) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-113">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="22bf7-114">次の手順に従って、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-114">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="22bf7-115">Evaluate メソッドを実装するには</span><span class="sxs-lookup"><span data-stu-id="22bf7-115">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="22bf7-116">このメソッドには、<xref:System.IdentityModel.Policy.EvaluationContext> クラスのインスタンスとオブジェクト参照の 2 つのパラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-116">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="22bf7-117">カスタム承認ポリシーがの <xref:System.IdentityModel.Claims.ClaimSet> 現在のコンテンツに関係なくインスタンスを追加する場合は、 <xref:System.IdentityModel.Policy.EvaluationContext> メソッドを呼び出し、 `ClaimSet` <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> メソッドからを返すことによって、各を追加し `true` <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-117">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="22bf7-118">`true` を返すことは、承認インフラストラクチャに対して、承認ポリシーがその処理を完了したため、もう一度呼び出す必要がないことを知らせることになります。</span><span class="sxs-lookup"><span data-stu-id="22bf7-118">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="22bf7-119">カスタム承認ポリシーで `EvaluationContext` 内に特定のクレームが既に存在するときにのみクレーム セットを追加する場合は、`ClaimSet` プロパティから返された <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> インスタンスを調べて、該当するクレームを見つけます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-119">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="22bf7-120">クレームが見つかった場合は、<xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> メソッドを呼び出して新しいクレーム セットを追加します。追加するクレーム セットがない場合は、`true` を返し、承認インフラストラクチャに承認ポリシーがその処理を完了したことを知らせます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-120">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="22bf7-121">クレームが存在しない場合は `false` を返し、他の承認ポリシーで `EvaluationContext` にさらにクレーム セットを追加する場合は、もう一度承認ポリシーを呼び出す必要があることを知らせます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-121">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="22bf7-122">より複雑な処理シナリオでは、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドの 2 番目のパラメーターを使用して、特定の評価のために <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> メソッドに対するその後の呼び出し時に承認インフラストラクチャから返される状態変数を格納します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-122">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="22bf7-123">構成を使用してカスタム承認ポリシーを指定するには</span><span class="sxs-lookup"><span data-stu-id="22bf7-123">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="22bf7-124">`policyType` 要素の `add` 要素にある `authorizationPolicies` 要素の `serviceAuthorization` 属性でカスタム承認ポリシーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-124">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="22bf7-125">コードを使用してカスタム承認ポリシーを指定するには</span><span class="sxs-lookup"><span data-stu-id="22bf7-125">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="22bf7-126"><xref:System.Collections.Generic.List%601> の <xref:System.IdentityModel.Policy.IAuthorizationPolicy> を作成します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-126">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="22bf7-127">カスタム承認ポリシーのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-127">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="22bf7-128">リストに承認ポリシー インスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-128">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="22bf7-129">カスタム承認ポリシーごとに手順 2. と 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-129">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="22bf7-130"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> プロパティにリストの読み取り専用バージョンを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="22bf7-130">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="22bf7-131">例</span><span class="sxs-lookup"><span data-stu-id="22bf7-131">Example</span></span>  

 <span data-ttu-id="22bf7-132">完成した <xref:System.IdentityModel.Policy.IAuthorizationPolicy> の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22bf7-132">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="22bf7-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="22bf7-133">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="22bf7-134">方法: クレームを比較する</span><span class="sxs-lookup"><span data-stu-id="22bf7-134">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="22bf7-135">方法: サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="22bf7-135">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="22bf7-136">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="22bf7-136">Authorization Policy</span></span>](../samples/authorization-policy.md)
