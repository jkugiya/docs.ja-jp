---
description: '詳細情報: トークン認証システム'
title: トークン認証システム
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 086b2e8d8e9538710a315b79ad2d5be3969bb00e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668579"
---
# <a name="token-authenticator"></a><span data-ttu-id="eeb2d-103">トークン認証システム</span><span class="sxs-lookup"><span data-stu-id="eeb2d-103">Token Authenticator</span></span>

<span data-ttu-id="eeb2d-104">このサンプルでは、カスタム トークンの認証システムを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-104">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="eeb2d-105">Windows Communication Foundation (WCF) のトークン認証システムは、メッセージで使用されるトークンを検証し、それが自己整合していることを確認し、トークンに関連付けられている id を認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-105">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="eeb2d-106">カスタム トークン認証システムは次のようなさまざまな場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-106">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="eeb2d-107">トークンに関連付けられた既定の認証機構をオーバーライドする場合。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-107">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="eeb2d-108">カスタム トークンを構築している場合。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-108">When you are building a custom token.</span></span>

 <span data-ttu-id="eeb2d-109">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="eeb2d-110">クライアントがユーザー名/パスワードの組み合わせを使用して認証する方法。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-110">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="eeb2d-111">サーバーがカスタム トークン認証システムを使用してクライアント資格情報を検証する方法。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-111">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="eeb2d-112">WCF サービスコードがカスタムトークン認証システムと連携する方法。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-112">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="eeb2d-113">サーバーの X.509 証明書を使用してそのサーバーを認証する方法。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-113">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="eeb2d-114">このサンプルでは、カスタムトークン認証プロセスの後に、WCF から呼び出し元の id にアクセスする方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-114">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="eeb2d-115">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは App.config 構成ファイルで定義します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-115">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="eeb2d-116">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="eeb2d-117">バインディングの構成には、標準の `wsHttpBinding` が使用されます。このセキュリティ モードは、`wsHttpBinding` の既定モードであるメッセージに設定されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-117">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="eeb2d-118">このサンプルは、クライアント ユーザー名認証を使用するように標準の `wsHttpBinding`を設定します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-118">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="eeb2d-119">また、サービスは `serviceCredentials` 動作を使用してサービス証明書の構成も行います。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-119">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="eeb2d-120">`securityCredentials` 動作を使用すると、サービス証明書を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-120">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="eeb2d-121">クライアントはサービス証明書を使用して、サービスを認証し、メッセージを保護します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-121">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="eeb2d-122">次の構成では、次のセットアップ手順で説明しているサンプル セットアップでインストールされる localhost 証明書を参照しています。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-122">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="eeb2d-123">クライアント エンドポイント構成は、構成名、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="eeb2d-124">クライアント バインディングは、適切な `Mode` と `clientCredentialType` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-124">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 <span data-ttu-id="eeb2d-125">クライアント実装では、使用するユーザー名とパスワードが設定されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-125">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="eeb2d-126">カスタム トークン認証システム</span><span class="sxs-lookup"><span data-stu-id="eeb2d-126">Custom Token Authenticator</span></span>

 <span data-ttu-id="eeb2d-127">カスタム トークン認証システムを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-127">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="eeb2d-128">カスタム トークン認証システムを作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-128">Write a custom token authenticator.</span></span>

     <span data-ttu-id="eeb2d-129">このサンプルは、ユーザー名が有効な電子メール形式であることを検証するカスタム トークン認証システムを実装しています。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-129">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="eeb2d-130">この実装は <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator> から派生します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-130">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="eeb2d-131">このクラスで最も重要なメソッドは <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29> です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-131">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="eeb2d-132">このメソッドで、認証システムはユーザー名の形式を検証し、さらに、ホスト名が非承認のドメインのものでないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-132">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="eeb2d-133">どちらの条件も満たされる場合は、<xref:System.IdentityModel.Policy.IAuthorizationPolicy> インスタンスの読み取り専用のコレクションを返します。次にこれを使用して、ユーザー名トークン内に格納されている情報を表すクレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-133">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="eeb2d-134">カスタム トークン認証システムによって返された承認ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-134">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="eeb2d-135">このサンプルでは、<xref:System.IdentityModel.Policy.IAuthorizationPolicy> という名前の `UnconditionalPolicy` の独自の実装を示します。これにより、コンストラクター内でこのポリシーに渡されたクレームと ID のセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-135">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="eeb2d-136">カスタム セキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-136">Write a custom security token manager.</span></span>

     <span data-ttu-id="eeb2d-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> は、<xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> メソッド内でカスタム セキュリティ トークン マネージャーに渡される特定の <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> オブジェクトを対象とした `CreateSecurityTokenAuthenticator` の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="eeb2d-138">セキュリティ トークン マネージャーは、トークン プロバイダーとトークン シリアライザーの作成にも使用されますが、このサンプルでは扱っていません。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-138">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="eeb2d-139">このサンプルでは、カスタム セキュリティ トークン マネージャーは <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスを継承し、渡されたトークンの要件でユーザー名認証システムが必要であることが示されている場合に、`CreateSecurityTokenAuthenticator` メソッドをオーバーライドしてユーザー名トークンのカスタム認証システムを返します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="eeb2d-140">カスタム サービス資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-140">Write a custom service credential.</span></span>

     <span data-ttu-id="eeb2d-141">サービス資格情報クラスは、サービス用に構成された資格情報を表すために使用され、トークン認証システム、トークン プロバイダー、およびトークン シリアライザーの取得に使用されるセキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-141">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="eeb2d-142">カスタム サービス資格情報を使用するようサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-142">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="eeb2d-143">サービスでカスタム サービス資格情報を使用するには、既定のサービス資格情報に事前構成されているサービス証明書をキャプチャした後で既定のサービス資格情報クラスを削除し、事前構成されているサービス証明書を使用するよう新しいサービス資格情報のインスタンスを構成します。さらに、この新しいサービス資格情報のインスタンスをサービス動作に追加します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-143">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="eeb2d-144">呼び出し元の情報を表示するには、次のコードに示すように <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-144">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="eeb2d-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> には、現在のユーザーに関する情報が保持されています。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="eeb2d-146">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="eeb2d-147">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="eeb2d-148">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="eeb2d-148">Setup Batch File</span></span>

 <span data-ttu-id="eeb2d-149">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-149">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="eeb2d-150">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="eeb2d-151">次に、バッチ ファイルのセクションのうち、適切な構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="eeb2d-152">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-152">Creating the server certificate.</span></span>

     <span data-ttu-id="eeb2d-153">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="eeb2d-154">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="eeb2d-155">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="eeb2d-156">このバッチ ファイルでの既定は localhost です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-156">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="eeb2d-157">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-157">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="eeb2d-158">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="eeb2d-159">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="eeb2d-160">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="eeb2d-161">セットアップ バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-161">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="eeb2d-162">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="eeb2d-163">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="eeb2d-164">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="eeb2d-164">To set up and build the sample</span></span>

