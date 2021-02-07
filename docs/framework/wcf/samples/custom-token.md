---
description: '詳細情報: カスタムトークン'
title: カスタム トークン
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 500cc187db0280e508ef079ca370483c716ea2c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752432"
---
# <a name="custom-token"></a><span data-ttu-id="e7878-103">カスタム トークン</span><span class="sxs-lookup"><span data-stu-id="e7878-103">Custom Token</span></span>

<span data-ttu-id="e7878-104">このサンプルでは、カスタムトークンの実装を Windows Communication Foundation (WCF) アプリケーションに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7878-104">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e7878-105">この例では、`CreditCardToken` を使用して、クライアントのクレジット カードに関する情報をサーバーに安全に渡します。</span><span class="sxs-lookup"><span data-stu-id="e7878-105">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="e7878-106">このトークンは、WS-Security メッセージ ヘッダー内で渡され、対称セキュリティ バインド要素を使用してメッセージ本文と他のメッセージ ヘッダーと共に署名および暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-106">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="e7878-107">これは、組み込みのトークンでは不十分な場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e7878-107">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="e7878-108">このサンプルでは、組み込みのトークンのいずれかを使用する代わりに、カスタム セキュリティ トークンをサービスに提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7878-108">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="e7878-109">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7878-109">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="e7878-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7878-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="e7878-111">このサンプルに示されている手順の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e7878-111">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="e7878-112">クライアントがカスタム セキュリティ トークンをサービスに渡す方法。</span><span class="sxs-lookup"><span data-stu-id="e7878-112">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="e7878-113">サービスがカスタム セキュリティ トークンを使用および検証する方法。</span><span class="sxs-lookup"><span data-stu-id="e7878-113">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="e7878-114">WCF サービスコードが、カスタムセキュリティトークンを含む、受信したセキュリティトークンに関する情報を取得する方法。</span><span class="sxs-lookup"><span data-stu-id="e7878-114">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="e7878-115">サーバーの X.509 証明書を使用して、メッセージの暗号化や署名に使用する対称キーを保護する方法。</span><span class="sxs-lookup"><span data-stu-id="e7878-115">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="e7878-116">カスタム セキュリティ トークンを使用したクライアント認証</span><span class="sxs-lookup"><span data-stu-id="e7878-116">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="e7878-117">サービスは単一エンドポイントを公開します。エンドポイントは、`BindingHelper` クラスと `EchoServiceHost` クラスを使用してプログラムによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-117">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="e7878-118">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-118">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e7878-119">バインディングは、`SymmetricSecurityBindingElement` と `HttpTransportBindingElement` を使用して、カスタム バインディングとして構成されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-119">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="e7878-120">このサンプルでは、`SymmetricSecurityBindingElement` を設定してサービスの X.509 証明書を使用し、送信中の対称キーを保護して、WS-Security メッセージ ヘッダー内でカスタム `CreditCardToken` を署名および暗号化されたセキュリティ トークンとして渡します。</span><span class="sxs-lookup"><span data-stu-id="e7878-120">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="e7878-121">この動作により、クライアント認証に使用されるサービス資格情報と、サービス X.509 証明書に関する情報が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-121">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="e7878-122">メッセージ内のクレジット カード トークンを使用するため、このサンプルではカスタム サービス資格情報を使用してこの機能を実現します。</span><span class="sxs-lookup"><span data-stu-id="e7878-122">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="e7878-123">サービス資格情報クラスは `CreditCardServiceCredentials` クラス内にあり、`EchoServiceHost.InitializeRuntime` メソッド内のサービス ホストの動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-123">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 <span data-ttu-id="e7878-124">クライアント エンドポイントは、サービス エンドポイントと同様の方法で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-124">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="e7878-125">クライアントは、同じ `BindingHelper` クラスを使用してバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-125">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="e7878-126">セットアップの残りの部分は、`Client` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="e7878-126">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="e7878-127">クライアントはさらに、`CreditCardToken` インスタンスを適切なデータと共にクライアント エンドポイントの動作コレクションに追加することによって、`CreditCardClientCredentials` に含まれる情報とサービス X.509 証明書に関する情報をセットアップ コード内に設定します。</span><span class="sxs-lookup"><span data-stu-id="e7878-127">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="e7878-128">サンプルでは、サービス証明書として、サブジェクト名が `CN=localhost` に設定された X.509 証明書を使用しています。</span><span class="sxs-lookup"><span data-stu-id="e7878-128">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="e7878-129">カスタム セキュリティ トークンの実装</span><span class="sxs-lookup"><span data-stu-id="e7878-129">Custom Security Token Implementation</span></span>

 <span data-ttu-id="e7878-130">WCF でカスタムセキュリティトークンを有効にするには、カスタムセキュリティトークンのオブジェクト表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-130">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="e7878-131">サンプルのこの表現は、`CreditCardToken` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="e7878-131">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="e7878-132">このオブジェクト表現は、セキュリティ トークンのすべての関連情報を保持し、セキュリティ トークンに含まれるセキュリティ キーのリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7878-132">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="e7878-133">この場合、クレジット カード セキュリティ トークンにはセキュリティ キーが含まれません。</span><span class="sxs-lookup"><span data-stu-id="e7878-133">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="e7878-134">次のセクションでは、カスタムトークンをネットワーク経由で送信し、WCF エンドポイントで使用できるようにするために行う必要がある操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7878-134">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="e7878-135">カスタム クレジット カード トークンのメッセージへの提供とメッセージからの取得</span><span class="sxs-lookup"><span data-stu-id="e7878-135">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="e7878-136">WCF のセキュリティトークンシリアライザーは、メッセージの XML からセキュリティトークンのオブジェクト表現を作成し、セキュリティトークンの XML 形式を作成する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="e7878-136">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="e7878-137">また、セキュリティ トークンを指すキー識別子の読み取りと書き込みなど、他の機能も備えていますが、この例ではセキュリティ トークン関連の機能だけを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7878-137">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="e7878-138">カスタム トークンを有効にするには、独自のセキュリティ トークン シリアライザーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7878-138">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="e7878-139">このサンプルでは、この目的のために `CreditCardSecurityTokenSerializer` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7878-139">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="e7878-140">サービス側では、カスタム シリアライザーは XML 形式のカスタム トークンを読み取り、そこからカスタム トークンのオブジェクト表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-140">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="e7878-141">クライアント側では、`CreditCardSecurityTokenSerializer` クラスが、セキュリティ トークンのオブジェクト表現に含まれる情報を XML ライターに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e7878-141">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="e7878-142">トークン プロバイダー クラスとトークン認証システム クラスの作成方法</span><span class="sxs-lookup"><span data-stu-id="e7878-142">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="e7878-143">クライアントとサービスの資格情報は、セキュリティ トークン マネージャーのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7878-143">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="e7878-144">セキュリティ トークン マネージャーのインスタンスを使用すると、トークン プロバイダー、トークン認証システム、およびトークン シリアライザーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e7878-144">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="e7878-145">トークン プロバイダーは、クライアントまたはサービスの資格情報に含まれる情報に基づいて、トークンのオブジェクト表現を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-145">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="e7878-146">次に、トークンのオブジェクト表現は、(前のセクションで説明したとおり) トークン シリアライザーを使用してメッセージに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e7878-146">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="e7878-147">トークン認証システムは、到着したメッセージ内のトークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="e7878-147">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="e7878-148">受信トークンのオブジェクト表現は、トークン シリアライザーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-148">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="e7878-149">このオブジェクト表現は、次に、検証のためトークン認証システムに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-149">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="e7878-150">トークンが正常に検証されたら、トークン認証システムは `IAuthorizationPolicy` オブジェクトのコレクションを返します。このオブジェクトはトークンに含まれる情報を表します。</span><span class="sxs-lookup"><span data-stu-id="e7878-150">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="e7878-151">この情報は、承認に関する決定を行ったり、アプリケーションに対するクレームを提供したりするために、後でメッセージ処理中に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-151">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="e7878-152">この例では、クレジット カード トークンの認証システムはこの目的のために `CreditCardTokenAuthorizationPolicy` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7878-152">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="e7878-153">トークン シリアライザーは、トークンのオブジェクト表現を通信回線に送り、通信回線からトークンのオブジェクト表現を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e7878-153">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="e7878-154">これについては、前のセクションで説明したとおりです。</span><span class="sxs-lookup"><span data-stu-id="e7878-154">This is discussed in the previous section.</span></span>

 <span data-ttu-id="e7878-155">このサンプルでは、トークン プロバイダーはクライアントでのみ使用し、トークン認証システムはサービスでのみ使用します。これは、クレジット カード トークンの送信はクライアントからサービスへの方向でのみ行うためです。</span><span class="sxs-lookup"><span data-stu-id="e7878-155">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="e7878-156">クライアント側の機能は `CreditCardClientCredentials`、`CreditCardClientCredentialsSecurityTokenManager`、および `CreditCardTokenProvider` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="e7878-156">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="e7878-157">サービス側の機能は `CreditCardServiceCredentials`、`CreditCardServiceCredentialsSecurityTokenManager`、`CreditCardTokenAuthenticator`、および `CreditCardTokenAuthorizationPolicy` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="e7878-157">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException(nameof(creditCardFile));

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException(nameof(issuedClaims));
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a><span data-ttu-id="e7878-158">呼び出し元の情報の表示</span><span class="sxs-lookup"><span data-stu-id="e7878-158">Displaying the Callers' Information</span></span>

 <span data-ttu-id="e7878-159">呼び出し元の情報を表示するには、次のサンプル コードに示すように `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7878-159">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="e7878-160">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` には、現在の呼び出し元に関連付けられている承認クレームが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7878-160">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="e7878-161">クレームは、`CreditCardToken` コレクションの `AuthorizationPolicies` クラスによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-161">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 <span data-ttu-id="e7878-162">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-162">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e7878-163">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e7878-163">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="e7878-164">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="e7878-164">Setup Batch File</span></span>

 <span data-ttu-id="e7878-165">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする、IIS でホストされるアプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e7878-165">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e7878-166">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7878-166">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="e7878-167">次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="e7878-167">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="e7878-168">サーバー証明書の作成 :</span><span class="sxs-lookup"><span data-stu-id="e7878-168">Creating the server certificate:</span></span>

     <span data-ttu-id="e7878-169">`Setup.bat` バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-169">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="e7878-170">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="e7878-170">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e7878-171">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7878-171">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e7878-172">このバッチ ファイルでの既定は localhost です。</span><span class="sxs-lookup"><span data-stu-id="e7878-172">The default in this batch file is localhost.</span></span> <span data-ttu-id="e7878-173">`%SERVER_NAME%` 変数を変更する場合は、Client.cs ファイルと Service.cs ファイル全体を参照して、localhost のすべてのインスタンスを Setup.bat スクリプトで使用するサーバー名に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7878-173">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="e7878-174">証明書は、`LocalMachine` ストアの場所の My (Personal) ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-174">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="e7878-175">証明書は、IIS でホストされるサービスの LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-175">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="e7878-176">自己ホスト型サービスの場合、バッチ ファイルで文字列 LocalMachine を CurrentUser に置き換えて、クライアント証明書を CurrentUser ストアの場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="e7878-176">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="e7878-177">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="e7878-177">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="e7878-178">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7878-178">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e7878-179">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="e7878-179">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e7878-180">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="e7878-180">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="e7878-181">IIS でホストされるサービスから証明書の秘密キーへのアクセスを有効にするには、IIS でホストされる処理が実行されているユーザー アカウントに、秘密キーへの適切なアクセス許可を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7878-181">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="e7878-182">これは、Setup.bat スクリプトの最後の手順によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-182">This is accomplished by last steps in the Setup.bat script.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="e7878-183">Setup.bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e7878-183">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="e7878-184">Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルを含むディレクトリを指します。</span><span class="sxs-lookup"><span data-stu-id="e7878-184">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e7878-185">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="e7878-185">To set up and build the sample</span></span>

