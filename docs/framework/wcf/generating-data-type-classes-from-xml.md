---
description: 詳細については、「XML からのデータ型クラスの生成」を参照してください。
title: XML からのデータ型クラスの生成
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: c79550b1e4804426267aef33860bc49d5d3b5efa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632140"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="ad165-103">XML からのデータ型クラスの生成</span><span class="sxs-lookup"><span data-stu-id="ad165-103">Generating Data Type Classes from XML</span></span>

<span data-ttu-id="ad165-104">.NET Framework 4.5 には、XML からデータ型クラスを生成するための新しい機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad165-104">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="ad165-105">このトピックでは、.NET ブログ RSS フィードのデータ型を自動的に生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad165-105">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="ad165-106">.NET ブログの RSS フィードから XML を取得する</span><span class="sxs-lookup"><span data-stu-id="ad165-106">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="ad165-107">Internet Explorer で、 [.Net ブログの RSS フィード](https://devblogs.microsoft.com/dotnet/feed/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="ad165-107">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="ad165-108">ページを右クリックし、[ **ソースの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad165-108">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="ad165-109">Ctrl キーを押し **ながら A** キーを押してすべてのテキストを選択し、 **ctrl + C** キーを押してコピーすることで、フィードのテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="ad165-109">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="ad165-110">データ型の作成</span><span class="sxs-lookup"><span data-stu-id="ad165-110">Creating the data types</span></span>  
  
1. <span data-ttu-id="ad165-111">プロキシが使用されるコード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ad165-111">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="ad165-112">このファイルは、.NET Framework 4.5 プロジェクトの一部である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad165-112">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="ad165-113">既存のクラスの外部にあるファイルの場所にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="ad165-113">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="ad165-114">[ **編集**]、[ **特殊な貼り付け**]、[ **XML をクラスとして貼り付ける**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad165-114">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="ad165-115">、、 `link` `rss` `rssChannel` 、 `rssChannelImage` 、 `rssChannelItem` およびというクラスは、 `rssChannelItemGuid` RSS フィード内の要素にアクセスするために必要なメンバーと共に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ad165-115">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="ad165-116">生成されたクラスの使用</span><span class="sxs-lookup"><span data-stu-id="ad165-116">Using the generated classes</span></span>  
  
1. <span data-ttu-id="ad165-117">クラスが生成されると、他のクラスのコードなどで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad165-117">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="ad165-118">次のコード例では、`rssChannelImage` クラスの新しいインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ad165-118">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
