---
description: '詳細情報: 信頼されたファサードサービス'
title: 信頼されたファサード サービス
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: aebfa89c47d5e8ea37e210b2d7b19afbe204a1a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685479"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="597e5-103">信頼されたファサード サービス</span><span class="sxs-lookup"><span data-stu-id="597e5-103">Trusted Facade Service</span></span>

<span data-ttu-id="597e5-104">このシナリオのサンプルでは、Windows Communication Foundation (WCF) セキュリティインフラストラクチャを使用して、呼び出し元の id 情報をあるサービスから別のサービスにフローする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="597e5-104">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="597e5-105">ファサード サービスを使用してサービスから提供される機能をパブリック ネットワークに公開するのは、一般的なデザイン パターンです。</span><span class="sxs-lookup"><span data-stu-id="597e5-105">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="597e5-106">ファサード サービスは、通常は境界ネットワーク (DMZ、非武装地帯、およびスクリーン サブネットとも呼ばれます) 内に存在し、ビジネス ロジックを実装して内部データにアクセスする、バックエンド サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="597e5-106">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="597e5-107">ファサード サービスとバックエンド サービス間の通信チャネルはファイアウォールを通過し、通常は 1 つの目的のみに限定されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-107">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="597e5-108">このサンプルは、次のコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="597e5-108">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="597e5-109">電卓クライアント</span><span class="sxs-lookup"><span data-stu-id="597e5-109">Calculator client</span></span>  
  
- <span data-ttu-id="597e5-110">電卓ファサード サービス</span><span class="sxs-lookup"><span data-stu-id="597e5-110">Calculator façade service</span></span>  
  
