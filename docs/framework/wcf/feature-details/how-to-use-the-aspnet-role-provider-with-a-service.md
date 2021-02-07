---
description: '詳細については、「方法: サービスで ASP.NET ロールプロバイダーを使用する」を参照してください。'
title: '方法: ASP.NET のロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 24bf9ad72d3634baf1d7120e4e60ccde5a4078a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734114"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="4dfc4-103">方法: ASP.NET のロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="4dfc4-103">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="4dfc4-104">ASP.NET ロールプロバイダー (ASP.NET メンバーシッププロバイダーと共に) は、ASP.NET 開発者がサイトを使用してアカウントを作成し、承認のためにロールを割り当てることができる Web サイトを作成できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-104">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="4dfc4-105">この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにログインしてサービスに排他的にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-105">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="4dfc4-106">これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="4dfc4-107">代わりに、資格情報 (ユーザー名とパスワードの組み合わせ) を指定するすべてのユーザーが、サイトとそのサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-107">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="4dfc4-108">サンプルアプリケーションについては、「 [メンバーシップとロールプロバイダー](../samples/membership-and-role-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="4dfc4-109">メンバーシッププロバイダーの ASP.NET 機能の詳細については、「 [方法: ASP.NET メンバーシッププロバイダーを使用](how-to-use-the-aspnet-membership-provider.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-109">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="4dfc4-110">ロール プロバイダー機能では、SQL Server データベースを使用してユーザー情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-110">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="4dfc4-111">Windows Communication Foundation (WCF) 開発者は、これらの機能をセキュリティ上の目的で利用できます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="4dfc4-112">WCF アプリケーションに統合されている場合、ユーザーは、WCF クライアントアプリケーションに対してユーザー名とパスワードの組み合わせを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-112">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="4dfc4-113">WCF でデータベースを使用できるようにするには、クラスのインスタンスを作成し、 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> その <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティをに設定 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> して、サービスをホストしているへの動作のコレクションにインスタンスを追加する必要があり <xref:System.ServiceModel.ServiceHost> ます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-113">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="4dfc4-114">ロールプロバイダーを構成する</span><span class="sxs-lookup"><span data-stu-id="4dfc4-114">Configure the role provider</span></span>  
  
1. <span data-ttu-id="4dfc4-115">Web.config ファイルの <> 要素の下に、 `system.web` <の `roleManager`> 要素を追加し、その `enabled` 属性をに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-115">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="4dfc4-116">`defaultProvider` 属性を `SqlRoleProvider` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-116">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="4dfc4-117"><> 要素の子として `roleManager` 、<> 要素を追加し `providers` ます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-117">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="4dfc4-118"><> 要素の子として、次の `providers` `add` `name` `type` `connectionStringName` `applicationName` 例に示すように、、、、およびの各属性を適切な値に設定して、<> 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-118">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="4dfc4-119">ロールプロバイダーを使用するようにサービスを構成する</span><span class="sxs-lookup"><span data-stu-id="4dfc4-119">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="4dfc4-120">Web.config ファイルで、要素を追加し [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ます。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-120">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="4dfc4-121">要素を [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) <`system.ServiceModel`> 要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-121">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="4dfc4-122">[\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<> 要素にを追加 `behaviors` します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-122">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="4dfc4-123">要素を追加 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) し、 `name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-123">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="4dfc4-124">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)<> 要素にを追加 `behavior` します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-124">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="4dfc4-125">`principalPermissionMode` 属性を `UseAspNetRoles` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-125">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="4dfc4-126">`roleProviderName` 属性を `SqlRoleProvider` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-126">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="4dfc4-127">この構成の一部を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4dfc4-127">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4dfc4-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dfc4-128">See also</span></span>

- [<span data-ttu-id="4dfc4-129">メンバーシップとロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="4dfc4-129">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="4dfc4-130">方法: ASP.NET メンバーシップ プロバイダーを使用する</span><span class="sxs-lookup"><span data-stu-id="4dfc4-130">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
