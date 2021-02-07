---
description: '詳細情報: ストリーミングフィードのサンプル'
title: ストリーミング フィードのサンプル
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 1de295391316396d6c454496d34d8b82ad8129d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668748"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="8d532-103">ストリーミング フィードのサンプル</span><span class="sxs-lookup"><span data-stu-id="8d532-103">Streaming Feeds Sample</span></span>

<span data-ttu-id="8d532-104">このサンプルでは、多数の項目が含まれた配信フィードを管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8d532-104">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="8d532-105">サーバー側のサンプルは、フィード内での個々の <xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトの作成を、項目がネットワーク ストリームに書き込まれる直前まで遅らせる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d532-105">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="8d532-106">クライアント側のサンプルは、カスタム配信フィード フォーマッタを使用して個々の項目をネットワーク ストリームから読み取り、読み取られたフィードがメモリに完全にバッファーされないようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d532-106">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="8d532-107">配信 API のストリーミング機能を十分に示すため、このサンプルでは、無数の項目を含むフィードがサーバーによって公開されるという多少通常とは異なるシナリオを使用しています。</span><span class="sxs-lookup"><span data-stu-id="8d532-107">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="8d532-108">この場合、サーバーは、クライアントがフィードから特定の数 (既定では 10) の項目を読み取ったと判断するまで、新しい項目をフィードに対して生成し続けます。</span><span class="sxs-lookup"><span data-stu-id="8d532-108">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="8d532-109">処理を簡単にするために、クライアントとサーバーは両方とも同じプロセスで実装され、共有 `ItemCounter` オブジェクトを使用して、クライアントによって生成された項目の数を追跡します。</span><span class="sxs-lookup"><span data-stu-id="8d532-109">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="8d532-110">`ItemCounter` 型は、サンプル シナリオを正常に終了するためにのみ存在し、示されるパターンの重要な要素ではありません。</span><span class="sxs-lookup"><span data-stu-id="8d532-110">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="8d532-111">このデモでは、(キーワードコンストラクトを使用して) Visual C# 反復子を使用し `yield return` ます。</span><span class="sxs-lookup"><span data-stu-id="8d532-111">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="8d532-112">反復子の詳細については、MSDN の「反復子の使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d532-112">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="8d532-113">サービス</span><span class="sxs-lookup"><span data-stu-id="8d532-113">Service</span></span>  

 <span data-ttu-id="8d532-114">次のコードに示すように、サービスは、1 つの操作で構成される基本的な <xref:System.ServiceModel.Web.WebGetAttribute> コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="8d532-114">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="8d532-115">次のコードに示すように、サービスは、`ItemGenerator` クラスを使用してこのコントラクトを実装し、反復子を使用する <xref:System.ServiceModel.Syndication.SyndicationItem> インスタンスの無数のストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d532-115">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="8d532-116">サービスの実装によってフィードが作成されると、項目のバッファされたコレクションの代わりに `ItemGenerator.GenerateItems()` の出力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8d532-116">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="8d532-117">その結果、項目のストリームはメモリに完全にはバッファされません。</span><span class="sxs-lookup"><span data-stu-id="8d532-117">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="8d532-118">この動作を確認するには、メソッド内のステートメントにブレークポイントを設定 `yield return` `ItemGenerator.GenerateItems()` し、サービスがメソッドの結果を返した後に、このブレークポイントが検出されたことを確認し `StreamedFeed()` ます。</span><span class="sxs-lookup"><span data-stu-id="8d532-118">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="8d532-119">クライアント</span><span class="sxs-lookup"><span data-stu-id="8d532-119">Client</span></span>  

 <span data-ttu-id="8d532-120">このサンプルのクライアントでは、フィードの項目をメモリにバッファする代わりに、個々の項目の実体化を遅延させるカスタム <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d532-120">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="8d532-121">カスタム `StreamedAtom10FeedFormatter` インスタンスの使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8d532-121">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="8d532-122">通常、<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> の呼び出しは、フィードのコンテンツ全体がネットワークから読み取られ、メモリにバッファされるまで返されません。</span><span class="sxs-lookup"><span data-stu-id="8d532-122">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="8d532-123">ただし、次のコードに示すように、`StreamedAtom10FeedFormatter` オブジェクトによって <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> がオーバーライドされ、バッファ内のコレクションの代わりに反復子が返されます。</span><span class="sxs-lookup"><span data-stu-id="8d532-123">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="8d532-124">その結果、各項目は、`ReadItems()` の結果を走査するクライアント アプリケーションで使用可能な状態になるまで、ネットワークから読み取られません。</span><span class="sxs-lookup"><span data-stu-id="8d532-124">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="8d532-125">この動作を確認するには、内のステートメントにブレークポイントを設定 `yield return` し、の `StreamedAtom10FeedFormatter.DelayReadItems()` 呼び出しが完了した後に、このブレークポイントが検出されたことを確認し `ReadFrom()` ます。</span><span class="sxs-lookup"><span data-stu-id="8d532-125">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="8d532-126">次の手順は、サンプルをビルドして実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d532-126">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="8d532-127">クライアントが 10 個の項目を読み取った後にサーバーによる項目の生成が停止されると、クライアントが読み取った項目数は 10 個より非常に多く出力されます。</span><span class="sxs-lookup"><span data-stu-id="8d532-127">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="8d532-128">これは、サンプルで使用されたネットワーキング バインディングによってデータが 4 キロバイト (KB) セグメントで転送されることが原因です。</span><span class="sxs-lookup"><span data-stu-id="8d532-128">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="8d532-129">このような場合、クライアントは、項目を 1 つでも読み取る前に 4 KB の項目データを受信します。</span><span class="sxs-lookup"><span data-stu-id="8d532-129">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="8d532-130">これは通常の動作です (適切にサイズが調整されたセグメントでストリーミングされた HTTP データを送信すると、パフォーマンスが向上します)。</span><span class="sxs-lookup"><span data-stu-id="8d532-130">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d532-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="8d532-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8d532-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d532-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8d532-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8d532-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8d532-134">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8d532-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8d532-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d532-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8d532-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d532-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8d532-137">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="8d532-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d532-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8d532-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="8d532-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d532-139">See also</span></span>

- [<span data-ttu-id="8d532-140">スタンドアロン診断フィード</span><span class="sxs-lookup"><span data-stu-id="8d532-140">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
