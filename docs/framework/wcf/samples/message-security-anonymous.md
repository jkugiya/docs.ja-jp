---
description: 詳細については、「匿名メッセージセキュリティ」を参照してください。
title: メッセージ セキュリティ匿名
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: a49b3542d2b3dd0173b31c9f7b81645ec1098afb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703901"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="b9b67-103">メッセージ セキュリティ匿名</span><span class="sxs-lookup"><span data-stu-id="b9b67-103">Message Security Anonymous</span></span>

<span data-ttu-id="b9b67-104">Message Security Anonymous サンプルでは、クライアント認証を使用せずに、サーバーの x.509 証明書を使用するサーバー認証を必要とする、メッセージレベルのセキュリティを使用する Windows Communication Foundation (WCF) アプリケーションを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-104">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="b9b67-105">クライアント/サーバー間のすべてのアプリケーション メッセージは署名され、暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-105">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="b9b67-106">このサンプルは、 [WSHttpBinding](wshttpbinding.md) サンプルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="b9b67-106">This sample is based on the [WSHttpBinding](wshttpbinding.md) sample.</span></span> <span data-ttu-id="b9b67-107">このサンプルは、クライアント コンソール プログラム (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b9b67-107">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b9b67-108">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="b9b67-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="b9b67-110">このサンプルでは、電卓インターフェイスに、クライアントが認証されなかった場合に `True` を返す新しい操作を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-110">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="b9b67-111">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (Web.config) で定義します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-111">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="b9b67-112">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-112">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="b9b67-113">このバインディングの構成には `wsHttpBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-113">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="b9b67-114">`wsHttpBinding` バインディングの既定のセキュリティ モードは `Message` です。</span><span class="sxs-lookup"><span data-stu-id="b9b67-114">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="b9b67-115">`clientCredentialType` 属性が `None` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="b9b67-115">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="b9b67-116">サービス認証に使用する資格情報は、で指定し [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-116">The credentials to be used for service authentication are specified in the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="b9b67-117">サーバー証明書の `SubjectName` には、`findValue` 属性に指定されている値と同じ値が指定されている必要があります。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-117">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="b9b67-118">クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="b9b67-119">`wsHttpBinding` バインディングのクライアント セキュリティ モードは `Message` です。</span><span class="sxs-lookup"><span data-stu-id="b9b67-119">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="b9b67-120">`clientCredentialType` 属性が `None` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="b9b67-120">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="b9b67-121">このサンプルでは、サービスの証明書を認証するために、<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> を <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-121">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="b9b67-122">これは、`behaviors` セクションのクライアントの App.config ファイルで行われます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-122">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="b9b67-123">つまり、証明書がユーザーの Trusted People ストア内に存在している場合、その証明書は発行者のチェーンが検証されることなく信頼されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-123">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="b9b67-124">証明機関 (CA) から発行された証明書を要求しなくともサンプルを実行できるようにするため、ここでは便宜上この設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-124">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="b9b67-125">この設定は、既定の ChainTrust よりも安全性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-125">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="b9b67-126">`PeerOrChainTrust` を製品版のコードで使用する前に、この設定のセキュリティへの影響について慎重に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-126">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="b9b67-127">クライアント実装は、メソッドへの呼び出しを追加 `IsCallerAnonymous` します。それ以外の場合は、 [WSHttpBinding](wshttpbinding.md) サンプルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-127">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="b9b67-128">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b9b67-129">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-129">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="b9b67-130">メッセージ セキュリティ匿名サンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、証明書ベースのセキュリティを必要とするホスト アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-130">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="b9b67-131">バッチ ファイルの実行には 2 つのモードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-131">The batch file can be run in two modes.</span></span> <span data-ttu-id="b9b67-132">バッチ ファイルを単一コンピューター モードで実行するには、コマンド ラインに「`setup.bat`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-132">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="b9b67-133">サービス モードで実行するには、「`setup.bat service`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-133">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="b9b67-134">このサンプルを複数のコンピューターで実行している場合は、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-134">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="b9b67-135">詳細については、このトピック末尾のセットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-135">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="b9b67-136">次に、バッチ ファイルの各セクションの概要を簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-136">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="b9b67-137">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="b9b67-137">Creating the server certificate.</span></span>

     <span data-ttu-id="b9b67-138">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="b9b67-139">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="b9b67-140">証明書は LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="b9b67-141">セットアップ バッチ ファイルの実行にサービスの引数 (`setup.bat service` など) が使用された場合、%SERVER_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-141">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="b9b67-142">それ以外の場合、既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="b9b67-142">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="b9b67-143">クライアントの信頼された証明書ストアへのサーバー証明書のインストール。</span><span class="sxs-lookup"><span data-stu-id="b9b67-143">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="b9b67-144">次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="b9b67-145">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="b9b67-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="b9b67-146">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="b9b67-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="b9b67-147">証明書の秘密キーに関する権限の付与。</span><span class="sxs-lookup"><span data-stu-id="b9b67-147">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="b9b67-148">Setup.bat バッチファイルの次の行は、LocalMachine ストアに格納されているサーバー証明書を ASP.NET ワーカープロセスアカウントにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-148">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="b9b67-149">非 U. S を使用している場合。英語版の Windows では、Setup.bat ファイルを編集し、 `NT AUTHORITY\NETWORK SERVICE` アカウント名をそれと同等の地域に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-149">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b9b67-150">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b9b67-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b9b67-151">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b9b67-152">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b9b67-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="b9b67-153">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="b9b67-153">To run the sample on the same computer</span></span>

1. <span data-ttu-id="b9b67-154">Makecert.exe と FindPrivateKey.exe が含まれているフォルダーがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-154">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="b9b67-155">Visual Studio の開発者コマンドプロンプトのサンプルのインストールフォルダーから、管理者特権で実行される Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-155">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="b9b67-156">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-156">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b9b67-157">セットアップバッチファイルは、Visual Studio の開発者コマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b9b67-157">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="b9b67-158">path 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-158">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="b9b67-159">この環境変数は、Visual Studio の開発者コマンドプロンプト内で自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-159">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="b9b67-160">アドレスを入力して、ブラウザーを使用してサービスへのアクセスを確認し `http://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-160">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="b9b67-161">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-161">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="b9b67-162">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-162">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="b9b67-163">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-163">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="b9b67-164">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="b9b67-164">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="b9b67-165">サービス コンピューターにディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-165">Create a directory on the service computer.</span></span> <span data-ttu-id="b9b67-166">インターネット インフォメーション サービス (IIS) 管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-166">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="b9b67-167">サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-167">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="b9b67-168">ファイルのコピー先が \bin サブディレクトリであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-168">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="b9b67-169">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-169">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="b9b67-170">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-170">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="b9b67-171">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="b9b67-172">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="b9b67-173">サーバーで、 `setup.bat service` 管理者特権で開かれた Visual Studio の開発者コマンドプロンプトでを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="b9b67-174">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="b9b67-175">Web.config を編集して、新しい証明書名 ( `findValue` の属性 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) を反映します。これは、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="b9b67-175">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="b9b67-176">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9b67-176">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="b9b67-177">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-177">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="b9b67-178">クライアントで、管理者特権で開いた Visual Studio の開発者コマンドプロンプトで ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-178">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="b9b67-179">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="b9b67-179">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="b9b67-180">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-180">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="b9b67-181">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-181">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b9b67-182">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="b9b67-182">To clean up after the sample</span></span>  
  
- <span data-ttu-id="b9b67-183">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="b9b67-183">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9b67-184">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="b9b67-184">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="b9b67-185">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="b9b67-185">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="b9b67-186">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.` となります。</span><span class="sxs-lookup"><span data-stu-id="b9b67-186">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
