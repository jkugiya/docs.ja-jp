---
description: '詳細情報: カスタムメッセージエンコーダー: 圧縮エンコーダー'
title: カスタム メッセージ エンコーダー:Expression Encoder
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 61c28435000333b1411a3fbcba485e0a252aed63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752519"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="83a9e-103">カスタム メッセージ エンコーダー:Expression Encoder</span><span class="sxs-lookup"><span data-stu-id="83a9e-103">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="83a9e-104">このサンプルでは、Windows Communication Foundation (WCF) プラットフォームを使用してカスタムエンコーダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-104">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83a9e-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83a9e-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="83a9e-107">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83a9e-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="83a9e-109">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="83a9e-109">Sample Details</span></span>

<span data-ttu-id="83a9e-110">このサンプルは、クライアント コンソール プログラム (.exe)、自己ホスト型サービス コンソール プログラム (.exe)、および圧縮メッセージ エンコーダー ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="83a9e-110">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="83a9e-111">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="83a9e-112">コントラクトは `ISampleServer` インターフェイスによって定義されます。このインターフェイスでは、基本的な文字列のエコー操作 (`Echo` と `BigEcho`) が公開されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-112">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="83a9e-113">クライアントは指定された操作を同期要求し、サービスはクライアントにメッセージをそのまま戻すことによって応答します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-113">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="83a9e-114">クライアント アクティビティとサービス アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-114">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="83a9e-115">このサンプルの目的は、カスタム エンコーダを記述する方法と、ネットワーク上でメッセージを圧縮したときの影響を示すことです。</span><span class="sxs-lookup"><span data-stu-id="83a9e-115">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="83a9e-116">圧縮メッセージ エンコーダーにインストルメンテーションを追加すると、メッセージのサイズ、処理時間、またはその両方を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-116">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="83a9e-117">.NET Framework 4 では、サーバーが (GZip や Deflate などのアルゴリズムで作成された) 圧縮された応答を送信する場合、WCF クライアントで自動展開が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="83a9e-117">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="83a9e-118">このサービスがインターネット インフォメーション サービス (IIS) で Web ホストされる場合は、サービスが圧縮された応答を送信するように IIS を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-118">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="83a9e-119">このサンプルは、クライアントとサービスの両方で圧縮および展開を行うという要件がある場合、またはサービスが自己ホスト型である場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-119">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="83a9e-120">このサンプルでは、カスタムメッセージエンコーダーを構築し、WCF アプリケーションに統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-120">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="83a9e-121">GZipEncoder.dll ライブラリは、クライアントとサービスの両方で配置されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-121">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="83a9e-122">また、このサンプルではメッセージを圧縮したときの影響も示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-122">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="83a9e-123">GZipEncoder.dll のコードでは、次が示されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-123">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="83a9e-124">カスタム エンコーダーおよびエンコーダー ファクトリの作成。</span><span class="sxs-lookup"><span data-stu-id="83a9e-124">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="83a9e-125">カスタム エンコーダのバインド要素の開発。</span><span class="sxs-lookup"><span data-stu-id="83a9e-125">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="83a9e-126">カスタム バインド要素を統合するためのカスタム バインド構成の使用。</span><span class="sxs-lookup"><span data-stu-id="83a9e-126">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="83a9e-127">カスタム バインド要素のファイル構成を可能にするカスタム構成ハンドラーの開発。</span><span class="sxs-lookup"><span data-stu-id="83a9e-127">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="83a9e-128">前に示したように、カスタム エンコーダにはいくつかのレイヤが実装されています。</span><span class="sxs-lookup"><span data-stu-id="83a9e-128">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="83a9e-129">こうした各レイヤ間の関係をわかりやすく説明するために、サービス起動のイベントの順序を簡略化した一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-129">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="83a9e-130">サーバーが起動します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-130">The server starts.</span></span>

2. <span data-ttu-id="83a9e-131">構成情報が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-131">The configuration information is read.</span></span>

    1. <span data-ttu-id="83a9e-132">サービス構成がカスタム構成ハンドラを登録します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-132">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="83a9e-133">サービス ホストが作成されて開かれます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-133">The service host is created and opened.</span></span>

    3. <span data-ttu-id="83a9e-134">カスタム構成要素がカスタム バインド要素を作成して返します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-134">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="83a9e-135">カスタム バインド要素がメッセージ エンコーダ ファクトリを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-135">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="83a9e-136">メッセージが受信されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-136">A message is received.</span></span>

