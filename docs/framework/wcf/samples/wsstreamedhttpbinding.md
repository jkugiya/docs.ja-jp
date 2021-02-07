---
description: '詳細情報: WSStreamedHttpBinding'
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: ef5b3bf3501f64389005ea1542874ff32a42ad82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668280"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="f8095-103">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f8095-103">WSStreamedHttpBinding</span></span>

<span data-ttu-id="f8095-104">このサンプルでは、HTTP トランスポート使用時にストリーミングをサポートする目的でデザインされたバインディングを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f8095-104">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="f8095-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8095-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8095-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8095-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8095-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f8095-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f8095-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f8095-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8095-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f8095-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="f8095-110">新しい標準バインディングを作成して構成する手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f8095-110">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="f8095-111">新しい標準バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="f8095-111">Create a new standard binding</span></span>

    <span data-ttu-id="f8095-112">BasicHttpBinding、netTcpBinding などの Windows Communication Foundation (WCF) の標準バインディングでは、特定の要件に応じて基になるトランスポートとチャネルスタックを構成します。</span><span class="sxs-lookup"><span data-stu-id="f8095-112">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="f8095-113">このサンプルでは、`WSStreamedHttpBinding` は、ストリーミングをサポートするようチャネル スタックを構成します。</span><span class="sxs-lookup"><span data-stu-id="f8095-113">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="f8095-114">既定では、WS-Security と信頼できるメッセージ機能はチャネル スタックに追加されません。どちらの機能もストリーミングではサポートされないためです。</span><span class="sxs-lookup"><span data-stu-id="f8095-114">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="f8095-115">新しいバインディングは、`WSStreamedHttpBinding` から派生するクラス <xref:System.ServiceModel.Channels.Binding> に実装されます。</span><span class="sxs-lookup"><span data-stu-id="f8095-115">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="f8095-116">`WSStreamedHttpBinding` には、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>、および <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> のバインド要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8095-116">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="f8095-117">このクラスは、作成されるバインディング スタックを構成する `CreateBindingElements()` メソッドを提供します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8095-117">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. <span data-ttu-id="f8095-118">構成サポートを追加する</span><span class="sxs-lookup"><span data-stu-id="f8095-118">Add configuration support</span></span>

    <span data-ttu-id="f8095-119">構成を使用してトランスポートを公開するため、サンプルではさらに、`WSStreamedHttpBindingConfigurationElement` クラスと `WSStreamedHttpBindingSection` クラスという 2 つのクラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="f8095-119">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="f8095-120">クラスは、 `WSStreamedHttpBindingSection` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> `WSStreamedHttpBinding` WCF 構成システムに公開するです。</span><span class="sxs-lookup"><span data-stu-id="f8095-120">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="f8095-121">実装の大部分は `WSStreamedHttpBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。</span><span class="sxs-lookup"><span data-stu-id="f8095-121">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="f8095-122">クラス `WSStreamedHttpBindingConfigurationElement` には `WSStreamedHttpBinding` のプロパティに対応するプロパティがあり、各構成要素をバインディングにマップする関数があります。</span><span class="sxs-lookup"><span data-stu-id="f8095-122">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="f8095-123">次のセクションをサービスの構成ファイルに追加することにより、ハンドラを構成システムに登録します。</span><span class="sxs-lookup"><span data-stu-id="f8095-123">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="f8095-124">ハンドラーは serviceModel 構成セクションから参照できます。</span><span class="sxs-lookup"><span data-stu-id="f8095-124">The handler can then be referenced from the serviceModel configuration section.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8095-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f8095-125">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f8095-126">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f8095-126">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="f8095-127">[Windows Communication Foundation のサンプルについ](one-time-setup-procedure-for-the-wcf-samples.md)ては、1回限りのセットアップ手順に記載されている手順を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8095-127">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="f8095-128">[インターネットインフォメーションサービス (IIS) サーバー証明書のインストール手順](iis-server-certificate-installation-instructions.md)を実行していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8095-128">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="f8095-129">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f8095-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="f8095-130">複数コンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f8095-130">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

6. <span data-ttu-id="f8095-131">クライアント ウィンドウが表示されたら、「Sample.txt」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f8095-131">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="f8095-132">ディレクトリで "Sample.txt のコピー" を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8095-132">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="f8095-133">WSStreamedHttpBinding サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="f8095-133">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="f8095-134">`WSStreamedHttpBinding` を使用するサービスのサンプルは、サービス サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="f8095-134">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="f8095-135">`OperationContract` の実装は `MemoryStream` を使用して、最初に受信ストリームからすべてのデータを取得し、その後 `MemoryStream` を返します。</span><span class="sxs-lookup"><span data-stu-id="f8095-135">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="f8095-136">このサンプル サービスは、インターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="f8095-136">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="f8095-137">WSStreamedHttpBinding クライアントのサンプル</span><span class="sxs-lookup"><span data-stu-id="f8095-137">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="f8095-138">`WSStreamedHttpBinding` を使用してサービスとやり取りするクライアントは、クライアント サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="f8095-138">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="f8095-139">このサンプルで使用される証明書は Makecert.exe で作成されたテスト証明書であるため、などのブラウザーで HTTPS アドレスにアクセスしようとすると、セキュリティ警告が表示され `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="f8095-139">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="f8095-140">WCF クライアントがテスト証明書を使用できるようにするために、セキュリティの警告を抑制するために、クライアントに追加のコードがいくつか追加されています。</span><span class="sxs-lookup"><span data-stu-id="f8095-140">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="f8095-141">そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="f8095-141">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
