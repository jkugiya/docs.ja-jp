---
description: '詳細情報: Loosely-Typed 拡張機能のサンプル'
title: 弱く型指定された拡張のサンプル
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: cd430a922a35baf0ed9ce387b7df81fa3af6b35d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793234"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="2e18c-103">弱く型指定された拡張のサンプル</span><span class="sxs-lookup"><span data-stu-id="2e18c-103">Loosely-Typed Extensions Sample</span></span>

<span data-ttu-id="2e18c-104">配信オブジェクト モデルでは、拡張データをさまざまな方法で処理できます。拡張データとは、配信フィードの XML 表現に含まれているが、<xref:System.ServiceModel.Syndication.SyndicationFeed> や <xref:System.ServiceModel.Syndication.SyndicationItem> などのクラスによって明示的に公開されない情報のことです。</span><span class="sxs-lookup"><span data-stu-id="2e18c-104">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="2e18c-105">このサンプルでは、拡張データを処理する基本的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2e18c-105">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="2e18c-106">このサンプルでは、例を示す目的で <xref:System.ServiceModel.Syndication.SyndicationFeed> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2e18c-106">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="2e18c-107">ただし、このサンプルで示すパターンは、拡張データをサポートするすべての配信クラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-107">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="2e18c-108">サンプル XML</span><span class="sxs-lookup"><span data-stu-id="2e18c-108">Sample XML</span></span>  

 <span data-ttu-id="2e18c-109">このサンプルで使用される XML ドキュメントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2e18c-109">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="2e18c-110">このドキュメントには、次の拡張データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2e18c-110">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="2e18c-111">`myAttribute` 要素の `<feed>` 属性。</span><span class="sxs-lookup"><span data-stu-id="2e18c-111">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="2e18c-112">`<simpleString>` 要素。</span><span class="sxs-lookup"><span data-stu-id="2e18c-112">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="2e18c-113">`<DataContractExtension>` 要素。</span><span class="sxs-lookup"><span data-stu-id="2e18c-113">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="2e18c-114">`<XmlSerializerExtension>` 要素。</span><span class="sxs-lookup"><span data-stu-id="2e18c-114">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="2e18c-115">`<xElementExtension>` 要素。</span><span class="sxs-lookup"><span data-stu-id="2e18c-115">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="2e18c-116">拡張データの書き込み</span><span class="sxs-lookup"><span data-stu-id="2e18c-116">Writing Extension Data</span></span>  

 <span data-ttu-id="2e18c-117">属性の拡張は、次のサンプル コードに示すように、エントリを <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> コレクションに追加することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-117">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="2e18c-118">要素拡張は、エントリを <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> コレクションに追加することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-118">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="2e18c-119">これらの拡張には、文字列などの基本的な値、.NET Framework オブジェクトの XML シリアル化、および手動で入力された XML ノードを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-119">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="2e18c-120">次のサンプル コードでは、`simpleString` という拡張要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-120">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="2e18c-121">この要素の XML 名前空間は空の名前空間 ("") で、その値は文字列 "hello, world!" を含むテキストノードです。</span><span class="sxs-lookup"><span data-stu-id="2e18c-121">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="2e18c-122">入れ子になった多数の要素で構成される複雑な要素拡張を作成する方法の 1 つに、次の例に示すように、.NET Framework API をシリアル化に使用する方法があります (<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Xml.Serialization.XmlSerializer> の両方がサポートされています)。</span><span class="sxs-lookup"><span data-stu-id="2e18c-122">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="2e18c-123">この例の `DataContractExtension` と `XmlSerializerExtension` は、シリアライザで使用するために記述されたカスタム型です。</span><span class="sxs-lookup"><span data-stu-id="2e18c-123">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="2e18c-124"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> クラスを使用すると、<xref:System.Xml.XmlReader> インスタンスから要素拡張を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-124">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="2e18c-125">これによって、次のサンプル コードに示すように、<xref:System.Xml.Linq.XElement> などの XML 処理 API と簡単に統合できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2e18c-125">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="2e18c-126">拡張データの読み取り</span><span class="sxs-lookup"><span data-stu-id="2e18c-126">Reading Extension Data</span></span>  

 <span data-ttu-id="2e18c-127">属性の拡張の値は、次のサンプル コードに示すように、<xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> を使用して <xref:System.Xml.XmlQualifiedName> コレクションの属性を検索することによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-127">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="2e18c-128">要素拡張には、`ReadElementExtensions<T>` メソッドを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2e18c-128">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="2e18c-129">`XmlReader` メソッドを使用して、個々の要素拡張で <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> を取得することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2e18c-129">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e18c-130">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="2e18c-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2e18c-131">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2e18c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2e18c-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2e18c-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2e18c-133">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2e18c-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2e18c-134">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2e18c-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e18c-135">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2e18c-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2e18c-136">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="2e18c-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e18c-137">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2e18c-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="2e18c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e18c-138">See also</span></span>

- [<span data-ttu-id="2e18c-139">厳密に型指定された拡張機能</span><span class="sxs-lookup"><span data-stu-id="2e18c-139">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="2e18c-140">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="2e18c-140">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