4. <span data-ttu-id="83a9e-137">メッセージ エンコーダ ファクトリは、メッセージを読み込んで応答を出力するためのメッセージ エンコーダを返します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-137">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="83a9e-138">エンコーダ レイヤはクラス ファクトリとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-138">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="83a9e-139">カスタム エンコーダ用にパブリックに公開する必要があるのはエンコーダのクラス ファクトリだけです。</span><span class="sxs-lookup"><span data-stu-id="83a9e-139">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="83a9e-140"><xref:System.ServiceModel.ServiceHost> オブジェクトまたは <xref:System.ServiceModel.ChannelFactory%601> オブジェクトが作成されると、ファクトリ オブジェクトがバインド要素によって返されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-140">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="83a9e-141">メッセージ エンコーダは、バッファ モードまたはストリーミング モードで動作できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-141">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="83a9e-142">このサンプルでは、バッファ モードとストリーミング モードの両方を示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-142">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="83a9e-143">各モードの `ReadMessage` 抽象クラスには、関連する `WriteMessage` メソッドと `MessageEncoder` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-143">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="83a9e-144">エンコード処理の大部分はこれらのメソッドで行われます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-144">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="83a9e-145">サンプルでは、既存のテキスト エンコーダとバイナリ メッセージ エンコーダをラップします。</span><span class="sxs-lookup"><span data-stu-id="83a9e-145">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="83a9e-146">これにより、内部のエンコーダがネットワーク上でのメッセージの表現の読み取りと書き込みを代行し、圧縮エンコーダがその結果を圧縮または解凍できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-146">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="83a9e-147">メッセージエンコード用のパイプラインがないため、WCF で複数のエンコーダーを使用する唯一のモデルとなります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-147">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="83a9e-148">メッセージが解凍されると、結果として得られたメッセージは、処理対象のチャネル スタックの上にスタックとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-148">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="83a9e-149">圧縮中は、結果として得られる圧縮メッセージは指定されたストリームに直接書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-149">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="83a9e-150">このサンプルは、ヘルパー メソッド (`CompressBuffer` と `DecompressBuffer`) を使用して、バッファを、`GZipStream` クラスを使用するストリームに変換します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-150">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="83a9e-151">バッファ内の `ReadMessage` クラスと `WriteMessage` クラスは、`BufferManager` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-151">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="83a9e-152">エンコーダにはエンコーダ ファクトリを通じてのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-152">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="83a9e-153">`MessageEncoderFactory` 抽象クラスは、現在のエンコーダにアクセスするための `Encoder` という名前のプロパティと、セッションをサポートするエンコーダを作成するための `CreateSessionEncoder` という名前のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-153">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="83a9e-154">チャネルがセッションをサポートし、順序付けされて信頼できるシナリオでは、このようなエンコーダを使用できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-154">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="83a9e-155">このシナリオでは、ネットワークに書き込まれるデータの各セッションを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-155">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="83a9e-156">これが必要でない場合は、基本メソッドをオーバーロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-156">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="83a9e-157">`Encoder` プロパティは、セッションのないエンコーダにアクセスする機構を備えており、`CreateSessionEncoder` メソッドの既定の実装では、このプロパティの値が返されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-157">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="83a9e-158">サンプルでは既存のエンコーダをラップして圧縮を行うので、`MessageEncoderFactory` の実装では、内部のエンコーダ ファクトリを表す `MessageEncoderFactory` が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-158">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="83a9e-159">エンコーダーとエンコーダーファクトリが定義されたので、それらを WCF クライアントおよびサービスと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-159">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="83a9e-160">ただし、これらのエンコーダをチャネル スタックに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-160">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="83a9e-161"><xref:System.ServiceModel.ServiceHost> クラスと <xref:System.ServiceModel.ChannelFactory%601> クラスの派生クラスを作成して `OnInitialize` メソッドをオーバーライドすると、このエンコーダ ファクトリを手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-161">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="83a9e-162">また、カスタム バインド要素を介してエンコーダ ファクトリを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-162">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="83a9e-163">新しいカスタム バインド要素を作成するには、<xref:System.ServiceModel.Channels.BindingElement> クラスの派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-163">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="83a9e-164">ただし、バインド要素には複数の型があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-164">There are, however, several types of binding elements.</span></span> <span data-ttu-id="83a9e-165">カスタム バインド要素がメッセージ エンコード バインド要素として認識されるには、さらに <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> も実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-165">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="83a9e-166"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> は、新しいメッセージ エンコーダ ファクトリ (`CreateMessageEncoderFactory`) を作成するためのメソッドを公開します。このメソッドを実装すると、一致するメッセージ エンコーダ ファクトリのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-166">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="83a9e-167">また、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> にはアドレス バージョンを示すプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-167">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="83a9e-168">このサンプルでは既存のエンコーダをラップするので、サンプルの実装では既存のエンコーダ バインド要素もラップし、内部のエンコーダ バインド要素をコンストラクタへのパラメータとして設定して、プロパティを介して公開します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-168">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="83a9e-169">`GZipMessageEncodingBindingElement` クラスを実装する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-169">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

