---
description: '詳細: WCF 配信オブジェクトモデルを Atom と RSS にマップする方法について説明します。'
title: WCF 配信オブジェクト モデルを Atom や RSS に割り当てる方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: d66fb30acde18053e866b8986ebf71a6eed562ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742941"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="9143d-103">WCF 配信オブジェクト モデルを Atom や RSS に割り当てる方法</span><span class="sxs-lookup"><span data-stu-id="9143d-103">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>

<span data-ttu-id="9143d-104">Windows Communication Foundation (WCF) 配信サービスを開発する場合は、次のクラスを使用してフィードと項目を作成します。</span><span class="sxs-lookup"><span data-stu-id="9143d-104">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="9143d-105"><xref:System.ServiceModel.Syndication.SyndicationFeed> はフォーマッタが定義されている任意の配信フォーマットにシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="9143d-105">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="9143d-106">WCF には、とという2つのフォーマッタが付属 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> して <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> います。</span><span class="sxs-lookup"><span data-stu-id="9143d-106">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="9143d-107">RSS 2.0 仕様より Atom 1.0 仕様の方が、<xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationItem> 周辺のオブジェクト モデルをより細かく調整しています。</span><span class="sxs-lookup"><span data-stu-id="9143d-107">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="9143d-108">これは、Atom 1.0 が、あいまいな要素または RSS 2.0 仕様から省略された要素を定義する、より基本的な仕様であるためです。</span><span class="sxs-lookup"><span data-stu-id="9143d-108">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="9143d-109">このため、WCF 配信オブジェクトモデルの多くの項目は、RSS 2.0 仕様に直接表現されていません。</span><span class="sxs-lookup"><span data-stu-id="9143d-109">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="9143d-110"><xref:System.ServiceModel.Syndication.SyndicationFeed>とオブジェクトを <xref:System.ServiceModel.Syndication.SyndicationItem> RSS 2.0 にシリアル化する場合、WCF では、atom 仕様に準拠した名前空間で修飾された拡張要素として、atom 固有のデータ要素をシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="9143d-110">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="9143d-111">これは、<xref:System.ServiceModel.Syndication.Rss20FeedFormatter> コンストラクターに渡すパラメーターで制御できます。</span><span class="sxs-lookup"><span data-stu-id="9143d-111">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="9143d-112">このトピックのコード例では、ここで定義される 2 つのメソッドのいずれかを使い、実際のシリアル化を行っています。</span><span class="sxs-lookup"><span data-stu-id="9143d-112">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="9143d-113">`SerializeFeed` は、配信フィードをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="9143d-113">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="9143d-114">`SerializeItem` は、配信項目をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="9143d-114">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="9143d-115">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="9143d-115">SyndicationFeed</span></span>  

 <span data-ttu-id="9143d-116"><xref:System.ServiceModel.Syndication.SyndicationFeed> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-116">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="9143d-117"><xref:System.ServiceModel.Syndication.SyndicationFeed> を Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 <span data-ttu-id="9143d-118"><xref:System.ServiceModel.Syndication.SyndicationFeed> を RSS 2.0.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-118">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a><span data-ttu-id="9143d-119">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="9143d-119">SyndicationItem</span></span>  

 <span data-ttu-id="9143d-120"><xref:System.ServiceModel.Syndication.SyndicationItem> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-120">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="9143d-121"><xref:System.ServiceModel.Syndication.SyndicationItem> を Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 <span data-ttu-id="9143d-122"><xref:System.ServiceModel.Syndication.SyndicationItem> を RSS 2.0.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-122">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a><span data-ttu-id="9143d-123">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="9143d-123">SyndicationPerson</span></span>  

 <span data-ttu-id="9143d-124"><xref:System.ServiceModel.Syndication.SyndicationPerson> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-124">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="9143d-125"><xref:System.ServiceModel.Syndication.SyndicationPerson> を Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 <span data-ttu-id="9143d-126"><xref:System.ServiceModel.Syndication.SyndicationPerson> コレクションまたは <xref:System.ServiceModel.Syndication.SyndicationPerson> コレクションに、それぞれ `Authors` が 1 つのみ存在する場合に、`Contributors` クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="9143d-127"><xref:System.ServiceModel.Syndication.SyndicationPerson> コレクションまたは <xref:System.ServiceModel.Syndication.SyndicationPerson> コレクションに、それぞれ `Authors` が複数存在する場合に、`Contributors` クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-127">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a><span data-ttu-id="9143d-128">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="9143d-128">SyndicationLink</span></span>  

 <span data-ttu-id="9143d-129"><xref:System.ServiceModel.Syndication.SyndicationLink> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-129">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="9143d-130"><xref:System.ServiceModel.Syndication.SyndicationLink> を Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="9143d-131"><xref:System.ServiceModel.Syndication.SyndicationLink> を RSS 2.0.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-131">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="9143d-132">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="9143d-132">SyndicationCategory</span></span>  

 <span data-ttu-id="9143d-133"><xref:System.ServiceModel.Syndication.SyndicationCategory> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-133">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="9143d-134"><xref:System.ServiceModel.Syndication.SyndicationCategory> を Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="9143d-135"><xref:System.ServiceModel.Syndication.SyndicationCategory> を RSS 2.0.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-135">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="9143d-136">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="9143d-136">TextSyndicationContent</span></span>  

 <span data-ttu-id="9143d-137"><xref:System.ServiceModel.Syndication.TextSyndicationContent> が HTML コンテンツと共に作成される場合に <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-137">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="9143d-138">HTML コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="9143d-139">HTML コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-139">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="9143d-140"><xref:System.ServiceModel.Syndication.TextSyndicationContent> がプレーンテキスト コンテンツと共に作成される場合に、<xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-140">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="9143d-141">プレーンテキスト コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="9143d-142">プレーンテキスト コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-142">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="9143d-143"><xref:System.ServiceModel.Syndication.TextSyndicationContent> が XHTML コンテンツと共に作成される場合に、<xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-143">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="9143d-144">XHTML コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="9143d-145">XHTML コンテンツ付きの <xref:System.ServiceModel.Syndication.TextSyndicationContent> クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-145">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="9143d-146">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="9143d-146">UrlSyndicationContent</span></span>  

 <span data-ttu-id="9143d-147"><xref:System.ServiceModel.Syndication.UrlSyndicationContent> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-147">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="9143d-148"><xref:System.ServiceModel.Syndication.UrlSyndicationContent> クラスを Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="9143d-149">XHTML コンテンツ付きの <xref:System.ServiceModel.Syndication.UrlSyndicationContent> クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-149">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="9143d-150">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="9143d-150">XmlSyndicationContent</span></span>  

 <span data-ttu-id="9143d-151"><xref:System.ServiceModel.Syndication.XmlSyndicationContent> クラスを Atom 1.0 および RSS 2.0 にシリアル化するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-151">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="9143d-152"><xref:System.ServiceModel.Syndication.XmlSyndicationContent> クラスを Atom 1.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="9143d-153">XHTML コンテンツ付きの <xref:System.ServiceModel.Syndication.XmlSyndicationContent> クラスを RSS 2.0 にシリアル化する方法を次の XML に示します。</span><span class="sxs-lookup"><span data-stu-id="9143d-153">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="9143d-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="9143d-154">See also</span></span>

- [<span data-ttu-id="9143d-155">WCF 配信の概要</span><span class="sxs-lookup"><span data-stu-id="9143d-155">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)
- [<span data-ttu-id="9143d-156">配信のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9143d-156">Architecture of Syndication</span></span>](architecture-of-syndication.md)
- [<span data-ttu-id="9143d-157">方法: 基本的な RSS フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="9143d-157">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="9143d-158">方法: 基本的な ATOM フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="9143d-158">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="9143d-159">方法: Atom および RSS の両方としてフィードを公開する</span><span class="sxs-lookup"><span data-stu-id="9143d-159">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)
