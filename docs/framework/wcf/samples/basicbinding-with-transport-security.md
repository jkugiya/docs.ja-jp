---
description: 詳細については、「トランスポートセキュリティを使用した BasicBinding」を参照してください。
title: トランスポート セキュリティ付き BasicBinding
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: e3d196136fcf91e3e61f82cee7e16421db221192
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755903"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="e8b76-103">トランスポート セキュリティ付き BasicBinding</span><span class="sxs-lookup"><span data-stu-id="e8b76-103">BasicBinding with Transport Security</span></span>

<span data-ttu-id="e8b76-104">このサンプルでは、基本的なバインディングを使用した SSL トランスポート セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-104">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="e8b76-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e8b76-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8b76-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8b76-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8b76-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e8b76-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e8b76-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="e8b76-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8b76-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e8b76-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a><span data-ttu-id="e8b76-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="e8b76-110">Sample Details</span></span>

<span data-ttu-id="e8b76-111">既定で、基本的なバインディングは HTTP 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e8b76-111">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="e8b76-112">このサンプルでは、基本的なバインディングのトランスポート セキュリティを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-112">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="e8b76-113">このサンプルを実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8b76-113">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>

> [!NOTE]
> <span data-ttu-id="e8b76-114">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8b76-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e8b76-115">サンプル内のプログラムコードは、 [はじめに](getting-started-sample.md) サービスのプログラムコードと同じです。</span><span class="sxs-lookup"><span data-stu-id="e8b76-115">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="e8b76-116">次に示すサンプル構成のように、構成ファイル設定でエンドポイントとバインディングを定義すると、通信のセキュリティ保護が有効になるように変更されます。</span><span class="sxs-lookup"><span data-stu-id="e8b76-116">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="e8b76-117">このサンプルで使用される証明書は Makecert.exe で作成されたテスト証明書であるため、ブラウザーで HTTPS: アドレスにアクセスしようとすると (など)、セキュリティ警告が表示され `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="e8b76-117">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="e8b76-118">Windows Communication Foundation (WCF) クライアントがテスト証明書を使用できるようにするには、セキュリティの警告を抑制するために、いくつかの追加コードをクライアントに追加します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-118">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="e8b76-119">そのためのコードとそれに必要なクラスは、実際の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="e8b76-119">This code, and the accompanying class, is not necessary when using real certificates.</span></span>

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```

<span data-ttu-id="e8b76-120">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8b76-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e8b76-121">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8b76-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e8b76-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e8b76-123">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="e8b76-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="e8b76-124">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="e8b76-125">[インターネットインフォメーションサービス (IIS) サーバー証明書のインストール手順](iis-server-certificate-installation-instructions.md)を実行していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e8b76-125">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="e8b76-126">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e8b76-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="e8b76-127">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e8b76-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>
