---
description: 詳細については、トークンのサポートに関するページをご覧ください。
title: トークンのサポート
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 455c69ce1ae03bd612f78a7977b013955bd81868
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668735"
---
# <a name="supporting-tokens"></a><span data-ttu-id="0a1b5-103">トークンのサポート</span><span class="sxs-lookup"><span data-stu-id="0a1b5-103">Supporting Tokens</span></span>

<span data-ttu-id="0a1b5-104">このトークンのサポート サンプルでは、WS-Security を使用するメッセージに追加トークンを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-104">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="0a1b5-105">この例では、ユーザー名セキュリティ トークンに加え、X.509 バイナリ セキュリティ トークンを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-105">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="0a1b5-106">トークンは、WS-Security メッセージ ヘッダーでクライアントからサービスに渡されます。そのメッセージの一部は X.509 証明書を所有していることを受信側に証明するため、X.509 セキュリティ トークンに関連付けられた秘密キーで署名されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-106">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="0a1b5-107">これは、複数のクレームをメッセージに関連付けて送信側を認証または承認する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-107">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="0a1b5-108">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0a1b5-109">対象</span><span class="sxs-lookup"><span data-stu-id="0a1b5-109">Demonstrates</span></span>

 <span data-ttu-id="0a1b5-110">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-110">The sample demonstrates:</span></span>

- <span data-ttu-id="0a1b5-111">クライアントが追加セキュリティ トークンをサービスに渡す方法。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-111">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="0a1b5-112">サーバーが、追加セキュリティ トークンに関連付けられたクレームにアクセスする方法。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-112">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="0a1b5-113">サーバーの X.509 証明書を使用して、メッセージの暗号化や署名に使用する対称キーを保護する方法。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-113">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1b5-114">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="0a1b5-115">クライアントによる、ユーザー名トークンと X.509 サポート セキュリティ トークンを使用した認証</span><span class="sxs-lookup"><span data-stu-id="0a1b5-115">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>

 <span data-ttu-id="0a1b5-116">サービスは、通信に使用する単一エンドポイントを公開します。エンドポイントは、`BindingHelper` クラスと `EchoServiceHost` クラスを使用してプログラムによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-116">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="0a1b5-117">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0a1b5-118">バインディングは、`SymmetricSecurityBindingElement` と `HttpTransportBindingElement` を使用して、カスタム バインディングとして構成されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="0a1b5-119">このサンプルでは、`SymmetricSecurityBindingElement` を設定してサービス X.509 証明書を使用し、送信中の対称キーを保護して、WS-Security メッセージ ヘッダー内で `UserNameToken` とサポート `X509SecurityToken` を渡します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-119">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="0a1b5-120">対称キーは、メッセージ本文とユーザー名セキュリティ トークンの暗号化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-120">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="0a1b5-121">サポート トークンは、追加バイナリ セキュリティ トークンとして WS-Security メッセージ ヘッダー内で渡されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-121">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="0a1b5-122">サポート トークンの信頼性は、サポート X.509 セキュリティ トークンに関連付けられている秘密キーを使用してメッセージに署名することによって証明されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-122">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="0a1b5-123">この動作により、クライアント認証に使用されるサービス資格情報と、サービス X.509 証明書に関する情報が指定されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-123">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="0a1b5-124">サンプルでは、サービス X.509 証明書内のサブジェクト名として `CN=localhost` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-124">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="0a1b5-125">サービス コード :</span><span class="sxs-lookup"><span data-stu-id="0a1b5-125">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="0a1b5-126">クライアント エンドポイントは、サービス エンドポイントと同様の方法で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-126">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="0a1b5-127">クライアントは、同じ `BindingHelper` クラスを使用してバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-127">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="0a1b5-128">セットアップの残りの部分は、`Client` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-128">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="0a1b5-129">クライアントはクライアント エンドポイントの動作コレクションに対するセットアップ コード内に、ユーザー名セキュリティ トークンに関する情報、サポート X.509 セキュリティ トークン、およびサービス X.509 証明書に関する情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-129">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="0a1b5-130">呼び出し元の情報の表示</span><span class="sxs-lookup"><span data-stu-id="0a1b5-130">Displaying Callers' Information</span></span>

 <span data-ttu-id="0a1b5-131">呼び出し元の情報を表示するには、次のコードに示すように `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-131">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="0a1b5-132">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` には、現在の呼び出し元に関連付けられている承認クレームが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-132">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="0a1b5-133">これらの要求は、メッセージで受信したすべてのトークンについて Windows Communication Foundation (WCF) によって自動的に提供されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-133">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="0a1b5-134">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="0a1b5-134">Running the Sample</span></span>

 <span data-ttu-id="0a1b5-135">このサンプルを実行すると、最初にクライアントから、ユーザー名トークンのユーザー名とパスワードを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-135">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="0a1b5-136">サービスの WCF では、ユーザー名トークンに指定された値がシステムによって提供される id にマップされるため、システムアカウントには必ず正しい値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-136">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="0a1b5-137">その後、クライアントではサービスからの応答が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-137">After that, the client displays the response from the service.</span></span> <span data-ttu-id="0a1b5-138">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-138">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="0a1b5-139">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="0a1b5-139">Setup Batch File</span></span>

 <span data-ttu-id="0a1b5-140">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、インターネット インフォメーション サービス (IIS) でホストされるアプリケーションを実行できるようになります。このアプリケーションは、サーバー証明書ベースのセキュリティを必要とします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-140">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="0a1b5-141">このバッチ ファイルは、別のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-141">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="0a1b5-142">次に、バッチ ファイルのセクションのうち、適切な構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-142">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="0a1b5-143">クライアント証明書の作成</span><span class="sxs-lookup"><span data-stu-id="0a1b5-143">Creating the Client Certificate</span></span>

 <span data-ttu-id="0a1b5-144">Setup.bat バッチ ファイルの次の行は、使用するクライアント証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-144">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="0a1b5-145">`%CLIENT_NAME%` 変数は、クライアント証明書のサブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-145">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="0a1b5-146">このサンプルでは、サブジェクト名として "client.com" を使用します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-146">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="0a1b5-147">証明書は、`CurrentUser` ストアの場所の My (Personal) ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-147">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="0a1b5-148">クライアント証明書のサーバーの信頼されたストアへのインストール</span><span class="sxs-lookup"><span data-stu-id="0a1b5-148">Installing the Client Certificate into the Server's Trusted Store</span></span>

 <span data-ttu-id="0a1b5-149">Setup.bat バッチ ファイルの次の行は、クライアント証明書をサーバーの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-149">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="0a1b5-150">この手順が必要なのは、Makecert.exe によって生成される証明書がサーバーのシステムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-150">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="0a1b5-151">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-151">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="0a1b5-152">サーバー証明書の作成</span><span class="sxs-lookup"><span data-stu-id="0a1b5-152">Creating the Server Certificate</span></span>

 <span data-ttu-id="0a1b5-153">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="0a1b5-154">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="0a1b5-155">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="0a1b5-156">このバッチ ファイルでの既定は localhost です。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-156">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="0a1b5-157">証明書は、LocalMachine ストアの場所の My (Personal) ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-157">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="0a1b5-158">証明書は、IIS でホストされるサービスの LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-158">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="0a1b5-159">自己ホスト型サービスの場合、バッチ ファイルで文字列 LocalMachine を CurrentUser に置き換えて、サーバー証明書を CurrentUser ストアの場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-159">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="0a1b5-160">サーバー証明書のクライアントの信頼された証明書ストアへのインストール</span><span class="sxs-lookup"><span data-stu-id="0a1b5-160">Installing Server Certificate into Client's Trusted Certificate Store</span></span>

 <span data-ttu-id="0a1b5-161">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-161">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0a1b5-162">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-162">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0a1b5-163">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-163">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="0a1b5-164">証明書の秘密キーへのアクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="0a1b5-164">Enabling Access to the Certificate's Private Key</span></span>

 <span data-ttu-id="0a1b5-165">IIS でホストされるサービスから証明書の秘密キーへのアクセスを有効にするには、IIS でホストされる処理が実行されているユーザー アカウントに、秘密キーへの適切なアクセス許可を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-165">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="0a1b5-166">これは、Setup.bat スクリプトの最後の手順によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-166">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a1b5-167">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0a1b5-167">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0a1b5-168">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-168">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0a1b5-169">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-169">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="0a1b5-170">サンプルを単一コンピューター構成で実行するか、複数コンピューター構成で実行するかに応じて、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-170">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="0a1b5-171">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0a1b5-171">To run the sample on the same machine</span></span>

