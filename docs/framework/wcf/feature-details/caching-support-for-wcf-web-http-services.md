---
description: 詳細については、「WCF Web HTTP サービスのキャッシュサポート」を参照してください。
title: WCF WEB HTTP サービスのキャッシュ サポート
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: a1f7351566c06010ed70093a1cab3697ae0e9356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643489"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="04dab-103">WCF WEB HTTP サービスのキャッシュ サポート</span><span class="sxs-lookup"><span data-stu-id="04dab-103">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="04dab-104">WCF Web HTTP サービスの ASP.NET で既に提供されている宣言型キャッシュ機構を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="04dab-104">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="04dab-105">これにより、WCF Web HTTP サービス操作からの応答をキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="04dab-105">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="04dab-106">キャッシュ用に構成されているサービスに対してユーザーが HTTP GET を送信すると、ASP.NET は、キャッシュされた応答を送り返し、サービス メソッドは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="04dab-106">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="04dab-107">キャッシュの有効期限が切れると、ユーザーが次回に HTTP GET を送信したときに、サービス メソッドが呼び出され、応答が再度キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-107">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="04dab-108">ASP.NET キャッシュの詳細については、「 [ASP.NET キャッシュの概要](/previous-versions/aspnet/ms178597(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04dab-108">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="04dab-109">基本的な Web HTTP サービスのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="04dab-109">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="04dab-110">WEB HTTP サービスのキャッシュを有効にするに <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> は、サービス設定のをまたはに適用して、ASP.NET の互換性を最初に有効にする必要があり <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> ます。</span><span class="sxs-lookup"><span data-stu-id="04dab-110">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="04dab-111">.NET Framework 4 では、キャッシュプロファイル名を指定できるという新しい属性が導入され <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ています。</span><span class="sxs-lookup"><span data-stu-id="04dab-111">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="04dab-112">この属性は、サービス操作に適用されます。</span><span class="sxs-lookup"><span data-stu-id="04dab-112">This attribute is applied to a service operation.</span></span> <span data-ttu-id="04dab-113">次の例では、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> をサービスに適用して ASP.NET との互換性を有効にし、`GetCustomer` 操作をキャッシュできるように構成しています。</span><span class="sxs-lookup"><span data-stu-id="04dab-113">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="04dab-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 属性には、使用されるキャッシュ設定が含まれるキャッシュ プロファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="04dab-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="04dab-115">また、次の例に示すように Web.config ファイルで ASP.NET 互換モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="04dab-115">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="04dab-116">ASP.NET 互換性モードが有効にされていない場合は、<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> が使用されて、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-116">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="04dab-117"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> によって指定されたキャッシュ プロファイル名によって、Web.config 構成ファイルに追加されるキャッシュ プロファイルが特定されます。</span><span class="sxs-lookup"><span data-stu-id="04dab-117">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="04dab-118">キャッシュプロファイルは、 `outputCacheSetting` 次の構成例に示すように、<> 要素で定義されています。</span><span class="sxs-lookup"><span data-stu-id="04dab-118">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="04dab-119">これは、ASP.NET アプリケーションで使用できる構成要素と同じです。</span><span class="sxs-lookup"><span data-stu-id="04dab-119">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="04dab-120">ASP.NET cache プロファイルの詳細については、「」を参照してください <xref:System.Web.Configuration.OutputCacheProfile> 。</span><span class="sxs-lookup"><span data-stu-id="04dab-120">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="04dab-121">Web HTTP サービスの場合、キャッシュ プロファイルで最も重要な属性は `cacheDuration` と `varyByParam` です。</span><span class="sxs-lookup"><span data-stu-id="04dab-121">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="04dab-122">この 2 つの属性はどちらも必要です。</span><span class="sxs-lookup"><span data-stu-id="04dab-122">Both of these attributes are required.</span></span> <span data-ttu-id="04dab-123">`cacheDuration` は、応答がキャッシュに保持される時間 (秒数) を設定します。</span><span class="sxs-lookup"><span data-stu-id="04dab-123">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="04dab-124">`varyByParam` では、応答のキャッシュに使用されるクエリ文字列パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="04dab-124">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="04dab-125">異なるクエリ文字列パラメーターの値を使用する要求は、すべて個別にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-125">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="04dab-126">たとえば、最初の要求がに対して行われると、 `http://MyServer/MyHttpService/MyOperation?param=10` 同じ URI で行われる後続のすべての要求は、キャッシュされた応答を返します (キャッシュ期間が経過していない限り)。</span><span class="sxs-lookup"><span data-stu-id="04dab-126">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="04dab-127">クエリ文字列パラメーターの値が異なることを除いて同じである同様の要求に対する応答は、個別にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-127">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="04dab-128">このような個別のキャッシングを行わない場合は、`varyByParam` を "none" に設定します。</span><span class="sxs-lookup"><span data-stu-id="04dab-128">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="04dab-129">SQL キャッシュ依存関係</span><span class="sxs-lookup"><span data-stu-id="04dab-129">SQL Cache Dependency</span></span>  

  <span data-ttu-id="04dab-130">Web HTTP サービスの応答も、SQL キャッシュ依存関係と併せてキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="04dab-130">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="04dab-131">SQL データベースに格納されているデータに応じて WCF Web HTTP サービスが異なる場合は、サービスの応答をキャッシュして、キャッシュした応答を、SQL データベース テーブル内のデータの変更時に無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="04dab-131">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="04dab-132">この動作は、すべて Web.config ファイル内で構成します。</span><span class="sxs-lookup"><span data-stu-id="04dab-132">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="04dab-133">まず、<> 要素に接続文字列を定義し `connectionStrings` ます。</span><span class="sxs-lookup"><span data-stu-id="04dab-133">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="04dab-134">`caching` `system.web` 次に、次の構成例に示すように、<> 要素内の <> 要素内で SQL キャッシュの依存関係を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dab-134">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="04dab-135">ここでは、SQL キャッシュ依存関係を有効にし、ポーリング タイムを 1000 ミリ秒に設定しています。</span><span class="sxs-lookup"><span data-stu-id="04dab-135">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="04dab-136">ポーリング タイムが経過するたびに、データベース テーブルで更新の有無が確認されます。</span><span class="sxs-lookup"><span data-stu-id="04dab-136">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="04dab-137">変更が検出されると、キャッシュの内容が削除され、次にサービス操作が呼び出されたときに、新しい応答がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-137">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="04dab-138">`sqlCacheDependency` `databases` 次の例に示すように、<の> 要素内にデータベースを追加し、<> 要素内の接続文字列を参照します。</span><span class="sxs-lookup"><span data-stu-id="04dab-138">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="04dab-139">次 `caching` に、次の例に示すように、<> 要素内に出力キャッシュ設定を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dab-139">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="04dab-140">ここでは、キャッシュ期間が60秒に設定され、 `varyByParam` が none に設定されて `sqlDependency` います。また、は、コロンで区切られたデータベース名とテーブルのペアのセミコロン区切りのリストに設定されています。</span><span class="sxs-lookup"><span data-stu-id="04dab-140">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="04dab-141">`MyTable` のデータが変更されると、キャッシュされているサービス操作への応答が削除されます。この操作が呼び出されると、新しい応答が (サービス操作の呼び出しによって) 生成され、キャッシュされて、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="04dab-141">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04dab-142">ASP.NET が SQL database にアクセスするには、 [ASP.NET SQL Server 登録ツール](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dab-142">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="04dab-143">また、適切なユーザー アカウントに、データベースおよびテーブルへのアクセスを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dab-143">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="04dab-144">詳細については、「 [Web アプリケーションからの SQL Server へのアクセス](/previous-versions/aspnet/ht43wsex(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04dab-144">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="04dab-145">条件付きの HTTP GET ベースのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="04dab-145">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="04dab-146">Web HTTP シナリオでは、 [Http 仕様](https://www.w3.org/Protocols/rfc2616/rfc2616.html)で説明されているように、インテリジェントな http キャッシュを実装するために、条件付き http GET がサービスによって使用されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="04dab-146">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="04dab-147">これを行うには、サービスは HTTP 応答で ETag ヘッダーの値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dab-147">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="04dab-148">また、HTTP 要求の If-None-Match ヘッダーの値を確認して、指定されている ETag が現在の ETag と一致するかどうかを調べる必要もあります。</span><span class="sxs-lookup"><span data-stu-id="04dab-148">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="04dab-149">GET および HEAD 要求の場合、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> は ETag 値を取得し、この値と要求内の If-None-Match ヘッダーとを比較します。</span><span class="sxs-lookup"><span data-stu-id="04dab-149">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="04dab-150">ヘッダーが存在し、一致するものがある場合は、 <xref:System.ServiceModel.Web.WebFaultException> HTTP 状態コード 304 (変更なし) のがスローされ、etag ヘッダーが一致する etag と共に応答に追加されます。</span><span class="sxs-lookup"><span data-stu-id="04dab-150">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="04dab-151"><xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドのオーバーロードの 1 つは、最終更新日を取得し、これを、要求の If-Modified-Since ヘッダーと比較します。</span><span class="sxs-lookup"><span data-stu-id="04dab-151">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="04dab-152">ヘッダーが存在し、リソースが変更されていない場合は、HTTP ステータス コード 304 (変更なし) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="04dab-152">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="04dab-153">PUT、POST、および DELETE の各要求の場合、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> は、リソースの現在の ETag 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="04dab-153">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="04dab-154">現在の ETag 値が null の場合、メソッドは、If-match ヘッダーの値が "\*" であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="04dab-154">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="04dab-155">現在の ETag 値が既定値ではない場合、メソッドは、現在の ETag 値と要求の If-None- Match ヘッダーを比較します。</span><span class="sxs-lookup"><span data-stu-id="04dab-155">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="04dab-156">どちらの場合も、求められるヘッダーが要求内に存在しない、またはヘッダーの値がチェック条件を満たしていないと、メソッドは、HTTP ステータス コード 412 (必須条件に失敗しました) が設定された <xref:System.ServiceModel.Web.WebFaultException> をスローし、応答の ETag ヘッダーを現在の ETag 値に設定します。</span><span class="sxs-lookup"><span data-stu-id="04dab-156">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="04dab-157">`CheckConditional` メソッドも <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> メソッドも、応答ヘッダーに設定される ETag 値が、確実に HTTP 仕様に沿った有効な ETag になるようにします。</span><span class="sxs-lookup"><span data-stu-id="04dab-157">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="04dab-158">これには、ETag 値を囲む二重引用符がない場合に二重引用符を付ける処理や、二重引用符内の文字を適切にエスケープする処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="04dab-158">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="04dab-159">ETag の弱い比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="04dab-159">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="04dab-160">これらのメソッドを使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="04dab-160">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="04dab-161">セキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="04dab-161">Security Considerations</span></span>  

 <span data-ttu-id="04dab-162">承認が必要な要求の応答はキャッシュしないでください。応答がキャッシュから提供された場合は、承認が実行されません。</span><span class="sxs-lookup"><span data-stu-id="04dab-162">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="04dab-163">このような応答をキャッシュすると、重大なセキュリティの脆弱性が生じます。</span><span class="sxs-lookup"><span data-stu-id="04dab-163">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="04dab-164">通常、承認が必要な要求ではユーザー固有のデータが提供されるため、サーバー側でキャッシュしても利点はありません。</span><span class="sxs-lookup"><span data-stu-id="04dab-164">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="04dab-165">このような場合は、クライアント側でキャッシュするか、単にキャッシュをまったく行わない方が適切です。</span><span class="sxs-lookup"><span data-stu-id="04dab-165">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
