---
description: 詳細については、SAML トークンプロバイダーに関するページを参照してください。
title: SAML トークン プロバイダー
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: f65d34732c14bc1d3a442b9aacda1621995c975e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703693"
---
# <a name="saml-token-provider"></a><span data-ttu-id="0c2b9-103">SAML トークン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0c2b9-103">SAML Token Provider</span></span>

<span data-ttu-id="0c2b9-104">このサンプルでは、カスタム クライアントの SAML トークン プロバイダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-104">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="0c2b9-105">Windows Communication Foundation (WCF) のトークンプロバイダーは、セキュリティインフラストラクチャに資格情報を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-105">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="0c2b9-106">一般的に、トークン プロバイダーは、ターゲットをチェックし、適切な証明書を発行して、セキュリティ インフラストラクチャがメッセージのセキュリティを保護できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="0c2b9-107">WCF には、既定の資格情報マネージャートークンプロバイダーが付属しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-107">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="0c2b9-108">また、WCF には、CardSpace トークンプロバイダーも付属しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-108">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="0c2b9-109">カスタム トークン プロバイダーは、次の場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-109">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="0c2b9-110">トークン プロバイダーが連携動作できない資格情報ストアがある場合。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-110">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="0c2b9-111">ユーザーが資格情報を使用するときに、ユーザーが詳細情報を提供した時点から資格情報を変換するための独自のカスタムメカニズムを提供する場合。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="0c2b9-112">カスタム トークンを構築している場合。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-112">If you are building a custom token.</span></span>

 <span data-ttu-id="0c2b9-113">このサンプルでは、WCF クライアントフレームワークの外部から取得した SAML トークンを使用できるようにするカスタムトークンプロバイダーを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-113">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="0c2b9-114">このサンプルに示されている手順の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-114">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="0c2b9-115">クライアントをカスタム トークン プロバイダーを使用して構成する手順。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="0c2b9-116">SAML トークンをカスタム クライアント資格情報に渡す手順。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-116">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="0c2b9-117">SAML トークンを WCF クライアントフレームワークに提供する方法。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-117">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="0c2b9-118">サーバーがクライアントによってサーバーの X.509 証明書を使用して認証される手順。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-118">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="0c2b9-119">サービスは、構成ファイル App.config を使用して定義された、サービスと通信するための2つのエンドポイントを公開します。各エンドポイントは、アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-119">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0c2b9-120">バインディングの構成には、標準の `wsFederationHttpBinding` が使用されます。これはメッセージ セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-120">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="0c2b9-121">1 つのエンドポイントは、クライアントが対称証明キーを使用する SAML トークンで認証を行うことを想定しています。これに対してもう 1 つのエンドポイントでは、クライアントが非対称証明キーを使用する SAML トークンで認証を行うことを想定しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-121">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="0c2b9-122">また、サービスは `serviceCredentials` 動作を使用してサービス証明書の構成も行います。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-122">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="0c2b9-123">`serviceCredentials` 動作を使用すると、サービス証明書を構成できます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-123">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="0c2b9-124">クライアントはサービス証明書を使用して、サービスを認証し、メッセージを保護します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-124">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="0c2b9-125">次の構成では、このトピックの最後のセットアップ手順で説明しているサンプル セットアップでインストールされる "localhost" 証明書を参照しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-125">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="0c2b9-126">`serviceCredentials` 動作を使用すると、SAML トークンに署名する信頼できる証明書を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-126">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="0c2b9-127">次の構成では、サンプルでインストールされる 'Alice' 証明書を参照しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-127">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="0c2b9-128">次の手順は、カスタム SAML トークンプロバイダーを開発し、WCF: security framework と統合する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-128">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="0c2b9-129">カスタムの SAML トークン プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-129">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="0c2b9-130">サンプルでは、構築時に提供される SAML アサーションに基づいてセキュリティ トークンを返す、カスタムの SAML トークン プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-130">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="0c2b9-131">このタスクを実行するため、カスタム トークン プロバイダーは <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスから派生し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-131">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="0c2b9-132">このメソッドは、新しい `SecurityToken` を作成して返します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-132">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="0c2b9-133">カスタム セキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-133">Write custom security token manager.</span></span>

     <span data-ttu-id="0c2b9-134"><xref:System.IdentityModel.Selectors.SecurityTokenManager> クラスは、<xref:System.IdentityModel.Selectors.SecurityTokenProvider> メソッド内で渡される特定の <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> の `CreateSecurityTokenProvider` の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-134">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="0c2b9-135">セキュリティ トークン マネージャーは、トークン認証システムとトークン シリアライザーの作成にも使用されますが、このサンプルでは扱っていません。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-135">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="0c2b9-136">このサンプルでは、カスタム セキュリティ トークン マネージャーは <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承し、渡されたトークンの要件で SAML トークンが必要であることが示されている場合に、`CreateSecurityTokenProvider` メソッドをオーバーライドしてカスタムの SAML トークン プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-136">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="0c2b9-137">クライアント資格情報クラス (手順 3. を参照) がアサーションを指定していない場合、セキュリティ トークン マネージャーは適切なインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-137">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="0c2b9-138">カスタム クライアント資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-138">Write a custom client credential.</span></span>

     <span data-ttu-id="0c2b9-139">クライアント資格情報クラスは、クライアント プロキシ用に構成された資格情報を表すために使用され、トークン認証システム、トークン プロバイダー、およびトークン シリアライザーの取得に使用されるセキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-139">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="0c2b9-140">カスタム クライアント資格情報を使用するようクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-140">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="0c2b9-141">サンプルでは既定のクライアント資格情報を削除し、新しいクライアント資格情報クラスを提供して、クライアントがカスタム クライアント資格情報を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-141">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="0c2b9-142">サービスでは、呼び出し元に関連するクレームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-142">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="0c2b9-143">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-143">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0c2b9-144">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-144">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="0c2b9-145">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="0c2b9-145">Setup Batch File</span></span>

 <span data-ttu-id="0c2b9-146">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-146">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="0c2b9-147">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-147">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="0c2b9-148">次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-148">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="0c2b9-149">サーバー証明書の作成 :</span><span class="sxs-lookup"><span data-stu-id="0c2b9-149">Creating the server certificate:</span></span>

     <span data-ttu-id="0c2b9-150">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-150">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="0c2b9-151">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-151">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="0c2b9-152">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-152">Change this variable to specify your own server name.</span></span> <span data-ttu-id="0c2b9-153">このバッチ ファイルでの既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-153">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="0c2b9-154">証明書は、LocalMachine ストアの場所の My (Personal) ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-154">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="0c2b9-155">クライアントの信頼された証明書ストアへのサーバー証明書のインストール。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-155">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="0c2b9-156">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-156">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0c2b9-157">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-157">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0c2b9-158">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-158">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="0c2b9-159">発行元の証明書の作成</span><span class="sxs-lookup"><span data-stu-id="0c2b9-159">Creating the issuer certificate.</span></span>

     <span data-ttu-id="0c2b9-160">Setup.bat バッチ ファイルの次の行は、使用する発行元の証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-160">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="0c2b9-161">`%USER_NAME%` 変数は発行元の名前です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-161">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="0c2b9-162">この変数を変更して、使用する発行元の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-162">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="0c2b9-163">このバッチ ファイルでの既定値は Alice です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-163">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="0c2b9-164">証明書は、CurrentUser 保存場所の My ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-164">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="0c2b9-165">サーバーの信頼された証明書ストアへの発行元証明書のインストール</span><span class="sxs-lookup"><span data-stu-id="0c2b9-165">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="0c2b9-166">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-166">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0c2b9-167">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-167">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0c2b9-168">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、サーバー証明書ストアに発行元証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-168">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="0c2b9-169">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="0c2b9-169">To set up and build the sample</span></span>

