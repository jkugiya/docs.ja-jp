---
description: 詳細については、「カスタムバインディングの信頼できるセッション」を参照してください。
title: カスタム バインディングの信頼できるセッション
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 0799e10c0fb86727bc21553584646031dc6f3606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752516"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="fc7be-103">カスタム バインディングの信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="fc7be-103">Custom Binding Reliable Session</span></span>

<span data-ttu-id="fc7be-104">カスタム バインドは、個々のバインド要素の順序付きリストとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="fc7be-104">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="fc7be-105">このサンプルでは、さまざまなトランスポートとメッセージ エンコーディング要素を使用し、特に信頼できるセッションを有効化することによって、カスタム バインディングを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fc7be-105">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc7be-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc7be-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc7be-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fc7be-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fc7be-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="fc7be-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc7be-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fc7be-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="fc7be-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="fc7be-110">Sample Details</span></span>

<span data-ttu-id="fc7be-111">信頼できるセッションは、信頼できるメッセージとセッションに関する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc7be-111">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="fc7be-112">信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fc7be-112">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="fc7be-113">セッションでは、呼び出し間でクライアントの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="fc7be-113">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="fc7be-114">サンプルでは、クライアントの状態を保持するセッションを実装し、配信順序を保証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc7be-114">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="fc7be-115">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="fc7be-115">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="fc7be-116">信頼できるセッション機能は、クライアントとサービスのアプリケーション構成ファイルで有効化され、構成されています。</span><span class="sxs-lookup"><span data-stu-id="fc7be-116">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="fc7be-117">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc7be-117">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="fc7be-118">バインディング要素の順序は、カスタムバインディングを定義する際に重要です。これは、それぞれがチャネルスタック内のレイヤーを表しているためです (「 [カスタムバインド](../extending/custom-bindings.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fc7be-118">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="fc7be-119">サンプルのサービス構成は、次のコード例のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="fc7be-119">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="fc7be-120">複数コンピュータのシナリオで実行する場合は、クライアントのエンドポイント アドレスをサービスのホスト名に合わせて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc7be-120">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="fc7be-121">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc7be-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fc7be-122">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fc7be-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc7be-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="fc7be-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fc7be-124">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="fc7be-124">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="fc7be-125">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fc7be-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="fc7be-126">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fc7be-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="fc7be-127">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fc7be-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fc7be-128">複数コンピューター構成でクライアントを実行する場合は、次の例に示すように、要素の属性との属性の両方で "localhost" を `address` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `clientBaseAddress` [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 適切なコンピューターの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="fc7be-128">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