1. <span data-ttu-id="0a1b5-172">管理者特権で実行する Visual Studio 2012 コマンドプロンプト内のサンプルのインストールフォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-172">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="0a1b5-173">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-173">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0a1b5-174">Setup.bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-174">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="0a1b5-175">Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルを含むディレクトリを指します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-175">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="0a1b5-176">サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-176">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="0a1b5-177">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-177">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="0a1b5-178">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="0a1b5-179">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-179">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="0a1b5-180">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="0a1b5-181">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0a1b5-181">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="0a1b5-182">サービス コンピューターにディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-182">Create a directory on the service machine.</span></span> <span data-ttu-id="0a1b5-183">インターネット インフォメーション サービス (IIS) 管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-183">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="0a1b5-184">サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-184">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="0a1b5-185">ファイルのコピー先が \bin サブディレクトリであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-185">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="0a1b5-186">Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-186">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="0a1b5-187">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-187">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="0a1b5-188">クライアント プログラム ファイルを、クライアント コンピュータに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-188">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="0a1b5-189">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-189">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="0a1b5-190">サーバーで、 `setup.bat service` 管理者特権で開かれた Visual Studio の開発者コマンドプロンプトでを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-190">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="0a1b5-191">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-191">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="0a1b5-192">Web.config を編集して、新しい証明書名 ( `findValue` の属性) を反映し [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ます。これは、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-192">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="0a1b5-193">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-193">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="0a1b5-194">クライアントで、 `setup.bat client` 管理者特権で開かれた Visual Studio の開発者コマンドプロンプトでを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-194">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="0a1b5-195">`setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-195">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="0a1b5-196">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-196">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="0a1b5-197">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-197">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="0a1b5-198">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-198">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="0a1b5-199">クライアントで ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-199">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="0a1b5-200">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-200">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="0a1b5-201">サーバーで ImportClientCert.bat を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-201">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="0a1b5-202">クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-202">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="0a1b5-203">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-203">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0a1b5-204">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="0a1b5-204">To clean up after the sample</span></span>  
  
- <span data-ttu-id="0a1b5-205">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-205">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a1b5-206">このサンプルを別のマシンで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-206">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="0a1b5-207">コンピューター間で証明書を使用する WCF サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-207">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="0a1b5-208">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="0a1b5-208">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