<span data-ttu-id="83a9e-170">`GZipMessageEncodingBindingElement` クラスは `IPolicyExportExtension` インターフェイスを実装しているので、次の例に示すように、このバインド要素はメタデータ内のポリシーとしてエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-170">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

<span data-ttu-id="83a9e-171">`GZipMessageEncodingBindingElementImporter` クラスは `IPolicyImportExtension` インターフェイスを実装しています。このクラスは `GZipMessageEncodingBindingElement` のポリシーをインポートします。</span><span class="sxs-lookup"><span data-stu-id="83a9e-171">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="83a9e-172">Svcutil.exe ツールを使用すると、ポリシーを構成ファイルにインポートして `GZipMessageEncodingBindingElement` を処理できます。これを行うには、Svcutil.exe.config に次のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-172">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="83a9e-173">これで、一致する圧縮エンコーダのバインド要素ができるので、新しいカスタム バインド オブジェクトを作成してそのカスタム バインド要素を追加すると、プログラムによって圧縮エンコーダのバインド要素をサービスまたはクライアントにフックできます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-173">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="83a9e-174">ほとんどのユーザー シナリオではこのコードで十分ですが、サービスが Web ホストの場合はファイル構成のサポートが重要になります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-174">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="83a9e-175">Web ホストのシナリオをサポートするには、カスタム構成ハンドラを開発して、カスタム バインディング要素をファイル内で構成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-175">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="83a9e-176">構成システム上にバインド要素の構成ハンドラーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-176">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="83a9e-177">バインド要素の構成ハンドラーは、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> クラスから派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-177">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="83a9e-178">は、 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> このセクション用に作成するバインド要素の型を構成システムに通知します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-178">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="83a9e-179">設定可能な `BindingElement` のすべての側面を、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 派生クラスのプロパティとして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-179">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="83a9e-180">は、 <xref:System.Configuration.ConfigurationPropertyAttribute> 属性がない場合に、構成要素の属性をプロパティにマップし、既定値を設定する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-180">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="83a9e-181">構成から値が読み込まれてプロパティに適用されると、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> メソッドが呼び出されます。このメソッドは、プロパティをバインディング要素の具体的なインスタンスに変換します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-181">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="83a9e-182">メソッドは、 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> 派生クラスのプロパティを、 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 新しく作成されたバインド要素に設定される値に変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-182">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="83a9e-183">`GZipMessageEncodingElement` を実装するサンプル コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-183">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

<span data-ttu-id="83a9e-184">この構成ハンドラーは、サービスまたはクライアントの App.config または Web.config の次の表現にマップされます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-184">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="83a9e-185">この構成ハンドラーを使用するには、 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 次のサンプル構成に示すように、要素内に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-185">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

<span data-ttu-id="83a9e-186">このサーバーを実行する場合は、操作要求および応答はコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-186">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="83a9e-187">サーバーをシャットダウンするには、ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-187">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="83a9e-188">このクライアントを実行する場合は、操作要求および応答はコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-188">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="83a9e-189">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-189">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83a9e-190">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="83a9e-190">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="83a9e-191">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="83a9e-191">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="83a9e-192">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="83a9e-192">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="83a9e-193">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="83a9e-193">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="83a9e-194">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="83a9e-194">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83a9e-195">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="83a9e-195">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83a9e-196">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-196">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="83a9e-197">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="83a9e-197">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83a9e-198">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="83a9e-198">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