- <span data-ttu-id="597e5-111">電卓バックエンド サービス</span><span class="sxs-lookup"><span data-stu-id="597e5-111">Calculator backend service</span></span>  
  
 <span data-ttu-id="597e5-112">ファサード サービスは、要求を検証して呼び出し元を認証します。</span><span class="sxs-lookup"><span data-stu-id="597e5-112">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="597e5-113">認証と検証が正常に完了すると、ファサード サービスは、境界ネットワークから内部ネットワークへの制御された通信チャネルを使用して、バックエンド サービスに要求を転送します。</span><span class="sxs-lookup"><span data-stu-id="597e5-113">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="597e5-114">ファサード サービスは、転送される要求の一部として呼び出し元の ID に関する情報を格納し、バックエンド サービスがプロセスでこの情報を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="597e5-114">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="597e5-115">呼び出し元の ID は、メッセージの `Username` ヘッダー内部にある `Security` セキュリティ トークンを使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-115">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="597e5-116">このサンプルでは、WCF セキュリティインフラストラクチャを使用して、この情報をヘッダーから送信および抽出し `Security` ます。</span><span class="sxs-lookup"><span data-stu-id="597e5-116">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="597e5-117">バックエンド サービスは、ファサード サービスを信頼して呼び出し元を認証します。</span><span class="sxs-lookup"><span data-stu-id="597e5-117">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="597e5-118">このため、バックエンド サービスは呼び出し元の再認証を行いません。つまり、ファサード サービスから転送された要求内の ID 情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-118">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="597e5-119">こうした信頼関係があるので、バックエンド サービスでは、転送メッセージが信頼されたソース (この場合はファサード サービス) から送信されことを確認するために、ファサード サービスを認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="597e5-119">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="597e5-120">実装</span><span class="sxs-lookup"><span data-stu-id="597e5-120">Implementation</span></span>  

 <span data-ttu-id="597e5-121">このサンプルには、通信パスが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="597e5-121">There are two communication paths in this sample.</span></span> <span data-ttu-id="597e5-122">1 つはクライアントとファサード サービス間のパスで、もう 1 つはファサード サービスとバックエンド サービス間のパスです。</span><span class="sxs-lookup"><span data-stu-id="597e5-122">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="597e5-123">クライアントとファサード サービス間の通信パス</span><span class="sxs-lookup"><span data-stu-id="597e5-123">Communication Path between Client and Façade Service</span></span>  

 <span data-ttu-id="597e5-124">クライアントとファサード サービスとの通信パスでは、 `wsHttpBinding` 型のクライアント資格情報が設定された `UserName` を使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-124">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="597e5-125">つまり、クライアントはユーザー名とパスワードを使用してファサード サービスに対する認証を行い、ファサード サービスは X.509 証明書を使用してクライアントに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="597e5-125">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="597e5-126">バインディング構成は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="597e5-126">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="597e5-127">ファサード サービスはカスタム `UserNamePasswordValidator` 実装を使用して、呼び出し元を認証します。</span><span class="sxs-lookup"><span data-stu-id="597e5-127">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="597e5-128">この認証では、デモンストレーション用に、呼び出し元のユーザー名と指定されたパスワードが一致していることだけを確認します。</span><span class="sxs-lookup"><span data-stu-id="597e5-128">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="597e5-129">実環境では多くの場合、Active Directory またはカスタムの ASP.NET メンバシップ プロバイダを使用して認証が行われます。</span><span class="sxs-lookup"><span data-stu-id="597e5-129">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="597e5-130">検証の実装は `FacadeService.cs` ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="597e5-130">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="597e5-131">カスタム検証が、ファサード サービス構成ファイルの `serviceCredentials` 動作の内側で使用されるよう構成されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-131">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="597e5-132">この動作は、サービスの X.509 証明書の構成にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-132">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="597e5-133">ファサード サービスと バックエンド サービス間の通信パス</span><span class="sxs-lookup"><span data-stu-id="597e5-133">Communication Path between Façade Service and Backend Service</span></span>  

 <span data-ttu-id="597e5-134">ファサード サービスとバックエンド サービスとの通信パスでは、複数のバインディング要素で構成される `customBinding` を使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-134">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="597e5-135">このバインディングにより、次の 2 つが実現されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-135">This binding accomplishes two things.</span></span> <span data-ttu-id="597e5-136">まず、ファサード サービスとバックエンド サービスが認証され、通信がセキュリティで保護されていることと、信頼されたソースからのものであることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-136">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="597e5-137">次に、 `Username` セキュリティ トークン内にある、最初の呼び出し元の ID が送信されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-137">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="597e5-138">この場合、最初の呼び出し元のユーザー名だけがバックエンド サービスに送信されます。パスワードはメッセージには含まれません。</span><span class="sxs-lookup"><span data-stu-id="597e5-138">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="597e5-139">これは、バックエンド サービスがファサード サービスに要求を転送する前に、ファサード サービスを信頼して呼び出し元を認証するためです。</span><span class="sxs-lookup"><span data-stu-id="597e5-139">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="597e5-140">ファサード サービスはバックエンド サービスに対して自己認証を行うので、バックエンド サービスは転送された要求に含まれる情報を信頼できます。</span><span class="sxs-lookup"><span data-stu-id="597e5-140">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="597e5-141">この通信パスのバインディング構成は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="597e5-141">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="597e5-142">バインド要素によって、 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 最初の呼び出し元のユーザー名の転送と抽出が行われます。</span><span class="sxs-lookup"><span data-stu-id="597e5-142">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="597e5-143">とは、 [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) ファサードとバックエンドサービスおよびメッセージ保護の認証を行います。</span><span class="sxs-lookup"><span data-stu-id="597e5-143">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="597e5-144">要求を転送するには、ファサードサービスの実装で、最初の呼び出し元のユーザー名を指定する必要があります。これにより、WCF セキュリティインフラストラクチャでは、転送されたメッセージにこれを配置できます。</span><span class="sxs-lookup"><span data-stu-id="597e5-144">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="597e5-145">最初の呼び出し元のユーザー名をファサード サービスの実装で提供するには、ファサード サービスがバックエンド サービスとの通信に使用するクライアント プロキシ インスタンスの `ClientCredentials` プロパティに、このユーザー名を設定します。</span><span class="sxs-lookup"><span data-stu-id="597e5-145">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="597e5-146">`GetCallerIdentity` メソッドをファサード サービスに実装する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="597e5-146">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="597e5-147">他のメソッドも同じパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-147">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="597e5-148">前のコードに示すように、 `ClientCredentials` プロパティではパスワードは設定されず、ユーザー名のみが設定されています。</span><span class="sxs-lookup"><span data-stu-id="597e5-148">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="597e5-149">この場合、WCF セキュリティインフラストラクチャでは、パスワードを使用せずにユーザー名セキュリティトークンが作成されます。この場合、このシナリオではまさにこれが必要です。</span><span class="sxs-lookup"><span data-stu-id="597e5-149">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="597e5-150">バックエンド サービスでは、ユーザー名セキュリティ トークンに含まれる情報が認証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="597e5-150">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="597e5-151">既定では、WCF セキュリティは、指定されたパスワードを使用して、ユーザーを Windows アカウントにマップしようとします。</span><span class="sxs-lookup"><span data-stu-id="597e5-151">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="597e5-152">この場合、パスワードは指定されず、バックエンド サービスはユーザー名を認証する必要がありません。ファサード サービスで既に認証が行われているからです。</span><span class="sxs-lookup"><span data-stu-id="597e5-152">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="597e5-153">WCF でこの機能を実装するには、ユーザー `UserNamePasswordValidator` 名がトークンで指定され、追加の認証を実行しないようにするカスタムのが用意されています。</span><span class="sxs-lookup"><span data-stu-id="597e5-153">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="597e5-154">カスタム検証が、ファサード サービス構成ファイルの `serviceCredentials` 動作の内側で使用されるよう構成されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-154">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="597e5-155">ユーザー名の情報と信頼されたファサード サービス アカウントに関する情報を抽出するには、バックエンド サービスの実装で `ServiceSecurityContext` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-155">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="597e5-156">`GetCallerIdentity` メソッドを実装する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="597e5-156">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="597e5-157">ファサード サービス アカウント情報は、 `ServiceSecurityContext.Current.WindowsIdentity` プロパティを使用して抽出されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-157">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="597e5-158">最初の呼び出し元に関する情報にアクセスするには、バックエンド サービスで `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="597e5-158">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="597e5-159">そして、型 `Identity` を含む `Name`クレームを検索します。</span><span class="sxs-lookup"><span data-stu-id="597e5-159">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="597e5-160">この要求は、セキュリティトークンに含まれている情報から、WCF セキュリティインフラストラクチャによって自動的に生成され `Username` ます。</span><span class="sxs-lookup"><span data-stu-id="597e5-160">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="597e5-161">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="597e5-161">Running the sample</span></span>  

 <span data-ttu-id="597e5-162">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-162">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="597e5-163">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="597e5-163">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="597e5-164">ファサード サービスまたはバックエンド サービスのコンソール ウィンドウで Enter キーを押すと、サービスがシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="597e5-164">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="597e5-165">信頼されたファサード シナリオのサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーが構成され、クライアントに対して自己認証を行う証明書ベースのセキュリティが必要なファサード サービスを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="597e5-165">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="597e5-166">詳細については、このトピック末尾のセットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597e5-166">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="597e5-167">次に、バッチ ファイルの各セクションの概要を簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="597e5-167">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="597e5-168">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="597e5-168">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="597e5-169">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="597e5-169">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="597e5-170">`%SERVER_NAME%` 変数はサーバー名を指定します。既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="597e5-170">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="597e5-171">証明書は LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-171">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="597e5-172">クライアントの信頼された証明書ストアへのファサード サービスの証明書のインストール。</span><span class="sxs-lookup"><span data-stu-id="597e5-172">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="597e5-173">次の行は、ファサード サービスの証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="597e5-173">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="597e5-174">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="597e5-174">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="597e5-175">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="597e5-175">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="597e5-176">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="597e5-176">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="597e5-177">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="597e5-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="597e5-178">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="597e5-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="597e5-179">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="597e5-179">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="597e5-180">Makecert.exe が存在するフォルダがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="597e5-180">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="597e5-181">Setup.bat をサンプルのインストール フォルダーで実行します。</span><span class="sxs-lookup"><span data-stu-id="597e5-181">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="597e5-182">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="597e5-182">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="597e5-183">別のコンソール ウィンドウで、\BackendService\bin ディレクトリの BackendService.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="597e5-183">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="597e5-184">別のコンソール ウィンドウで、\FacadeService\bin ディレクトリの FacadeService.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="597e5-184">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="597e5-185">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="597e5-185">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="597e5-186">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-186">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="597e5-187">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597e5-187">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="597e5-188">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="597e5-188">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="597e5-189">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="597e5-189">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="597e5-190">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="597e5-190">The samples may already be installed on your machine.</span></span> <span data-ttu-id="597e5-191">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="597e5-191">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="597e5-192">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="597e5-192">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="597e5-193">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="597e5-193">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
