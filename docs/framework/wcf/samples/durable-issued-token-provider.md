---
description: '詳細情報: 永続的に発行されたトークンプロバイダー'
title: 永続性発行済みトークン プロバイダー
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: dfde4efa961704659d9d1de6010b16616467a779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793273"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="b108f-103">永続性発行済みトークン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="b108f-103">Durable Issued Token Provider</span></span>

<span data-ttu-id="b108f-104">このサンプルでは、カスタム クライアントの発行済みトークン プロバイダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b108f-104">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b108f-105">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="b108f-105">Discussion</span></span>  

 <span data-ttu-id="b108f-106">Windows Communication Foundation (WCF) のトークンプロバイダーは、セキュリティインフラストラクチャに資格情報を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-106">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="b108f-107">一般的に、トークン プロバイダーは、ターゲットをチェックし、適切な証明書を発行して、セキュリティ インフラストラクチャがメッセージのセキュリティを保護できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b108f-107">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="b108f-108">WCF には、CardSpace トークンプロバイダーが付属しています。</span><span class="sxs-lookup"><span data-stu-id="b108f-108">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="b108f-109">カスタム トークン プロバイダーは、次の場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b108f-109">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="b108f-110">組み込みのトークン プロバイダが連係動作できない資格情報ストアがある場合。</span><span class="sxs-lookup"><span data-stu-id="b108f-110">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="b108f-111">ユーザーが資格情報を使用するときに、ユーザーが詳細情報を提供した時点から資格情報を変換するための独自のカスタムメカニズムを提供する場合。</span><span class="sxs-lookup"><span data-stu-id="b108f-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="b108f-112">カスタム トークンを構築している場合。</span><span class="sxs-lookup"><span data-stu-id="b108f-112">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="b108f-113">このサンプルでは、セキュリティ トークン サービス (STS) によって発行されたトークンをキャッシュする、カスタム トークン プロバイダーを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b108f-113">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="b108f-114">このサンプルに示されている手順の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b108f-114">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="b108f-115">クライアントをカスタム トークン プロバイダーを使用して構成する手順。</span><span class="sxs-lookup"><span data-stu-id="b108f-115">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="b108f-116">発行済みトークンをキャッシュし、WCF クライアントに提供する方法。</span><span class="sxs-lookup"><span data-stu-id="b108f-116">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="b108f-117">サーバーがクライアントによってサーバーの X.509 証明書を使用して認証される手順。</span><span class="sxs-lookup"><span data-stu-id="b108f-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="b108f-118">このサンプルは、クライアント コンソール プログラム (Client.exe)、セキュリティ トークン サービス コンソール プログラム (Securitytokenservice.exe)、およびサービス コンソール プログラム (Service.exe) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b108f-118">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="b108f-119">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="b108f-119">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b108f-120">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="b108f-120">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="b108f-121">クライアントは、セキュリティ トークンをセキュリティ トークン サービス (STS) から取得し、指定された算術演算を実行する同期要求をサービスに対して行います。サービスは、結果を添えて応答します。</span><span class="sxs-lookup"><span data-stu-id="b108f-121">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="b108f-122">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-122">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b108f-123">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b108f-123">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b108f-124">このサンプルでは、を使用して ICalculator コントラクトを公開し [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b108f-124">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="b108f-125">このバインディングのクライアント側の構成は、次のコードに示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="b108f-125">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="b108f-126">`security` の `wsFederationHttpBinding` 要素では、使用するセキュリティ モードは `mode` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-126">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="b108f-127">このサンプルでは、メッセージ セキュリティが使用されています。このため、`message` の `wsFederationHttpBinding` 要素が `security` の `wsFederationHttpBinding` 要素の内側で指定されています。</span><span class="sxs-lookup"><span data-stu-id="b108f-127">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="b108f-128">`issuer` の `wsFederationHttpBinding` 要素の内側にある `message` の `wsFederationHttpBinding` 要素は、セキュリティ トークンをクライアントに発行するセキュリティ トークン サービスのアドレスとバインディングを指定します。これにより、クライアントが Calculator サービスに認証されるようになります。</span><span class="sxs-lookup"><span data-stu-id="b108f-128">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="b108f-129">このバインディングのサービス側の構成は、次のコードに示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="b108f-129">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="b108f-130">`security` の `wsFederationHttpBinding` 要素では、使用するセキュリティ モードは `mode` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-130">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="b108f-131">このサンプルでは、メッセージ セキュリティが使用されています。このため、`message` の `wsFederationHttpBinding` 要素が `security` の `wsFederationHttpBinding` 要素の内側で指定されています。</span><span class="sxs-lookup"><span data-stu-id="b108f-131">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="b108f-132">`issuerMetadata` の `wsFederationHttpBinding` 要素の内側にある `message` の `wsFederationHttpBinding` 要素は、セキュリティ トークン サービスのメタデータ取得に使用できるエンドポイントのアドレスと ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="b108f-132">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="b108f-133">このサービスの動作を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b108f-133">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="b108f-134">`issuedTokenAuthentication` 要素の内側にある `serviceCredentials` 要素を使用すると、サービスは、認証時にクライアントが提示できるトークンに関する制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b108f-134">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="b108f-135">この構成の指定では、サブジェクト名が CN=STS である証明書によって署名されたトークンがサービスによって受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="b108f-135">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="b108f-136">セキュリティ トークン サービスは、標準の wsHttpBinding を使用して、単一のエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="b108f-136">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="b108f-137">セキュリティ トークン サービスは、クライアントからのトークンの要求に応答し、クライアントが Windows アカウントを使用して認証していることを前提として、クライアントのユーザー名がクレームとして含まれているトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="b108f-137">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="b108f-138">セキュリティ トークン サービスは、トークン作成の一環として、CN=STS 証明書に関連付けられている秘密キーを使用して、トークンに署名します。</span><span class="sxs-lookup"><span data-stu-id="b108f-138">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="b108f-139">また、対称キーを作成し、CN=localhost 証明書に関連付けられている秘密キーを使用して暗号化します。</span><span class="sxs-lookup"><span data-stu-id="b108f-139">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="b108f-140">セキュリティ トークン サービスは、トークンをクライアントに返すときに、対称キーも返します。</span><span class="sxs-lookup"><span data-stu-id="b108f-140">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="b108f-141">クライアントは、発行されたトークンを Calculator サービスに提示し、対称キーを使用してメッセージに署名することで対称キーを認識していることを証明します。</span><span class="sxs-lookup"><span data-stu-id="b108f-141">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="b108f-142">カスタム クライアント資格情報とトークン プロバイダ</span><span class="sxs-lookup"><span data-stu-id="b108f-142">Custom Client Credentials and Token Provider</span></span>  

 <span data-ttu-id="b108f-143">次の手順では、発行されたトークンをキャッシュし、WCF: security に統合するカスタムトークンプロバイダーを開発する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b108f-143">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="b108f-144">カスタム トークン プロバイダーを開発するには</span><span class="sxs-lookup"><span data-stu-id="b108f-144">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="b108f-145">カスタム トークン プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b108f-145">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="b108f-146">サンプルでは、キャッシュから取得したセキュリティ トークンを返すカスタム トークン プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="b108f-146">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="b108f-147">このタスクを実行するため、カスタム トークン プロバイダーは <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスを派生し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b108f-147">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="b108f-148">このメソッドは、キャッシュ内のトークンの取得を試行します。キャッシュ内にトークンが見つからない場合は、基になるプロバイダからトークンを取得してキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="b108f-148">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="b108f-149">どちらの場合も、メソッドは `SecurityToken` を返します。</span><span class="sxs-lookup"><span data-stu-id="b108f-149">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="b108f-150">カスタム セキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b108f-150">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="b108f-151"><xref:System.IdentityModel.Selectors.SecurityTokenManager> は、<xref:System.IdentityModel.Selectors.SecurityTokenProvider> メソッド内で渡される特定の <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> の `CreateSecurityTokenProvider` の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-151">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="b108f-152">セキュリティ トークン マネージャーは、トークン認証システムとトークン シリアライザーの作成にも使用されますが、このサンプルでは扱っていません。</span><span class="sxs-lookup"><span data-stu-id="b108f-152">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="b108f-153">このサンプルでは、カスタム セキュリティ トークン マネージャーは <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承し、`CreateSecurityTokenProvider` メソッドをオーバーライドして、渡されたトークンの要件で発行済みトークンが必要であることが示されている場合にはカスタム トークン プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="b108f-153">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="b108f-154">カスタム クライアント資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="b108f-154">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="b108f-155">クライアント資格情報クラスは、クライアント プロキシ用に構成された資格情報を表すために使用され、トークン認証システム、トークン プロバイダ、およびトークン シリアライザの取得に使用されるセキュリティ トークン マネージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="b108f-155">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="b108f-156">トークン キャッシュを実装します。</span><span class="sxs-lookup"><span data-stu-id="b108f-156">Implement the token cache.</span></span> <span data-ttu-id="b108f-157">サンプルの実装では抽象基本クラスを使用し、トークン キャッシュの利用先ではこのクラスを通じてキャッシュとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="b108f-157">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="b108f-158">クライアントがカスタム クライアント資格情報を使用するため、サンプルでは既定のクライアント資格情報を削除し、新しいクライアント資格情報クラスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="b108f-158">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="b108f-159">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="b108f-159">Running the sample</span></span>  

 <span data-ttu-id="b108f-160">サンプルの実行方法を次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="b108f-160">See the following instructions to run the sample.</span></span> <span data-ttu-id="b108f-161">サンプルを実行すると、セキュリティ トークン要求がセキュリティ トークン サービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-161">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="b108f-162">操作要求と応答は、クライアントとサービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-162">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="b108f-163">いずれかのコンソール ウィンドウで Enter キーを押すと、アプリケーションがシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="b108f-163">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="b108f-164">Setup.cmd バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="b108f-164">The Setup.cmd Batch File</span></span>  

 <span data-ttu-id="b108f-165">このサンプルに用意されている Setup.cmd バッチ ファイルを使用すると、適切な証明書を使用してサーバーとセキュリティ トークン サービスを構成し、自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b108f-165">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="b108f-166">このバッチ ファイルにより、CurrentUser/TrustedPeople 証明書ストアのどちらにも 2 つの証明書が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-166">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="b108f-167">片方の証明書は CN=STS のサブジェクト名を持ち、クライアントに発行するセキュリティ トークンを署名するためにセキュリティ トークン サービスが使用します。</span><span class="sxs-lookup"><span data-stu-id="b108f-167">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="b108f-168">もう片方の証明書は CN=localhost のサブジェクト名を持ち、サービスが暗号化を解除できるようにシークレットを暗号化するためにセキュリティ トークン サービスが使用します。</span><span class="sxs-lookup"><span data-stu-id="b108f-168">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b108f-169">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b108f-169">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b108f-170">setup.cmd ファイルを実行して、必要な証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="b108f-170">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="b108f-171">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b108f-171">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="b108f-172">ソリューション内のすべてのプロジェクトがビルドされていることを確認します (Shared、RSTRSTR、Service、SecurityTokenService、Client)。</span><span class="sxs-lookup"><span data-stu-id="b108f-172">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="b108f-173">Service.exe と SecurityTokenService.exe がどちらも管理者権限で実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b108f-173">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="b108f-174">client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="b108f-174">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b108f-175">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="b108f-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="b108f-176">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="b108f-176">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b108f-177">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b108f-177">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b108f-178">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b108f-178">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b108f-179">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b108f-179">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b108f-180">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b108f-180">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
