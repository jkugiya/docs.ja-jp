---
description: '詳細情報: 厳密に型指定された拡張機能のサンプル'
title: 厳密に型指定された拡張機能のサンプル
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: dd0a12b07db3f805f041742c8957cd46bb418bad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668761"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="3e021-103">厳密に型指定された拡張機能のサンプル</span><span class="sxs-lookup"><span data-stu-id="3e021-103">Strongly typed extensions sample</span></span>

<span data-ttu-id="3e021-104">このサンプルでは、例を示す目的で <xref:System.ServiceModel.Syndication.SyndicationFeed> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e021-104">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="3e021-105">ただし、このサンプルで示すパターンは、拡張データをサポートするすべての配信クラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e021-105">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="3e021-106">配信オブジェクト モデル (<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem>、および関連クラス) は、<xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> プロパティおよび <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> プロパティを使用することにより、拡張データへの弱い型定義によるアクセスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3e021-106">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="3e021-107">このサンプルでは <xref:System.ServiceModel.Syndication.SyndicationFeed> 、 <xref:System.ServiceModel.Syndication.SyndicationItem> 特定のアプリケーション固有の拡張機能を厳密に型指定されたプロパティとして使用できる、およびのカスタム派生クラスを実装することで、拡張データへの厳密に型指定されたアクセスを提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3e021-107">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="3e021-108">例として、このサンプルでは Atom Threading Extensions の RFC 案で定義された拡張要素を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3e021-108">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="3e021-109">このサンプルは、使い方を示すために用意されたものであり、仕様案を完全に実装するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="3e021-109">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="3e021-110">サンプル XML</span><span class="sxs-lookup"><span data-stu-id="3e021-110">Sample XML</span></span>  

 <span data-ttu-id="3e021-111">次の XML の例は、`<in-reply-to>` 拡張要素が追加された Atom 1.0 エントリを示しています。</span><span class="sxs-lookup"><span data-stu-id="3e021-111">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="3e021-112">`<in-reply-to>`要素は、3つの必須の属性 (、および) を指定しますが、 `ref` 追加の `type` `href` 拡張属性と拡張要素も存在できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e021-112">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="3e021-113">In-Reply-To 要素のモデル化</span><span class="sxs-lookup"><span data-stu-id="3e021-113">Modeling the In-Reply-To element</span></span>  

 <span data-ttu-id="3e021-114">このサンプルでは、`<in-reply-to>` 要素は <xref:System.Xml.Serialization.IXmlSerializable> を実装する CLR としてモデル化されており、<xref:System.Runtime.Serialization.DataContractSerializer> と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e021-114">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="3e021-115">また、次のサンプルコードに示すように、要素のデータにアクセスするためのメソッドとプロパティも実装しています。</span><span class="sxs-lookup"><span data-stu-id="3e021-115">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="3e021-116">`InReplyToElement` クラスは、必須の属性 (`HRef`、`MediaType`、および `Source`) のプロパティと共に、<xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> および <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> を保持するコレクションを実装します。</span><span class="sxs-lookup"><span data-stu-id="3e021-116">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="3e021-117">`InReplyToElement` クラスは、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装します。このインターフェイスは、オブジェクト インスタンスを XML から読み取る、または書き込む方法の直接制御を可能にします。</span><span class="sxs-lookup"><span data-stu-id="3e021-117">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="3e021-118">`ReadXml` メソッドは、渡された `Ref` から `HRef`、`Source`、`MediaType`、および <xref:System.Xml.XmlReader> の各プロパティを最初に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3e021-118">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="3e021-119">不明な属性は<xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> コレクションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e021-119">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="3e021-120">すべての属性が読み取られると、<xref:System.Xml.XmlReader.ReadStartElement> が呼び出されて、リーダーが次の要素に進みます。</span><span class="sxs-lookup"><span data-stu-id="3e021-120">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="3e021-121">次のコードに示すように、このクラスによりモデル化された要素には必須の子がないので、子要素は `XElement` インスタンスにバッファされ、<xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> コレクションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e021-121">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="3e021-122">`WriteXml` では、`InReplyToElement` メソッドは最初に `Ref`、`HRef`、`Source`、および `MediaType` の各プロパティの値を XML 属性として書き込みます (`WriteXml` は、実際の外側の要素自体は書き込みません。`WriteXml` により行われるためです)。</span><span class="sxs-lookup"><span data-stu-id="3e021-122">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="3e021-123">また、次のコードに示すように、<xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> および <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> の内容をライタに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3e021-123">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="3e021-124">ThreadedFeed および ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="3e021-124">ThreadedFeed and ThreadedItem</span></span>  

 <span data-ttu-id="3e021-125">このサンプルでは、`SyndicationItems` 拡張が存在する `InReplyTo` が `ThreadedItem` クラスによりモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="3e021-125">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="3e021-126">同様に、`ThreadedFeed` クラスは、項目が `SyndicationFeed` のすべてのインスタンスである `ThreadedItem` です。</span><span class="sxs-lookup"><span data-stu-id="3e021-126">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="3e021-127">`ThreadedFeed` クラスは、`SyndicationFeed` から継承され、`OnCreateItem` をオーバーライドして `ThreadedItem` を返します。</span><span class="sxs-lookup"><span data-stu-id="3e021-127">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="3e021-128">また、次のコードに示すように、`Items` コレクションにアクセスするメソッドを `ThreadedItems` として実装します。</span><span class="sxs-lookup"><span data-stu-id="3e021-128">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="3e021-129">クラスは、 `ThreadedItem` を継承 `SyndicationItem` し、 `InReplyToElement` 厳密に型指定されたプロパティとしてを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e021-129">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="3e021-130">これにより、`InReplyTo` 拡張データにプログラムによって簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3e021-130">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="3e021-131">また、次のコードに示すように、その拡張データの読み取り/書き込みを行う `TryParseElement` および `WriteElementExtensions` も実装します。</span><span class="sxs-lookup"><span data-stu-id="3e021-131">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e021-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3e021-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3e021-133">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e021-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3e021-134">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3e021-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3e021-135">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3e021-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3e021-136">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e021-136">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3e021-137">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3e021-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3e021-138">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3e021-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e021-139">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e021-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
