---
description: 詳細については、AJAX-Enabled ASP.NET Web サービスを WCF に移行する方法に関するページを参照してください。
title: '方法: AJAX 対応 ASP.NET Web サービスを WCF に移行する'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: fe79660f0ed8ef01a2607c94362d484cacc6a7b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793728"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="efcae-103">方法: AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="efcae-103">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>

<span data-ttu-id="efcae-104">このトピックでは、基本的な ASP.NET AJAX サービスを同等の AJAX 対応 Windows Communication Foundation (WCF) サービスに移行する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="efcae-104">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="efcae-105">ここでは、ASP.NET AJAX サービスの機能的に同等の WCF バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efcae-105">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="efcae-106">2つのサービスを並行して使用することも、WCF サービスを使用して ASP.NET AJAX サービスを置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="efcae-106">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="efcae-107">既存の ASP.NET AJAX サービスを WCF AJAX サービスに移行すると、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="efcae-107">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="efcae-108">最小限の追加構成で、AJAX サービスを SOAP サービスとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="efcae-108">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="efcae-109">トレースなどの WCF 機能を活用できます。</span><span class="sxs-lookup"><span data-stu-id="efcae-109">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="efcae-110">次の手順では、Visual Studio 2012 を使用していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="efcae-110">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="efcae-111">手順に続く例で、ここで説明する手順によって作成されるコードを示します。</span><span class="sxs-lookup"><span data-stu-id="efcae-111">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="efcae-112">AJAX 対応エンドポイントを使用して WCF サービスを公開する方法の詳細については、「 [方法: 構成を使用して ASP.NET AJAX エンドポイントを追加](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efcae-112">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="efcae-113">ASP.NET Web サービス アプリケーションを作成してテストする</span><span class="sxs-lookup"><span data-stu-id="efcae-113">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="efcae-114">Visual Studio 2012 を開きます。</span><span class="sxs-lookup"><span data-stu-id="efcae-114">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="efcae-115">[ **ファイル** ] メニューの [ **新規作成**]、[ **プロジェクト**]、[ **web**] の順に選択し、[ **ASP.NET web Service Application**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="efcae-115">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="efcae-116">プロジェクトに名前を指定し、 `ASPHello` [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efcae-116">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="efcae-117">Service1.asmx.cs ファイルで、`System.Web.Script.Services.ScriptService]` が含まれた行のコメントを解除し、このサービスに対して AJAX を有効にします。</span><span class="sxs-lookup"><span data-stu-id="efcae-117">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="efcae-118">[ **ビルド** ] メニューの [ **ソリューションのビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efcae-118">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="efcae-119">**[デバッグ]** メニューから **[デバッグなしで開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="efcae-119">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="efcae-120">生成された Web ページで、`HelloWorld` 操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="efcae-120">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="efcae-121">[テスト] ページの [ **起動** ] ボタンをクリックし `HelloWorld` ます。</span><span class="sxs-lookup"><span data-stu-id="efcae-121">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="efcae-122">次の XML 応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="efcae-122">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="efcae-123">この応答は、ASP.NET AJAX サービスが現在機能していること、およびこのサービスが現在 Service1.asmx/HelloWorld でエンドポイントを公開していることを確認するものです。このエンドポイントが HTTP POST 要求に応答し、XML を返します。</span><span class="sxs-lookup"><span data-stu-id="efcae-123">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="efcae-124">これで、WCF AJAX サービスを使用するようにこのサービスを変換する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="efcae-124">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="efcae-125">同等の WCF AJAX サービス アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="efcae-125">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="efcae-126">**Asphello** プロジェクトを右クリックし、[**追加**]、[**新しい項目**]、[ **AJAX 対応 WCF サービス**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="efcae-126">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="efcae-127">サービスに名前を指定し、 `WCFHello` [ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efcae-127">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="efcae-128">WCFHello.svc.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="efcae-128">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="efcae-129">Service1.asmx.cs から、次の操作の実装をコピーし `HelloWorld` ます。</span><span class="sxs-lookup"><span data-stu-id="efcae-129">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="efcae-130">次のコードの代わりに、コピーした操作の実装を WCFHello.svc.cs ファイルに貼り付け `HelloWorld` ます。</span><span class="sxs-lookup"><span data-stu-id="efcae-130">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="efcae-131">とし `Namespace` ての属性を指定し <xref:System.ServiceModel.ServiceContractAttribute> `WCFHello` ます。</span><span class="sxs-lookup"><span data-stu-id="efcae-131">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="efcae-132">を <xref:System.ServiceModel.Web.WebInvokeAttribute> 操作に追加 `HelloWorld` し、プロパティをに設定して <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> を返し <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ます。</span><span class="sxs-lookup"><span data-stu-id="efcae-132">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="efcae-133">この設定を行わない場合、既定の戻り値の型は <xref:System.ServiceModel.Web.WebMessageFormat.Json> です。</span><span class="sxs-lookup"><span data-stu-id="efcae-133">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="efcae-134">[ **ビルド** ] メニューの [ **ソリューションのビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="efcae-134">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="efcae-135">Wcfhello.svc ファイルを開き、[ **デバッグ** ] メニューの [ **デバッグなしで開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="efcae-135">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="efcae-136">サービスは `WCFHello.svc/HelloWorld` 、HTTP POST 要求に応答するでエンドポイントを公開するようになりました。</span><span class="sxs-lookup"><span data-stu-id="efcae-136">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="efcae-137">HTTP POST 要求をブラウザーからテストすることはできませんが、エンドポイントは次の XML を返します。</span><span class="sxs-lookup"><span data-stu-id="efcae-137">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="efcae-138">`WCFHello.svc/HelloWorld`と `Service1.aspx/HelloWorld` エンドポイントが機能的に同等になりました。</span><span class="sxs-lookup"><span data-stu-id="efcae-138">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="efcae-139">例</span><span class="sxs-lookup"><span data-stu-id="efcae-139">Example</span></span>

 <span data-ttu-id="efcae-140">このトピックで説明した手順によって作成されるコードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="efcae-140">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="efcae-141"><xref:System.Xml.XmlDocument> 型は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によってシリアル化できないため、<xref:System.Xml.Serialization.XmlSerializer> ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="efcae-141">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="efcae-142"><xref:System.Xml.Linq.XDocument> 型を使用するか、<xref:System.Xml.XmlDocument.DocumentElement%2A> をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="efcae-142">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="efcae-143">ASMX Web サービスを WCF サービスに対してサイドバイサイドでアップグレードおよび移行する場合は、2つの型をクライアントで同じ名前にマップしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="efcae-143">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="efcae-144">同じ名前が割り当てられていると、<xref:System.Web.Services.WebMethodAttribute> と <xref:System.ServiceModel.ServiceContractAttribute> で同じ型が使用されている場合に、シリアライザーで次のような例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="efcae-144">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="efcae-145">WCF サービスが先に追加された場合、ASMX Web サービスでメソッドを呼び出すと、で例外が発生 <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> します。これは、プロキシでの順序の wcf スタイル定義が優先されるためです。</span><span class="sxs-lookup"><span data-stu-id="efcae-145">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="efcae-146">ASMX Web サービスが先に追加されている場合、WCF サービスでメソッドを呼び出すと、で例外が発生 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> します。これは、プロキシでの順序の Web サービススタイル定義が優先されるためです。</span><span class="sxs-lookup"><span data-stu-id="efcae-146">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="efcae-147"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> の動作には大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="efcae-147">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="efcae-148">たとえば、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> はディクショナリをキーと値のペアの配列として表しますが、ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> はディクショナリを実際の JSON オブジェクトとして表します。</span><span class="sxs-lookup"><span data-stu-id="efcae-148">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="efcae-149">したがって、ASP.NET AJAX では、ディクショナリが次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="efcae-149">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="efcae-150">このディクショナリは、JSON オブジェクトでは次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="efcae-150">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="efcae-151"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では [{"Key":"one","Value":1},{"Key":"two","Value":2}] と表され、</span><span class="sxs-lookup"><span data-stu-id="efcae-151">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="efcae-152">ASP.NET AJAX による {"one": 1, "two": 2} <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="efcae-152">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="efcae-153"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、キーの種類が文字列ではないディクショナリを処理でき、<xref:System.Web.Script.Serialization.JavaScriptSerializer> はできません。この点で前者はより強力と言えます。</span><span class="sxs-lookup"><span data-stu-id="efcae-153">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="efcae-154">しかし、後者の方が JSON で使いやすいと言えます。</span><span class="sxs-lookup"><span data-stu-id="efcae-154">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="efcae-155">これらのシリアライザーの主な違いを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="efcae-155">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="efcae-156">相違点のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="efcae-156">Category of Differences</span></span>|<span data-ttu-id="efcae-157">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="efcae-157">DataContractJsonSerializer</span></span>|<span data-ttu-id="efcae-158">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="efcae-158">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="efcae-159">空きバッファー (新しい byte[0]) の <xref:System.Object> (または <xref:System.Uri>、あるいは他の一部のクラス) への逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="efcae-159">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="efcae-160">SerializationException</span><span class="sxs-lookup"><span data-stu-id="efcae-160">SerializationException</span></span>|<span data-ttu-id="efcae-161">null</span><span class="sxs-lookup"><span data-stu-id="efcae-161">null</span></span>|
|<span data-ttu-id="efcae-162"><xref:System.DBNull.Value> のシリアル化</span><span class="sxs-lookup"><span data-stu-id="efcae-162">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="efcae-163">{} (または {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="efcae-163">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="efcae-164">[Null]</span><span class="sxs-lookup"><span data-stu-id="efcae-164">Null</span></span>|
|<span data-ttu-id="efcae-165">[Serializable] 型のプライベート メンバーのシリアル化</span><span class="sxs-lookup"><span data-stu-id="efcae-165">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="efcae-166">できるか</span><span class="sxs-lookup"><span data-stu-id="efcae-166">serialized</span></span>|<span data-ttu-id="efcae-167">シリアル化できません</span><span class="sxs-lookup"><span data-stu-id="efcae-167">not serialized</span></span>|
|<span data-ttu-id="efcae-168"><xref:System.Runtime.Serialization.ISerializable> 型のパブリック プロパティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="efcae-168">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="efcae-169">シリアル化できません</span><span class="sxs-lookup"><span data-stu-id="efcae-169">not serialized</span></span>|<span data-ttu-id="efcae-170">できるか</span><span class="sxs-lookup"><span data-stu-id="efcae-170">serialized</span></span>|
|<span data-ttu-id="efcae-171">JSON の「拡張機能」</span><span class="sxs-lookup"><span data-stu-id="efcae-171">"Extensions" of JSON</span></span>|<span data-ttu-id="efcae-172">オブジェクト メンバー名で引用符を必要とする ({"a":"hello"}) JSON 仕様に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="efcae-172">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="efcae-173">引用符のないオブジェクト メンバー名 ({a:"hello"}) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="efcae-173">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="efcae-174"><xref:System.DateTime> 協定世界時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="efcae-174"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="efcae-175">" \\ /Date (/日付) \\ /" または "/ \\ 日付 \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) \\ \\ \\ の形式はサポートされていません。/)".</span><span class="sxs-lookup"><span data-stu-id="efcae-175">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="efcae-176">Format "/ \\ date (/日付) \\ /" および "/ \\ 日付 \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) \\ \\ \\ をサポートしています。/) "を DateTime 値として指定します。</span><span class="sxs-lookup"><span data-stu-id="efcae-176">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="efcae-177">ディクショナリの表現</span><span class="sxs-lookup"><span data-stu-id="efcae-177">Representation of dictionaries</span></span>|<span data-ttu-id="efcae-178">KeyValuePair の配列 \<K,V> 。文字列ではないキー型を処理します。</span><span class="sxs-lookup"><span data-stu-id="efcae-178">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="efcae-179">実際の JSON オブジェクトですが、文字列の種類のキーのみ処理します。</span><span class="sxs-lookup"><span data-stu-id="efcae-179">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="efcae-180">エスケープ文字</span><span class="sxs-lookup"><span data-stu-id="efcae-180">Escaped characters</span></span>|<span data-ttu-id="efcae-181">必ず、エスケープ文字であるスラッシュ (/) を付けます。"\n" などのエスケープされない無効な JSON 文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="efcae-181">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="efcae-182">DateTime 値には、エスケープ文字スラッシュ (/) を付けます。</span><span class="sxs-lookup"><span data-stu-id="efcae-182">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="efcae-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="efcae-183">See also</span></span>

- [<span data-ttu-id="efcae-184">方法: 構成を使用して ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="efcae-184">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
