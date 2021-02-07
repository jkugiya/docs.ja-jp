---
description: 詳細については、「WS トランスポートセキュリティ」を参照してください。
title: WS トランスポート セキュリティ
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 0fc09815e757e1cda1a7fd196e33fab4d56d2cde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668358"
---
# <a name="ws-transport-security"></a><span data-ttu-id="01978-103">WS トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01978-103">WS Transport Security</span></span>

<span data-ttu-id="01978-104">このサンプルでは、<xref:System.ServiceModel.WSHttpBinding> バインディングを使用した SSL トランスポート セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="01978-104">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="01978-105">既定で、`wsHttpBinding` バインディングは HTTP 通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="01978-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="01978-106">トランスポート セキュリティ用に構成すると、バインディングは HTTPS 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="01978-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="01978-107">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="01978-107">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="01978-108">`wsHttpBinding` は、クライアントとサービスのアプリケーション構成ファイルに指定され、構成されます。</span><span class="sxs-lookup"><span data-stu-id="01978-108">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01978-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01978-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01978-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="01978-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01978-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="01978-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="01978-112">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="01978-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01978-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="01978-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="01978-114">サンプル内のプログラムコードは、 [はじめに](getting-started-sample.md) サービスのプログラムコードと同じです。</span><span class="sxs-lookup"><span data-stu-id="01978-114">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="01978-115">このサンプルをビルドして実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="01978-115">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="01978-116">次に示すクライアント用構成の例のように、構成ファイル設定でエンドポイントとバインディングを定義すると、`Transport` セキュリティ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="01978-116">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="01978-117">指定されたアドレスはスキームを使用し `https://` ます。</span><span class="sxs-lookup"><span data-stu-id="01978-117">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="01978-118">このバインド構成により、セキュリティ モードが `Transport` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="01978-118">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="01978-119">同じセキュリティ モードが、サービスの Web.config ファイルで指定される必要があります。</span><span class="sxs-lookup"><span data-stu-id="01978-119">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="01978-120">このサンプルで使用される証明書は Makecert.exe で作成されたテスト証明書であるため、ブラウザーからなどの https: アドレスにアクセスしようとすると、セキュリティの警告が表示され `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="01978-120">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="01978-121">Windows Communication Foundation (WCF) クライアントが適切なテスト証明書を使用できるようにするために、セキュリティの警告を抑制するために、いくつかの追加のコードがクライアントに追加されました。</span><span class="sxs-lookup"><span data-stu-id="01978-121">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="01978-122">そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="01978-122">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="01978-123">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="01978-123">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="01978-124">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="01978-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01978-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="01978-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="01978-126">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="01978-126">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="01978-127">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="01978-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="01978-128">[インターネットインフォメーションサービス (IIS) サーバー証明書のインストール手順](iis-server-certificate-installation-instructions.md)を実行していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="01978-128">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="01978-129">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="01978-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="01978-130">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="01978-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
