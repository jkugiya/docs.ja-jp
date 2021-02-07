---
description: '詳細情報: x.509 Certificate バリデーター'
title: X.509 証明書検証
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 3fead47cab4d639640f5af755717636ca2e8d01e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726235"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="a802d-103">X.509 証明書検証</span><span class="sxs-lookup"><span data-stu-id="a802d-103">X.509 Certificate Validator</span></span>

<span data-ttu-id="a802d-104">このサンプルでは、カスタム X.509 証明書検証を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a802d-104">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="a802d-105">これは、アプリケーションの要件に適した組み込みの X.509 証明書検証モードがない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a802d-105">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="a802d-106">このサンプルでは、自己発行の証明書を許可するカスタム検証を備えたサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="a802d-106">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="a802d-107">クライアントはこのような証明書を使用して、このサービスに認証されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-107">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="a802d-108">メモ : 任意のユーザーが自己発行の証明書を作成できる場合、このサービスで使用されるカスタム検証は、ChainTrust X509CertificateValidationMode によって提供される既定の動作よりも安全性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="a802d-108">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="a802d-109">この検証ロジックを製品版のコードで使用する前に、こうしたセキュリティへの影響について慎重に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a802d-109">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="a802d-110">このサンプルで示す処理の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a802d-110">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="a802d-111">クライアントは X.509 証明書を使用して認証される。</span><span class="sxs-lookup"><span data-stu-id="a802d-111">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="a802d-112">サーバーはクライアント資格情報をカスタム X509Certificate 検証と照合する。</span><span class="sxs-lookup"><span data-stu-id="a802d-112">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="a802d-113">サーバーがそのサーバーの X.509 証明書を使用して認証される。</span><span class="sxs-lookup"><span data-stu-id="a802d-113">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="a802d-114">サービスは、構成ファイル App.config を使用して定義された、サービスと通信するための単一のエンドポイントを公開します。エンドポイントは、アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-114">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a802d-115">バインディングは、 `wsHttpBinding` 既定でとクライアント証明書の認証を使用する標準で構成され `WSSecurity` ます。</span><span class="sxs-lookup"><span data-stu-id="a802d-115">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="a802d-116">サービス動作では、クライアントの X.509 証明書を検証するためのカスタム モード、および検証クラスの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-116">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="a802d-117">さらに、serviceCertificate 要素を使用しているサーバー証明書も指定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-117">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="a802d-118">サーバー証明書には、のと同じ値が含まれている必要があり `SubjectName` `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a802d-118">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="a802d-119">クライアント エンドポイント構成は、構成名、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-119">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="a802d-120">クライアント バインディングは、適切なモードおよびメッセージ `clientCredentialType` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-120">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

<span data-ttu-id="a802d-121">クライアントの実装では、使用するクライアント証明書を設定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-121">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

<span data-ttu-id="a802d-122">このサンプルでは、カスタム X509Certificate 検証を使用して証明書を検証します。</span><span class="sxs-lookup"><span data-stu-id="a802d-122">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="a802d-123">サンプルは、<xref:System.IdentityModel.Selectors.X509CertificateValidator> から派生するカスタム X509Certificate 検証を実装します。</span><span class="sxs-lookup"><span data-stu-id="a802d-123">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a802d-124">詳細については、<xref:System.IdentityModel.Selectors.X509CertificateValidator> に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802d-124">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="a802d-125">特定のカスタム検証を使用しているこのサンプルは、自己発行の任意の X.509 証明書を許可する Validate メソッドを実装しています。次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802d-125">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="a802d-126">サービス コードに検証を実装した場合、使用する検証インスタンスをサービス ホストに通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a802d-126">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="a802d-127">これは次のコードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-127">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="a802d-128">または、構成で次のように指定することで、同じことを実現できます。</span><span class="sxs-lookup"><span data-stu-id="a802d-128">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="a802d-129">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a802d-130">クライアントはすべてのメソッドを問題なく呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="a802d-130">The client should successfully call all the methods.</span></span> <span data-ttu-id="a802d-131">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a802d-131">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="a802d-132">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="a802d-132">Setup Batch File</span></span>