1. <span data-ttu-id="0c2b9-170">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-170">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0c2b9-171">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-171">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0c2b9-172">Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-172">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0c2b9-173">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0c2b9-173">To run the sample on the same computer</span></span>

1. <span data-ttu-id="0c2b9-174">管理者特権で実行する Visual Studio 2012 コマンドプロンプト内のサンプルのインストールフォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-174">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="0c2b9-175">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-175">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0c2b9-176">Setup.bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-176">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="0c2b9-177">Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルを含むディレクトリを指します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-177">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="0c2b9-178">Service.exe を service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-178">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="0c2b9-179">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-179">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="0c2b9-180">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-180">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="0c2b9-181">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-181">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0c2b9-182">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0c2b9-182">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="0c2b9-183">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-183">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="0c2b9-184">サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-184">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="0c2b9-185">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-185">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="0c2b9-186">コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-186">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="0c2b9-187">新しい証明書名を反映するには、Service.exe.config ファイルを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-187">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="0c2b9-188">サーバー証明書を作成するには、Setup.bat バッチ ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-188">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="0c2b9-189">setup.bat ファイルは、管理者特権で開いた Visual Studio ウィンドウの開発者コマンドプロンプトで実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-189">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="0c2b9-190">`%SERVER_NAME%` 変数には、サービスをホストするコンピューターの完全修飾ホスト名を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-190">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="0c2b9-191">サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-191">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="0c2b9-192">この手順は、サーバー証明書の発行元をクライアントが信頼できる場合は不要です。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-192">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="0c2b9-193">サービス コンピューターの Service.exe.config ファイルで、ベース アドレスの値を localhost から完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-193">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="0c2b9-194">サービス コンピューターで、コマンド プロンプトから Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-194">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="0c2b9-195">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-195">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="0c2b9-196">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-196">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="0c2b9-197">クライアント コンピューターで、コマンド プロンプト ウィンドウから `Client.exe` を起動します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-197">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="0c2b9-198">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-198">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0c2b9-199">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="0c2b9-199">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="0c2b9-200">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="0c2b9-200">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