1. <span data-ttu-id="e7878-186">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e7878-186">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e7878-187">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e7878-187">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e7878-188">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="e7878-188">To run the sample on the same computer</span></span>

1. <span data-ttu-id="e7878-189">管理者特権で Visual Studio 2012 のコマンドプロンプトウィンドウを開き、サンプルのインストールフォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="e7878-189">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="e7878-190">これにより、サンプルの実行に必要なすべての証明書がインストールされます。Makecert.exe が存在するフォルダーがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e7878-190">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="e7878-191">サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="e7878-191">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="e7878-192">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7878-192">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="e7878-193">Client.exe を client\bin ディレクトリで起動します。</span><span class="sxs-lookup"><span data-stu-id="e7878-193">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="e7878-194">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7878-194">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="e7878-195">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7878-195">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="e7878-196">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="e7878-196">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="e7878-197">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7878-197">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="e7878-198">サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7878-198">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="e7878-199">必ず CreditCardFile.txt をコピーしてください。これを行わない場合、クレジット カードの認証システムはクライアントから送信されたクレジット カード情報を検証できません。</span><span class="sxs-lookup"><span data-stu-id="e7878-199">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="e7878-200">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7878-200">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e7878-201">コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="e7878-201">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e7878-202">`%SERVER_NAME%` 変数を、サービスがホストされるコンピューターの完全修飾名に変更すると、Setup.bat を使用してこの証明書を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e7878-202">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="e7878-203">Setup.bat ファイルは、管理者特権で開いた Visual Studio の開発者コマンドプロンプトで実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e7878-203">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="e7878-204">サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7878-204">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="e7878-205">このようにする必要があるのは、サーバー証明書が信頼できる発行元から発行されていない場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e7878-205">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="e7878-206">EchoServiceHost.cs ファイルで、証明書のサブジェクト名の値を localhost から完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="e7878-206">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="e7878-207">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7878-207">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="e7878-208">Client.cs ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="e7878-208">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="e7878-209">Client.cs ファイルで、サービス X.509 証明書のサブジェクト名を localhost からリモート ホストの完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="e7878-209">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="e7878-210">クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="e7878-210">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="e7878-211">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7878-211">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e7878-212">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="e7878-212">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="e7878-213">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="e7878-213">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