<span data-ttu-id="a802d-133">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a802d-133">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="a802d-134">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a802d-134">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="a802d-135">次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="a802d-135">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="a802d-136">サーバー証明書の作成 :</span><span class="sxs-lookup"><span data-stu-id="a802d-136">Creating the server certificate:</span></span>

     <span data-ttu-id="a802d-137">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="a802d-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="a802d-138">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="a802d-139">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-139">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a802d-140">既定値は、localhost です。</span><span class="sxs-lookup"><span data-stu-id="a802d-140">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a802d-141">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="a802d-141">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="a802d-142">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-142">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a802d-143">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="a802d-143">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a802d-144">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="a802d-144">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="a802d-145">クライアント証明書の作成 :</span><span class="sxs-lookup"><span data-stu-id="a802d-145">Creating the client certificate:</span></span>

     <span data-ttu-id="a802d-146">Setup.bat バッチ ファイルの次の行は、使用するクライアント証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="a802d-146">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="a802d-147">%USER_NAME% 変数はクライアント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a802d-147">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="a802d-148">この値は "test1" に設定されます。クライアント コードによってこの名前が検索されるためです。</span><span class="sxs-lookup"><span data-stu-id="a802d-148">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="a802d-149">%USER_NAME% の値を変更した場合は、Client.cs ソース ファイル内の対応する値を変更して、クライアントを再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a802d-149">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="a802d-150">証明書は、CurrentUser ストアの場所の My (Personal) ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-150">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a802d-151">クライアント証明書のサーバーの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="a802d-151">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="a802d-152">Setup.bat バッチ ファイルの次の行は、クライアント証明書を信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-152">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="a802d-153">この手順が必要なのは、Makecert.exe によって生成される証明書がサーバー システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="a802d-153">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="a802d-154">マイクロソフト発行の証明書など、信頼されたルート証明書に基づく証明書が既にある場合は、サーバー証明書ストアにクライアント証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="a802d-154">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a802d-155">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="a802d-155">To set up and build the sample</span></span>

1. <span data-ttu-id="a802d-156">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a802d-156">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="a802d-157">サンプルを単一コンピューター構成で実行するか、複数コンピューター構成で実行するかに応じて、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a802d-157">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a802d-158">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="a802d-158">To run the sample on the same computer</span></span>

1. <span data-ttu-id="a802d-159">管理者特権で開いた Visual Studio 2012 コマンドプロンプト内のサンプルのインストールフォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-159">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="a802d-160">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a802d-160">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a802d-161">Setup.bat バッチファイルは、Visual Studio 2012 のコマンドプロンプトから実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a802d-161">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="a802d-162">Visual Studio 2012 のコマンドプロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルを含むディレクトリを指します。</span><span class="sxs-lookup"><span data-stu-id="a802d-162">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="a802d-163">Service.exe を service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="a802d-163">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="a802d-164">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="a802d-164">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a802d-165">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-165">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="a802d-166">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802d-166">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a802d-167">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="a802d-167">To run the sample across computers</span></span>

1. <span data-ttu-id="a802d-168">サービス コンピューターにディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a802d-168">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="a802d-169">サービス プログラム ファイルを \service\bin からサービス コンピューターの仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-169">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="a802d-170">Setup.bat、Cleanup.bat、GetComputerName.vbs、ImportClientCert.bat の各ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-170">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="a802d-171">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a802d-171">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="a802d-172">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-172">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="a802d-173">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-173">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="a802d-174">サーバーで、 `setup.bat service` 管理者特権で開かれた Visual Studio の開発者コマンドプロンプトでを実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-174">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="a802d-175">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="a802d-175">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="a802d-176">Service.exe.config を編集して、新しい証明書名 ( `findValue` の属性) を反映し [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ます。これは、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="a802d-176">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a802d-177">また、要素のコンピューター名 \<service> / \<baseAddresses> を localhost からサービスコンピューターの完全修飾名に変更します。</span><span class="sxs-lookup"><span data-stu-id="a802d-177">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="a802d-178">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-178">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="a802d-179">クライアントで、 `setup.bat client` 管理者特権で開かれた Visual Studio の開発者コマンドプロンプトでを実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-179">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="a802d-180">`setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="a802d-180">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="a802d-181">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="a802d-181">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="a802d-182">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a802d-182">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="a802d-183">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a802d-183">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="a802d-184">クライアントで、管理者特権で開いた Visual Studio の開発者コマンドプロンプトで ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-184">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="a802d-185">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="a802d-185">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="a802d-186">サーバーで、管理者特権で開いた Visual Studio の開発者コマンドプロンプトで ImportClientCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-186">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="a802d-187">これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="a802d-187">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="a802d-188">サーバー コンピューターで、コマンド プロンプト ウィンドウから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="a802d-188">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="a802d-189">クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="a802d-189">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="a802d-190">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a802d-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a802d-191">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="a802d-191">To clean up after the sample</span></span>

1. <span data-ttu-id="a802d-192">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a802d-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="a802d-193">これにより、証明書ストアからサーバー証明書とクライアント証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a802d-193">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="a802d-194">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="a802d-194">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="a802d-195">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="a802d-195">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="a802d-196">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="a802d-196">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
