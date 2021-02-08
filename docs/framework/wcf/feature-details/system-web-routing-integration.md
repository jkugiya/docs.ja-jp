---
description: 詳細については、「System.web. Routing Integration」を参照してください。
title: System.Web.Routing 統合
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 8f396d5a3cad30f5cc67cb0cf44fad76a0bb54c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793338"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="2ee4a-103">System.Web.Routing 統合</span><span class="sxs-lookup"><span data-stu-id="2ee4a-103">System.Web.Routing Integration</span></span>

<span data-ttu-id="2ee4a-104">インターネットインフォメーションサービス (IIS) で Windows Communication Foundation (WCF) サービスをホストする場合は、.svc ファイルを仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-104">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="2ee4a-105">この .svc ファイルは、使用するサービス ホスト ファクトリと、サービスを実装するクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-105">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="2ee4a-106">サービスに要求を行うときは、URI に .svc ファイルを指定します。たとえば、のように指定します。 `http://contoso.com/EmployeeServce.svc`</span><span class="sxs-lookup"><span data-stu-id="2ee4a-106">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="2ee4a-107">REST サービスを記述するプログラマにとっては、この種類の URI は最適とは言えません。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-107">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="2ee4a-108">REST サービス用の URI は、特定のリソースを指定しており、拡張子がないのが普通です。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-108">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="2ee4a-109"><xref:System.Web.Routing>統合機能を使用すると、拡張されていない uri に応答する WCF REST サービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-109">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="2ee4a-110">ルーティングの詳細については、「 [ASP.NET routing](/previous-versions/aspnet/cc668201(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-110">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="2ee4a-111">System.Web.Routing 統合の使用</span><span class="sxs-lookup"><span data-stu-id="2ee4a-111">Using System.Web.Routing Integration</span></span>  

 <span data-ttu-id="2ee4a-112"><xref:System.Web.Routing> 統合機能を使用するには、<xref:System.ServiceModel.Activation.ServiceRoute> クラスを使用して 1 つ以上のルートを作成し、Global.asax ファイルでそれらを <xref:System.Web.Routing.RouteTable> に追加します。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-112">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="2ee4a-113">これらのルートは、サービスが応答する相対 URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-113">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="2ee4a-114">次の例は、その方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-114">The following example shows how to do this.</span></span>  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 <span data-ttu-id="2ee4a-115">これは、Customers で始まる相対 URI が指定されたすべての要求を `Service` サービスにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-115">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="2ee4a-116">Web.config ファイルでは、次の例に示すように、`System.Web.Routing.UrlRoutingModule` モジュールを追加し、`runAllManagedModulesForAllRequests` 属性を `true` に設定し、`UrlRoutingHandler` ハンドラーを `<system.webServer>` 要素に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-116">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="2ee4a-117">これで、ルーティングに必要なモジュールとハンドラーが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-117">This loads a module and handler required for routing.</span></span> <span data-ttu-id="2ee4a-118">詳細については、[ルーティング](routing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-118">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="2ee4a-119">また、次の例に示すように、`aspNetCompatibilityEnabled` 要素で `true` 属性を `<serviceHostingEnvironment>` に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-119">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="2ee4a-120">次の例に示すように、このサービスを実装するクラスでは、ASP.NET 互換要件を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ee4a-120">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ee4a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ee4a-121">See also</span></span>

- [<span data-ttu-id="2ee4a-122">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="2ee4a-122">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="2ee4a-123">[ASP.NET ルーティング](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2ee4a-123">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
