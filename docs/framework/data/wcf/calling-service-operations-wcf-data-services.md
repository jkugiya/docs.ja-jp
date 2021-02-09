---
description: '詳細情報: サービス操作の呼び出し (WCF Data Services)'
title: サービス操作の呼び出し (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 49b08581e42fcd20b9d560d73379eb43ebbf2eb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766466"
---
# <a name="calling-service-operations-wcf-data-services"></a><span data-ttu-id="53bc5-103">サービス操作の呼び出し (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="53bc5-103">Calling Service Operations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="53bc5-104">Open Data Protocol (OData) では、データ サービスのサービス操作が定義されています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-104">The Open Data Protocol (OData) defines service operations for a data service.</span></span> <span data-ttu-id="53bc5-105">WCF Data Services では、データ サービスのメソッドとしてこのような操作を定義できます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-105">WCF Data Services enables you to define such operations as methods on the data service.</span></span> <span data-ttu-id="53bc5-106">他のデータ サービス リソースと同様に、これらのサービス操作は URI によってアドレス指定できます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-106">Like other data service resources, these service operations are addressed by using URIs.</span></span> <span data-ttu-id="53bc5-107">サービス操作では、エンティティ型のコレクション、1 つのエンティティ型のインスタンス、およびプリミティブ型 (整数、文字列など) を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-107">A service operation can return collections of entity types, single entity type instances, and primitive types, such as integer and string.</span></span> <span data-ttu-id="53bc5-108">さらに、サービス操作では、`null` (Visual Basic の場合は `Nothing`) を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-108">A service operation can also return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="53bc5-109">WCF Data Services クライアント ライブラリを使用して、HTTP GET 要求をサポートするサービス操作にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-109">The WCF Data Services client library can be used to access service operations that support HTTP GET requests.</span></span> <span data-ttu-id="53bc5-110">この種のサービス操作は、<xref:System.ServiceModel.Web.WebGetAttribute> が適用されたメソッドとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-110">These kinds of service operations are defined as methods that have the <xref:System.ServiceModel.Web.WebGetAttribute> applied.</span></span> <span data-ttu-id="53bc5-111">詳細については、「[サービス操作](service-operations-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc5-111">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="53bc5-112">サービス操作は、OData を実装するデータ サービスによって返されるメタデータで公開されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-112">Service operations are exposed in the metadata returned by a data service that implements the OData.</span></span> <span data-ttu-id="53bc5-113">メタデータ内で、サービス操作は、`FunctionImport` 要素として表されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-113">In the metadata, service operations are represented as `FunctionImport` elements.</span></span> <span data-ttu-id="53bc5-114">厳密に型指定された <xref:System.Data.Services.Client.DataServiceContext> を生成するとき、この要素は "サービス参照の追加" と DataSvcUtil.exe ツールで無視されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-114">When generating the strongly typed <xref:System.Data.Services.Client.DataServiceContext>, the Add Service Reference and DataSvcUtil.exe tools ignore this element.</span></span> <span data-ttu-id="53bc5-115">このため、サービス操作を直接呼び出すために使用できるコンテキストにはメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-115">Because of this, you will not find a method on the context that can be used to call a service operation directly.</span></span> <span data-ttu-id="53bc5-116">ただし、次のいずれかの方法を使用して、WCF Data Services クライアントでサービス操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-116">However, you can still use the WCF Data Services client to call service operations in one of these two ways:</span></span>  
  
- <span data-ttu-id="53bc5-117"><xref:System.Data.Services.Client.DataServiceContext.Execute%2A> で <xref:System.Data.Services.Client.DataServiceContext> メソッドを呼び出し、サービス操作の URI をその他のパラメーターと共に指定します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-117">By calling the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method on the <xref:System.Data.Services.Client.DataServiceContext>, supplying the URI of the service operation, along with any parameters.</span></span> <span data-ttu-id="53bc5-118">このメソッドは、GET サービス操作の呼び出しに使用されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-118">This method is used to call any GET service operation.</span></span>  
  
- <span data-ttu-id="53bc5-119"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> の <xref:System.Data.Services.Client.DataServiceContext> メソッドを使用して、<xref:System.Data.Services.Client.DataServiceQuery%601> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-119">By using the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> method on the <xref:System.Data.Services.Client.DataServiceContext> to create a <xref:System.Data.Services.Client.DataServiceQuery%601> object.</span></span> <span data-ttu-id="53bc5-120"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を呼び出すとき、サービス操作の名前が `entitySetName` パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-120">When calling <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, the name of the service operation is supplied to the `entitySetName` parameter.</span></span> <span data-ttu-id="53bc5-121">このメソッドは、列挙されたときまたは <xref:System.Data.Services.Client.DataServiceQuery%601> メソッドが呼び出されたときにサービス操作を呼び出す <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-121">This method returns a <xref:System.Data.Services.Client.DataServiceQuery%601> object that calls the service operation when enumerated or when the <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> method is called.</span></span> <span data-ttu-id="53bc5-122">このメソッドは、コレクションを返す GET サービス操作の呼び出しに使用されます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-122">This method is used to call GET service operations that return a collection.</span></span> <span data-ttu-id="53bc5-123">1 つのパラメーターは、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-123">A single parameter can be supplied by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="53bc5-124">このメソッドによって返される <xref:System.Data.Services.Client.DataServiceQuery%601> オブジェクトは、クエリ オブジェクトのようにさらに構成できます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-124">The <xref:System.Data.Services.Client.DataServiceQuery%601> object returned by this method can be further composed against like any query object.</span></span> <span data-ttu-id="53bc5-125">詳細については、「[データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc5-125">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="considerations-for-calling-service-operations"></a><span data-ttu-id="53bc5-126">サービス操作の呼び出しに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="53bc5-126">Considerations for Calling Service Operations</span></span>  

 <span data-ttu-id="53bc5-127">WCF Data Services クライアントを使用してサービス操作を呼び出すときは、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="53bc5-127">The following considerations apply when using the WCF Data Services client to call service operations.</span></span>  
  
- <span data-ttu-id="53bc5-128">データ サービスに非同期にアクセスするときは、<xref:System.Data.Services.Client.DataServiceContext> の同等の非同期 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> メソッドまたは <xref:System.Data.Services.Client.DataServiceQuery%601> の <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc5-128">When accessing the data service asynchronously, you must use the equivalent asynchronous <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceContext> or the <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span>  
  
- <span data-ttu-id="53bc5-129">WCF Data Services クライアント ライブラリは、プリミティブ型のコレクションを返すサービス操作からの結果を具体化できません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-129">The WCF Data Services client library cannot materialize the results from a service operation that returns a collection of primitive types.</span></span>  
  
- <span data-ttu-id="53bc5-130">WCF Data Services クライアント ライブラリでは、POST サービス操作の呼び出しはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-130">The WCF Data Services client library does not support calling POST service operations.</span></span> <span data-ttu-id="53bc5-131">HTTP POST によって呼び出されるサービス操作は、<xref:System.ServiceModel.Web.WebInvokeAttribute> に `Method="POST"` パラメーターを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-131">Service operations that are called by an HTTP POST are defined by using the <xref:System.ServiceModel.Web.WebInvokeAttribute> with the `Method="POST"` parameter.</span></span> <span data-ttu-id="53bc5-132">HTTP POST 要求を使用してサービス操作を呼び出すには、代わりに <xref:System.Net.HttpWebRequest> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc5-132">To call a service operation by using an HTTP POST request, you must instead use an <xref:System.Net.HttpWebRequest>.</span></span>  
  
- <span data-ttu-id="53bc5-133"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して、エンティティまたはプリミティブ型の単一の結果を返す GET サービス操作または 1 つ以上の入力パラメーターを必要とする GET サービス操作を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-133">You cannot use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a GET service operation that returns a single result, of either entity or primitive type, or that requires more than one input parameter.</span></span> <span data-ttu-id="53bc5-134">代わりに <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc5-134">You must instead call the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method.</span></span>  
  
- <span data-ttu-id="53bc5-135">ツールによって生成される厳密に型指定された <xref:System.Data.Services.Client.DataServiceContext> 部分クラスで <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> メソッドまたは <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> メソッドを使用してサービス操作を呼び出す拡張メソッドを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="53bc5-135">Consider creating an extension method on the strongly typed <xref:System.Data.Services.Client.DataServiceContext> partial class, which is generated by the tools, that uses either the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> or the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method to call a service operation.</span></span> <span data-ttu-id="53bc5-136">これにより、コンテキストから直接サービス操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-136">This enables you to call service operations directly from the context.</span></span> <span data-ttu-id="53bc5-137">詳細については、ブログの投稿「[サービス操作および WCF Data Services クライアント](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc5-137">For more information, see the blog post [Service Operations and the WCF Data Services Client](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).</span></span>  
  
- <span data-ttu-id="53bc5-138"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用してサービス操作を呼び出す場合、クライアント ライブラリは、アンパサンド (&) などの予約文字のパーセント エンコードを実行し、文字列内の単一引用符をエスケープして、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> に入力された文字を自動的にエスケープします。</span><span class="sxs-lookup"><span data-stu-id="53bc5-138">When you use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a service operation, the client library automatically escapes characters supplied to the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> by performing percent-encoding of reserved characters, such as ampersand (&), and escaping of single-quotes in strings.</span></span> <span data-ttu-id="53bc5-139">ただし、いずれかの *Execute* メソッドを呼び出してサービス操作を呼び出す場合は、このユーザーが指定した任意の文字列値のエスケープを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc5-139">However, when you call one of the *Execute* methods to call a service operation, you must remember to perform this escaping of any user-supplied string values.</span></span> <span data-ttu-id="53bc5-140">URI 内の単一引用符は、単一引用符のペアとしてエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="53bc5-140">Single-quotes in URIs are escaped as pairs of single-quotes.</span></span>  
  
## <a name="examples-of-calling-service-operations"></a><span data-ttu-id="53bc5-141">サービス操作の呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="53bc5-141">Examples of Calling Service Operations</span></span>  

 <span data-ttu-id="53bc5-142">このセクションには、WCF Data Services クライアント ライブラリを使用してサービス操作を呼び出す方法を示す次の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-142">This section contains the following examples of how to call service operations by using the WCF Data Services client library:</span></span>  
  
- [<span data-ttu-id="53bc5-143">Execute&lt;T&gt; を呼び出してエンティティのコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-143">Calling Execute&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [<span data-ttu-id="53bc5-144">CreateQuery&lt;T&gt; を使用してエンティティのコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-144">Using CreateQuery&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [<span data-ttu-id="53bc5-145">Execute&lt;T&gt; を呼び出して 1 つのエンティティを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-145">Calling Execute&lt;T&gt; to Return a Single Entity</span></span>](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [<span data-ttu-id="53bc5-146">Execute&lt;T&gt; を呼び出してプリミティブ値のコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-146">Calling Execute&lt;T&gt; to Return a Collection of Primitive Values</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [<span data-ttu-id="53bc5-147">Execute&lt;T&gt; を呼び出して 1 つのプリミティブ値を返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-147">Calling Execute&lt;T&gt; to Return a Single Primitive Value</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [<span data-ttu-id="53bc5-148">データを返さないサービス操作を呼び出す</span><span class="sxs-lookup"><span data-stu-id="53bc5-148">Calling a Service Operation that Returns No Data</span></span>](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [<span data-ttu-id="53bc5-149">サービス操作を非同期に呼び出す</span><span class="sxs-lookup"><span data-stu-id="53bc5-149">Calling a Service Operation Asynchronously</span></span>](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>

### <a name="calling-executet-to-return-a-collection-of-entities"></a><span data-ttu-id="53bc5-150">Execute\<T> を呼び出してエンティティのコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-150">Calling Execute\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="53bc5-151">次の例では、文字列パラメーター `city` を受け取り、<xref:System.Linq.IQueryable%601> を返す、GetOrdersByCity という名前のサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-151">The following example calls a service operation named GetOrdersByCity, which takes a string parameter of `city` and returns an <xref:System.Linq.IQueryable%601>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 <span data-ttu-id="53bc5-152">この例では、サービス操作は、`Order` オブジェクトのコレクションを関連する `Order_Detail` オブジェクトと共に返します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-152">In this example, the service operation returns a collection of `Order` objects with related `Order_Detail` objects.</span></span>  
  
<a name="CreateQueryIQueryable"></a>

### <a name="using-createqueryt-to-return-a-collection-of-entities"></a><span data-ttu-id="53bc5-153">CreateQuery\<T> を使用してエンティティのコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-153">Using CreateQuery\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="53bc5-154">次の例では、<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して、同じ GetOrdersByCity サービス操作を呼び出すために使用される <xref:System.Data.Services.Client.DataServiceQuery%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-154">The following example uses the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to return a <xref:System.Data.Services.Client.DataServiceQuery%601> that is used to call the same GetOrdersByCity service operation:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 <span data-ttu-id="53bc5-155">この例では、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用してクエリにパラメーターを追加し、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して関連する Order_Details オブジェクトを結果に含めています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-155">In this example, the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method is used to add the parameter to the query, and the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is used to include related Order_Details objects in the results.</span></span>  
  
<a name="ExecuteSingleEntity"></a>

### <a name="calling-executet-to-return-a-single-entity"></a><span data-ttu-id="53bc5-156">Execute\<T> を呼び出して 1 つのエンティティを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-156">Calling Execute\<T> to Return a Single Entity</span></span>  

 <span data-ttu-id="53bc5-157">次の例では、単一の Order エンティティのみを返す、GetNewestOrder という名前のサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-157">The following example calls a service operation named GetNewestOrder that returns only a single Order entity:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 <span data-ttu-id="53bc5-158">この例では、<xref:System.Linq.Enumerable.FirstOrDefault%2A> メソッドを使用して、実行時に単一の Order エンティティのみを要求します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-158">In this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single Order entity on execution.</span></span>  
  
<a name="ExecutePrimitiveCollection"></a>

### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a><span data-ttu-id="53bc5-159">Execute\<T> を呼び出してプリミティブ値のコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-159">Calling Execute\<T> to Return a Collection of Primitive Values</span></span>  

 <span data-ttu-id="53bc5-160">次の例では、文字列値のコレクションを返すサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-160">The following example calls a service operation that returns a collection of string values:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>

### <a name="calling-executet-to-return-a-single-primitive-value"></a><span data-ttu-id="53bc5-161">Execute\<T> を呼び出して 1 つのプリミティブ値を返す</span><span class="sxs-lookup"><span data-stu-id="53bc5-161">Calling Execute\<T> to Return a Single Primitive Value</span></span>  

 <span data-ttu-id="53bc5-162">次の例では、単一の文字列値を返すサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-162">The following example calls a service operation that returns a single string value:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 <span data-ttu-id="53bc5-163">この例において、<xref:System.Linq.Enumerable.FirstOrDefault%2A> メソッドを使用して、実行時に単一の整数値のみを要求しています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-163">Again in this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single integer value on execution.</span></span>  
  
<a name="ExecuteVoid"></a>

### <a name="calling-a-service-operation-that-returns-no-data"></a><span data-ttu-id="53bc5-164">データを返さないサービス操作を呼び出す</span><span class="sxs-lookup"><span data-stu-id="53bc5-164">Calling a Service Operation that Returns No Data</span></span>  

 <span data-ttu-id="53bc5-165">次の例では、データを返さないサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53bc5-165">The following example calls a service operation that returns no data:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 <span data-ttu-id="53bc5-166">データが返されないため、実行の値は割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-166">Because not data is returned, the value of the execution is not assigned.</span></span> <span data-ttu-id="53bc5-167">要求が成功したことを示す唯一の印は、<xref:System.Data.Services.Client.DataServiceQueryException> が発生しないことです。</span><span class="sxs-lookup"><span data-stu-id="53bc5-167">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
<a name="ExecuteAsync"></a>

### <a name="calling-a-service-operation-asynchronously"></a><span data-ttu-id="53bc5-168">サービス操作を非同期に呼び出す</span><span class="sxs-lookup"><span data-stu-id="53bc5-168">Calling a Service Operation Asynchronously</span></span>  

 <span data-ttu-id="53bc5-169">次の例では、<xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> と <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> を呼び出してサービス操作を非同期に呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-169">The following example calls a service operation asynchronously by calling <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> and <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 <span data-ttu-id="53bc5-170">データが返されないため、実行によって返される値は割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="53bc5-170">Because no data is returned, the value returned by the execution is not assigned.</span></span> <span data-ttu-id="53bc5-171">要求が成功したことを示す唯一の印は、<xref:System.Data.Services.Client.DataServiceQueryException> が発生しないことです。</span><span class="sxs-lookup"><span data-stu-id="53bc5-171">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
 <span data-ttu-id="53bc5-172">次の例では、<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> を使用して同じサービス操作を非同期に呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="53bc5-172">The following example calls the same service operation asynchronously by using <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a><span data-ttu-id="53bc5-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="53bc5-173">See also</span></span>

- [<span data-ttu-id="53bc5-174">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="53bc5-174">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