1. <span data-ttu-id="eeb2d-165">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="eeb2d-166">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="eeb2d-167">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="eeb2d-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="eeb2d-168">管理者特権で Visual Studio 2012 コマンドプロンプトを開き、サンプルのインストールフォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="eeb2d-169">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eeb2d-170">Setup.bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="eeb2d-171">Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルを含むディレクトリを指します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="eeb2d-172">service.exe を \service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="eeb2d-173">client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-173">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="eeb2d-174">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="eeb2d-175">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="eeb2d-176">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="eeb2d-176">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="eeb2d-177">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-177">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="eeb2d-178">サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-178">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="eeb2d-179">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-179">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="eeb2d-180">コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-180">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="eeb2d-181">新しい証明書名を反映するには、サービスの App.config ファイルを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-181">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="eeb2d-182">`%SERVER_NAME%` 変数を、サービスを実行するコンピューターの完全修飾ホスト名に設定している場合は、Setup.bat を使用してこの証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-182">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="eeb2d-183">setup.bat ファイルは、管理者特権で開いた Visual Studio の開発者コマンドプロンプトから実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-183">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="eeb2d-184">サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-184">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="eeb2d-185">サーバー証明書の発行元をクライアントが信頼できる場合を除き、この操作は不要です。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-185">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="eeb2d-186">サービス コンピューターの App.config ファイルで、ベース アドレスの値を localhost から完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-186">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="eeb2d-187">サービス コンピューターで、コマンド プロンプトから service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-187">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="eeb2d-188">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-188">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="eeb2d-189">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-189">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="eeb2d-190">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-190">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="eeb2d-191">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="eeb2d-192">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="eeb2d-192">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="eeb2d-193">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="eeb2d-193">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
