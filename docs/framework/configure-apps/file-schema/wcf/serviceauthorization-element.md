---
description: '詳細情報: <serviceAuthorization> 要素'
title: <serviceAuthorization> 要素
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: ee447f487027ed12f829dd0fd364556ce095d7d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682931"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="62048-103">\<serviceAuthorization> 要素</span><span class="sxs-lookup"><span data-stu-id="62048-103">\<serviceAuthorization> element</span></span>

<span data-ttu-id="62048-104">サービス操作へのアクセスを許可する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="62048-104">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="62048-105">構文</span><span class="sxs-lookup"><span data-stu-id="62048-105">Syntax</span></span>

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62048-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="62048-106">Attributes and elements</span></span>

<span data-ttu-id="62048-107">次のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="62048-107">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="62048-108">属性</span><span class="sxs-lookup"><span data-stu-id="62048-108">Attributes</span></span>

|<span data-ttu-id="62048-109">属性</span><span class="sxs-lookup"><span data-stu-id="62048-109">Attribute</span></span>|<span data-ttu-id="62048-110">説明</span><span class="sxs-lookup"><span data-stu-id="62048-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62048-111">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="62048-111">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="62048-112">サービスのすべての操作が呼び出し元を偽装するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="62048-112">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="62048-113">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="62048-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="62048-114">特定のサービス操作が呼び出し元を偽装する場合、スレッド コンテキストは、指定されたサービスを実行する前に呼び出し元のコンテキストに切り替えられます。</span><span class="sxs-lookup"><span data-stu-id="62048-114">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="62048-115">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="62048-115">principalPermissionMode</span></span>|<span data-ttu-id="62048-116">サーバーでの操作を実行するために使用されるプリンシパルを設定します。</span><span class="sxs-lookup"><span data-stu-id="62048-116">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="62048-117">次の値があります。</span><span class="sxs-lookup"><span data-stu-id="62048-117">Values include the following:</span></span><br /><br /> <span data-ttu-id="62048-118">-なし</span><span class="sxs-lookup"><span data-stu-id="62048-118">-   None</span></span><br /><span data-ttu-id="62048-119">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="62048-119">-   UseWindowsGroups</span></span><br /><span data-ttu-id="62048-120">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="62048-120">-   UseAspNetRoles</span></span><br /><span data-ttu-id="62048-121">-カスタム</span><span class="sxs-lookup"><span data-stu-id="62048-121">-   Custom</span></span><br /><br /> <span data-ttu-id="62048-122">既定値は UseWindowsGroups です。</span><span class="sxs-lookup"><span data-stu-id="62048-122">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="62048-123">値は、<xref:System.ServiceModel.Description.PrincipalPermissionMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="62048-123">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="62048-124">この属性の使用方法の詳細については、「 [方法: PrincipalPermissionAttribute クラスを使用してアクセスを制限する](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-124">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="62048-125">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="62048-125">roleProviderName</span></span>|<span data-ttu-id="62048-126">Windows Communication Foundation (WCF) アプリケーションにロール情報を提供するロール プロバイダーの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="62048-126">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="62048-127">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="62048-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="62048-128">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="62048-128">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="62048-129">サービス承認マネージャーの型を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="62048-129">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="62048-130">詳細については、「<xref:System.ServiceModel.ServiceAuthorizationManager>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-130">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="62048-131">子要素</span><span class="sxs-lookup"><span data-stu-id="62048-131">Child elements</span></span>

|<span data-ttu-id="62048-132">要素</span><span class="sxs-lookup"><span data-stu-id="62048-132">Element</span></span>|<span data-ttu-id="62048-133">説明</span><span class="sxs-lookup"><span data-stu-id="62048-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62048-134">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="62048-134">authorizationPolicies</span></span>|<span data-ttu-id="62048-135">`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="62048-135">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="62048-136">各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。</span><span class="sxs-lookup"><span data-stu-id="62048-136">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="62048-137">この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="62048-137">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="62048-138">アクセス制御は、それに基づいて許可または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="62048-138">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="62048-139">詳細については、「<xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-139">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="62048-140">親要素</span><span class="sxs-lookup"><span data-stu-id="62048-140">Parent elements</span></span>

|<span data-ttu-id="62048-141">要素</span><span class="sxs-lookup"><span data-stu-id="62048-141">Element</span></span>|<span data-ttu-id="62048-142">説明</span><span class="sxs-lookup"><span data-stu-id="62048-142">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="62048-143">サービスの動作設定のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="62048-143">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="62048-144">解説</span><span class="sxs-lookup"><span data-stu-id="62048-144">Remarks</span></span>

<span data-ttu-id="62048-145">このセクションには、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62048-145">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="62048-146">`principalPermissionMode` 属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="62048-146">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="62048-147">既定値は `UseWindowsGroups` で、リソースにアクセスしようとしている ID を、"Administrators" や "Users" などの Windows グループから検索するように指定します。</span><span class="sxs-lookup"><span data-stu-id="62048-147">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="62048-148">`UseAspNetRoles` \<system.web> 次のコードに示すように、要素の下に構成されているカスタムロールプロバイダーを使用するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="62048-148">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```
  
<span data-ttu-id="62048-149">次のコードは、 `roleProviderName` 属性で使用されるを示してい `principalPermissionMode` ます。</span><span class="sxs-lookup"><span data-stu-id="62048-149">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="62048-150">この構成要素の使用例については、「 [サービス操作](../../../wcf/samples/authorizing-access-to-service-operations.md) と [承認ポリシー](../../../wcf/samples/authorization-policy.md)へのアクセスの承認」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-150">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="62048-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="62048-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="62048-152">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="62048-152">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="62048-153">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="62048-153">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="62048-154">方法: サービスで使用するカスタム承認マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="62048-154">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="62048-155">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="62048-155">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="62048-156">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="62048-156">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
