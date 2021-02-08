---
description: 詳細については、「HTTPS 経由のカスタムバインドの信頼できるセッション」を参照してください。
title: HTTPS を介したカスタム バインドの信頼できるセッション
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: ed02ce8ea199b5e7ae744fb0eacf168ea5fa85df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778296"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="565d4-103">HTTPS を介したカスタム バインドの信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="565d4-103">Custom Binding Reliable Session over HTTPS</span></span>

<span data-ttu-id="565d4-104">このサンプルでは、信頼できるセッションを使用した SSL トランスポート セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="565d4-104">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="565d4-105">信頼できるセッションは、WS-ReliableMessaging プロトコルを実装しています。</span><span class="sxs-lookup"><span data-stu-id="565d4-105">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="565d4-106">信頼できるセッションを介して WS-Security を構築することにより、セキュリティで保護された信頼できるセッションを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="565d4-106">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="565d4-107">ただし、SSL による HTTP トランスポート セキュリティの使用を選択できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="565d4-107">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="565d4-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="565d4-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="565d4-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="565d4-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="565d4-110">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="565d4-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="565d4-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="565d4-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="565d4-112">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="565d4-112">Sample Details</span></span>  

 <span data-ttu-id="565d4-113">SSL では、パケット自体のセキュリティが保護されます。</span><span class="sxs-lookup"><span data-stu-id="565d4-113">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="565d4-114">WS-SecureConversation を使用して、信頼できるセッションのセキュリティを保護する場合とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="565d4-114">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="565d4-115">HTTPS を介して信頼できるセッションを使用するには、カスタム バインドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="565d4-115">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="565d4-116">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="565d4-116">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="565d4-117">カスタムバインディングは、信頼できるセッションのバインディング要素とを使用して作成され [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md) ます。</span><span class="sxs-lookup"><span data-stu-id="565d4-117">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="565d4-118">カスタム バインドの構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="565d4-118">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="565d4-119">サンプル内のプログラムコードは、 [はじめに](getting-started-sample.md) サービスのプログラムコードと同じです。</span><span class="sxs-lookup"><span data-stu-id="565d4-119">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="565d4-120">このサンプルをビルドして実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="565d4-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="565d4-121">次に示すクライアント用構成の例のように、構成ファイル設定でエンドポイントとバインディングを定義すると、カスタム バインドの使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="565d4-121">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="565d4-122">指定されたアドレスはスキームを使用し `https://` ます。</span><span class="sxs-lookup"><span data-stu-id="565d4-122">The address specified uses the `https://` scheme.</span></span>  
  
 <span data-ttu-id="565d4-123">このサンプルで使用される証明書は Makecert.exe で作成されたテスト証明書であるため、ブラウザーからなどの https: アドレスにアクセスしようとすると、セキュリティの警告が表示され `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="565d4-123">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="565d4-124">Windows Communication Foundation (WCF) クライアントが適切なテスト証明書を使用できるようにするために、セキュリティの警告を抑制するために、いくつかの追加のコードがクライアントに追加されました。</span><span class="sxs-lookup"><span data-stu-id="565d4-124">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="565d4-125">そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="565d4-125">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="565d4-126">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="565d4-126">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="565d4-127">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="565d4-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="565d4-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="565d4-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="565d4-129">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="565d4-129">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="565d4-130">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="565d4-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="565d4-131">[インターネットインフォメーションサービス (IIS) サーバー証明書のインストール手順](iis-server-certificate-installation-instructions.md)を実行していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="565d4-131">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="565d4-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="565d4-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="565d4-133">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="565d4-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
