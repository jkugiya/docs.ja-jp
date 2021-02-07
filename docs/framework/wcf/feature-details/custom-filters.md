---
description: 詳細については、「カスタムフィルター」を参照してください。
title: カスタム フィルター
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 95a419823cf69575f951c0984e2136f9e7afca56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704980"
---
# <a name="custom-filters"></a><span data-ttu-id="ef8b3-103">カスタム フィルター</span><span class="sxs-lookup"><span data-stu-id="ef8b3-103">Custom Filters</span></span>

<span data-ttu-id="ef8b3-104">カスタム フィルターを使用すると、システムが提供するメッセージ フィルターを使用して実現できない一致ロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-104">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="ef8b3-105">たとえば、特定のメッセージ要素をハッシュし、その値を検証してフィルターが true または false のどちらを返すかを決定するカスタム フィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-105">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="ef8b3-106">実装</span><span class="sxs-lookup"><span data-stu-id="ef8b3-106">Implementation</span></span>  

 <span data-ttu-id="ef8b3-107">カスタム フィルターは、<xref:System.ServiceModel.Dispatcher.MessageFilter> 抽象基本クラスの実装です。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-107">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="ef8b3-108">カスタム フィルターを実装する場合は、コンストラクターが必要に応じて、文字列パラメーターを 1 つだけ受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-108">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="ef8b3-109">このパラメーターには、MessageFilter コンストラクターに渡される構成情報が含まれ、フィルターが照合を実行するために実行時に必要とする値や構成を指示します。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-109">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="ef8b3-110">これは、評価対象のメッセージ内でフィルターが検索する必要がある値を提供する場合などに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-110">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="ef8b3-111">文字列パラメーターを受け取るカスタムのメッセージ フィルターの基本の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-111">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="ef8b3-112">実際の実装では、Match メソッドには、このメッセージフィルターが **true** または **false** を返すかどうかを確認するメッセージを確認するロジックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-112">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="ef8b3-113">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="ef8b3-113">Performance</span></span>  

 <span data-ttu-id="ef8b3-114">カスタム フィルターを実装する場合は、フィルターがメッセージの評価を完了するのに要する最大時間を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-114">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="ef8b3-115">メッセージは、一致が見つかるまでに複数のフィルターに対して評価される場合があるので、すべてのフィルターを評価する前にクライアント要求がタイムアウトしないようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-115">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="ef8b3-116">したがって、カスタム フィルターのコードは、メッセージがフィルター条件に一致するかどうかを調べるために、メッセージのコンテンツまたは属性を評価するのに必要なコードだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-116">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="ef8b3-117">一般に、カスタム フィルターを実装する場合は、次のことを避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-117">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="ef8b3-118">IO。たとえば、ディスクやデータベースへのデータの保存です。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-118">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="ef8b3-119">不要な処理。たとえば、ドキュメントの複数のレコードのループ処理です。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-119">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="ef8b3-120">ブロック操作。たとえば、共有リソースに対するロックの取得を必要とする呼び出しや、データベースに対する検索の実行です。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-120">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="ef8b3-121">実稼働環境でカスタム フィルターを使用する前に、パフォーマンス テストを実行して、フィルターがメッセージを評価するのに要する平均時間を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-121">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="ef8b3-122">フィルター テーブルで使用される他のフィルターの平均処理時間と合わせることで、クライアント アプリケーションで指定する必要がある最大タイムアウト値を正確に計算できます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-122">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ef8b3-123">使用</span><span class="sxs-lookup"><span data-stu-id="ef8b3-123">Usage</span></span>  

 <span data-ttu-id="ef8b3-124">ルーティングサービスでカスタムフィルターを使用するには、"カスタム" 型の新しいフィルターエントリ、メッセージフィルターの完全修飾型名、およびアセンブリの名前を指定して、フィルターテーブルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-124">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="ef8b3-125">その他の MessageFilter と同様に、カスタム フィルターのコンストラクターに渡される文字列 filterData を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-125">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="ef8b3-126">カスタム フィルターをルーティング サービスと使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ef8b3-126">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
