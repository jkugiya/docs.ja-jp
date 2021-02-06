---
description: '詳細については、「方法: チャネルのセキュリティ資格情報を指定する」を参照してください。'
title: '方法: チャネルのセキュリティ資格情報を指定する'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 18cbb1ea1113e5b31f5adb43556db03d91c618ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643151"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="d9eeb-103">方法: チャネルのセキュリティ資格情報を指定する</span><span class="sxs-lookup"><span data-stu-id="d9eeb-103">How to: Specify Channel Security Credentials</span></span>

<span data-ttu-id="d9eeb-104">Windows Communication Foundation (WCF) サービスモニカーを使用すると、COM アプリケーションから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-104">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="d9eeb-105">ほとんどの WCF サービスでは、クライアントが認証と承認のための資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-105">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="d9eeb-106">Wcf クライアントから WCF サービスを呼び出すときに、これらの資格情報をマネージコードまたはアプリケーション構成ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-106">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="d9eeb-107">COM アプリケーションから WCF サービスを呼び出す場合は、インターフェイスを使用して <xref:System.ServiceModel.ComIntegration.IChannelCredentials> 資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-107">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="d9eeb-108">ここでは、<xref:System.ServiceModel.ComIntegration.IChannelCredentials> インターフェイスを使用して資格情報を指定するさまざまな方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-108">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9eeb-109"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> は IDispatch ベースのインターフェイスです。Visual Studio 環境で IntelliSense 機能を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-109"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="d9eeb-110">この記事では、 [メッセージセキュリティのサンプル](../samples/message-security-sample.md)で定義されている WCF サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-110">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="d9eeb-111">クライアント証明書を指定するには</span><span class="sxs-lookup"><span data-stu-id="d9eeb-111">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="d9eeb-112">メッセージ セキュリティのディレクトリの Setup.bat ファイルを実行し、必要なテスト証明書を作成してインストールします。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-112">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="d9eeb-113">メッセージ セキュリティのプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-113">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="d9eeb-114">`[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]`を `ICalculator` インターフェイス定義に追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-114">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="d9eeb-115">`bindingNamespace="http://Microsoft.ServiceModel.Samples"`サービスの App.config のエンドポイントタグにを追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-115">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="d9eeb-116">メッセージ セキュリティ サンプルをビルドし、Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-116">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="d9eeb-117">Internet Explorer を使用してサービスの URI () を参照し、 `http://localhost:8000/ServiceModelSamples/Service` サービスが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-117">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="d9eeb-118">Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d9eeb-119">フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. <span data-ttu-id="d9eeb-120">Visual Basic アプリケーションを実行し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-120">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="d9eeb-121">Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-121">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="d9eeb-122"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> または <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> を <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> の代わりに使用して、クライアント証明書を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-122"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="d9eeb-123">この呼び出しを機能させるには、クライアントが実行されているコンピューターでクライアント証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-123">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9eeb-124">モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-124">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="d9eeb-125">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-125">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="d9eeb-126">ユーザー名とパスワードを指定するには</span><span class="sxs-lookup"><span data-stu-id="d9eeb-126">To specify user name and password</span></span>  
  
1. <span data-ttu-id="d9eeb-127">`wsHttpBinding` を使用するよう App.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-127">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="d9eeb-128">これは、ユーザー名とパスワードの検証に必要です。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-128">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="d9eeb-129">`clientCredentialType` を UserName に設定します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-129">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="d9eeb-130">Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-130">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d9eeb-131">フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-131">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="d9eeb-132">Visual Basic アプリケーションを実行し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-132">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="d9eeb-133">Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-133">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d9eeb-134">この例のサービス モニカーに指定されたバインディングは、WSHttpBinding_ICalculator に変更されました。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-134">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="d9eeb-135">また、<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> の呼び出しにも有効なユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-135">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="d9eeb-136">Windows 資格情報を指定するには</span><span class="sxs-lookup"><span data-stu-id="d9eeb-136">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="d9eeb-137">サービスの App.config ファイルで、`clientCredentialType` を Windows に設定します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-137">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="d9eeb-138">Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-138">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d9eeb-139">フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-139">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="d9eeb-140">Visual Basic アプリケーションを実行し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-140">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="d9eeb-141">Visual Basic アプリケーションに Add(3,4) の結果を示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-141">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d9eeb-142">"ドメイン"、"ユーザー ID"、"パスワード" を有効な値に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-142">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="d9eeb-143">発行トークンを指定するには</span><span class="sxs-lookup"><span data-stu-id="d9eeb-143">To specify an issue token</span></span>  
  
1. <span data-ttu-id="d9eeb-144">発行トークンは、フェデレーション セキュリティを使用するアプリケーションのみが使用します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-144">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="d9eeb-145">フェデレーションセキュリティの詳細については、「 [フェデレーションと発行済みトークン](federation-and-issued-tokens.md) および [フェデレーションのサンプル](../samples/federation-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-145">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="d9eeb-146"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> メソッドを呼び出す方法を次の Visual Basic コード例に示します。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-146">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="d9eeb-147">このメソッドのパラメーターの詳細については、<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9eeb-147">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9eeb-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9eeb-148">See also</span></span>

- [<span data-ttu-id="d9eeb-149">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="d9eeb-149">Federation</span></span>](federation.md)
- [<span data-ttu-id="d9eeb-150">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="d9eeb-150">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="d9eeb-151">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="d9eeb-151">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="d9eeb-152">メッセージのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d9eeb-152">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="d9eeb-153">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d9eeb-153">Bindings and Security</span></span>](bindings-and-security.md)
