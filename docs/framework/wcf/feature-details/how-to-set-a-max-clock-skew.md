---
description: '詳細については、「方法: 最大時刻のずれを設定する」を参照してください。'
title: '方法: 時刻のずれの最大値を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 688be1bb42dd7b30fce577082992741b76819e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643203"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="cb92a-103">方法: 時刻のずれの最大値を設定する</span><span class="sxs-lookup"><span data-stu-id="cb92a-103">How to: Set a Max Clock Skew</span></span>

<span data-ttu-id="cb92a-104">時刻が重要な要素となる機能は、2 台のコンピューターで時刻の設定が異なっていると失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cb92a-104">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="cb92a-105">この可能性を減らすには、`MaxClockSkew` プロパティを <xref:System.TimeSpan> に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-105">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="cb92a-106">このプロパティは、次の 2 つのクラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-106">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb92a-107">セキュリティで保護された通信を行うには、サービスまたはクライアントをブートストラップするときに、プロパティに対する変更を `MaxClockSkew` 行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb92a-107">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="cb92a-108">これを行うには、 <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティによって返されるのプロパティを設定する必要があり <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-108">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="cb92a-109">システム提供のバインディングの 1 つでこのプロパティを変更するには、バインディングのコレクションでセキュリティ バインド要素を見つけて、`MaxClockSkew` プロパティを新しい値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb92a-109">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="cb92a-110"><xref:System.ServiceModel.Channels.SecurityBindingElement> から派生される 2 つのクラスは、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> クラスおよび <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラスです。</span><span class="sxs-lookup"><span data-stu-id="cb92a-110">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="cb92a-111">コレクションからセキュリティ バインディングを取得する場合は、`MaxClockSkew` プロパティを正しく設定するために、これらの型のどちらかにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb92a-111">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="cb92a-112">次の例では、<xref:System.ServiceModel.WSHttpBinding> を使用していますが、これは <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-112">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="cb92a-113">システム指定の各バインディングで使用するセキュリティバインディングの種類を指定する一覧については、「 [システム指定](../system-provided-bindings.md)のバインディング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb92a-113">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="cb92a-114">コードを使用して時刻のずれの新しい値を持つカスタム バインドを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb92a-114">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="cb92a-115">コード内の次の名前空間への参照を追加します。 <xref:System.ServiceModel.Channels> 、、 <xref:System.ServiceModel.Description> <xref:System.Security.Permissions> 、および <xref:System.ServiceModel.Security.Tokens> 。</span><span class="sxs-lookup"><span data-stu-id="cb92a-115">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="cb92a-116"><xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、セキュリティ モードを <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-116">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="cb92a-117"><xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを呼び出して、<xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-117">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="cb92a-118"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> クラスの <xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを使用して、セキュリティ バインド要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-118">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="cb92a-119"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> メソッドを使用する場合には、実際の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="cb92a-119">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="cb92a-120">次の例では <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 型にキャストしています。</span><span class="sxs-lookup"><span data-stu-id="cb92a-120">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="cb92a-121">セキュリティ バインド要素の <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-121">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="cb92a-122">適切なサービス型とベース アドレスを使用して、<xref:System.ServiceModel.ServiceHost> を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-122">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="cb92a-123"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してエンドポイントを追加し、<xref:System.ServiceModel.Channels.CustomBinding> を含めます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-123">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="cb92a-124">構成で MaxClockSkew を設定するには</span><span class="sxs-lookup"><span data-stu-id="cb92a-124">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="cb92a-125">[\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)要素セクションでを作成し [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) ます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-125">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="cb92a-126">要素を作成 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) し、 `name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-126">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="cb92a-127">`MaxClockSkewBinding` に設定する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-127">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="cb92a-128">エンコーディング要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-128">Add an encoding element.</span></span> <span data-ttu-id="cb92a-129">次の例では、を追加し [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-129">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="cb92a-130">要素を追加 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) し、属性を `authenticationMode` 適切な設定に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-130">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="cb92a-131">次の例では、この属性を `Kerberos` に設定して、サービスが Windows 認証を使用するように指定しています。</span><span class="sxs-lookup"><span data-stu-id="cb92a-131">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="cb92a-132">を追加 [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) し、 `maxClockSkew` 属性をの形式の値に設定し `"##:##:##"` ます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-132">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="cb92a-133">次の例では 7 分に設定しています。</span><span class="sxs-lookup"><span data-stu-id="cb92a-133">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="cb92a-134">必要に応じて、を追加 [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) し、 `maxClockSkew` 属性を適切な設定に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-134">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="cb92a-135">transport 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-135">Add a transport element.</span></span> <span data-ttu-id="cb92a-136">次の例では、を使用 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) します。</span><span class="sxs-lookup"><span data-stu-id="cb92a-136">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="cb92a-137">セキュリティで保護された通信を行うには、要素のブートストラップでセキュリティ設定を行う必要があり [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) ます。</span><span class="sxs-lookup"><span data-stu-id="cb92a-137">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cb92a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb92a-138">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cb92a-139">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="cb92a-139">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
