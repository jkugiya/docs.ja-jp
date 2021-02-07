---
description: '詳細情報: WCF Web HTTP プログラミングモデルの概要'
title: WCF Web HTTP プログラミング モデルの概要
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 3359b0018458256cb3436e0fb631ee5fa438521e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732879"
---
# <a name="wcf-web-http-programming-model-overview"></a><span data-ttu-id="974be-103">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="974be-103">WCF Web HTTP Programming Model Overview</span></span>

<span data-ttu-id="974be-104">Windows Communication Foundation (WCF) WEB HTTP プログラミングモデルは、WCF を使用した WEB HTTP サービスの構築に必要な基本的な要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="974be-104">The Windows Communication Foundation (WCF) WEB HTTP programming model provides the basic elements required to build WEB HTTP services with WCF.</span></span> <span data-ttu-id="974be-105">WCF WEB HTTP サービスは、Web ブラウザーなどの幅広いクライアントからアクセスできるように設計されており、次のような固有の要件があります。</span><span class="sxs-lookup"><span data-stu-id="974be-105">WCF WEB HTTP services are designed to be accessed by the widest range of possible clients, including Web browsers and have the following unique requirements:</span></span>  
  
- <span data-ttu-id="974be-106">Uri **と uri の処理** Uri は、WEB HTTP サービスの設計で中心的な役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="974be-106">**URIs and URI Processing** URIs play a central role in the design of WEB HTTP services.</span></span> <span data-ttu-id="974be-107">WCF WEB HTTP プログラミングモデルでは、クラスとクラスを使用して、 <xref:System.UriTemplate> <xref:System.UriTemplateTable> URI 処理機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="974be-107">The WCF WEB HTTP programming model uses the <xref:System.UriTemplate> and <xref:System.UriTemplateTable> classes to provide URI processing capabilities.</span></span>  
  
- <span data-ttu-id="974be-108">**GET 操作と POST 操作のサポート** WEB HTTP サービスは、データ変更やリモート呼び出しのためのさまざまな呼び出し動詞に加えて、データ取得のために GET 動詞を使用します。</span><span class="sxs-lookup"><span data-stu-id="974be-108">**Support for GET and POST operations** WEB HTTP services make use of the GET verb for data retrieval, in addition to various invoke verbs for data modification and remote invocation.</span></span> <span data-ttu-id="974be-109">WCF WEB HTTP プログラミングモデルでは、およびを使用して、 <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> サービス操作を GET と、PUT、POST、DELETE などの他の HTTP 動詞の両方に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="974be-109">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> to associate service operations with both GET and other HTTP verbs like PUT, POST, and DELETE.</span></span>  
  
- <span data-ttu-id="974be-110">**複数のデータ形式** Web スタイルサービスは、SOAP メッセージに加えて、さまざまな種類のデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="974be-110">**Multiple data formats** Web-style services process many kinds of data in addition to SOAP messages.</span></span> <span data-ttu-id="974be-111">WCF WEB HTTP プログラミングモデルは、およびを使用して、 <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> XML ドキュメント、JSON データオブジェクト、バイナリコンテンツのストリーム (画像、ビデオファイル、プレーンテキストなど) を含むさまざまなデータ形式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="974be-111">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> to support many different data formats including XML documents, JSON data object, and streams of binary content such as images, video files, or plain text.</span></span>  
  
 <span data-ttu-id="974be-112">WCF WEB HTTP プログラミングモデルは、WEB HTTP サービス、AJAX および JSON サービス、配信 (ATOM/RSS) フィードを含む Web スタイルのシナリオに対応するために、WCF の範囲を拡張します。</span><span class="sxs-lookup"><span data-stu-id="974be-112">The WCF WEB HTTP programming model extends the reach of WCF to cover Web-style scenarios that include WEB HTTP services, AJAX and JSON services, and Syndication (ATOM/RSS) feeds.</span></span> <span data-ttu-id="974be-113">AJAX および JSON サービスの詳細については、「 [ajax の統合と json のサポート](ajax-integration-and-json-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-113">For more information about AJAX and JSON services, see [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span> <span data-ttu-id="974be-114">配信の詳細については、「 [WCF 配信の概要](wcf-syndication-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-114">For more information about Syndication, see [WCF Syndication Overview](wcf-syndication-overview.md).</span></span>  
  
 <span data-ttu-id="974be-115">WEB HTTP サービスから返されるデータの種類に追加の制限はありません。</span><span class="sxs-lookup"><span data-stu-id="974be-115">There are no extra restrictions on the types of data that can be returned from a WEB HTTP service.</span></span> <span data-ttu-id="974be-116">WEB HTTP サービス操作からは任意のシリアル化可能な型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="974be-116">Any serializable type can be returned from an WEB HTTP service operation.</span></span> <span data-ttu-id="974be-117">WEB HTTP サービス操作は Web ブラウザーによって呼び出すことができるため、URL に指定できるデータ型に制限があります。</span><span class="sxs-lookup"><span data-stu-id="974be-117">Because WEB HTTP service operations can be invoke by a web browser there is a limitation on what data types can be specified in a URL.</span></span> <span data-ttu-id="974be-118">既定でサポートされている型の詳細については、以下の「 **UriTemplate クエリ文字列パラメーターと url** 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-118">For more information on what types are supported by default see the **UriTemplate Query String Parameters and URLs** section below.</span></span> <span data-ttu-id="974be-119">既定の動作は、URL で指定されたパラメーターから実際のパラメーター型への変換方法を指定する独自の T:System.ServiceModel.Dispatcher.QueryStringConverter 実装を提供することで変更できます。</span><span class="sxs-lookup"><span data-stu-id="974be-119">The default behavior can be changed by providing your own T:System.ServiceModel.Dispatcher.QueryStringConverter implementation which specifies how to convert the parameters specified in a URL to the actual parameter type.</span></span> <span data-ttu-id="974be-120">詳細については、<xref:System.ServiceModel.Dispatcher.QueryStringConverter> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-120">For more information, see <xref:System.ServiceModel.Dispatcher.QueryStringConverter></span></span>  
  
> [!CAUTION]
> <span data-ttu-id="974be-121">WCF WEB HTTP プログラミングモデルで記述されたサービスは、SOAP メッセージを使用しません。</span><span class="sxs-lookup"><span data-stu-id="974be-121">Services written with the WCF WEB HTTP programming model do not use SOAP messages.</span></span> <span data-ttu-id="974be-122">SOAP は使用されないため、WCF によって提供されるセキュリティ機能は使用できません。</span><span class="sxs-lookup"><span data-stu-id="974be-122">Because SOAP is not used, the security features provided by WCF cannot be used.</span></span> <span data-ttu-id="974be-123">ただし、HTTPS でサービスをホストすることによってトランスポート ベースのセキュリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="974be-123">You can, however use transport-based security by hosting your service with HTTPS.</span></span> <span data-ttu-id="974be-124">WCF セキュリティの詳細については、「[セキュリティの概要](security-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-124">For more information about WCF security, see [Security Overview](security-overview.md)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="974be-125">IIS の WebDAV 拡張をインストールすると、WebDAV 拡張がすべての PUT 要求を処理しようとしたときに Web HTTP サービスが HTTP 405 エラーを返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="974be-125">Installing the WebDAV extension for IIS can cause Web HTTP services to return an HTTP 405 error as the WebDAV extension attempts to handle all PUT requests.</span></span> <span data-ttu-id="974be-126">この問題を解決するには、WebDAV 拡張をアンインストールするか、Web サイトの WebDAV 拡張を無効にします。</span><span class="sxs-lookup"><span data-stu-id="974be-126">To work around this issue you can uninstall the WebDAV extension or disable the WebDAV extension for your web site.</span></span> <span data-ttu-id="974be-127">詳細については、「 [IIS と WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-127">For more information, see [IIS and WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span></span>  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a><span data-ttu-id="974be-128">UriTemplate および UriTemplateTable を使用した URI 処理</span><span class="sxs-lookup"><span data-stu-id="974be-128">URI Processing with UriTemplate and UriTemplateTable</span></span>  

 <span data-ttu-id="974be-129">URI テンプレートには、構造的に類似する URI の大規模なセットを効率的に表現するための構文が備わっています。</span><span class="sxs-lookup"><span data-stu-id="974be-129">URI templates provide an efficient syntax for expressing large sets of structurally similar URIs.</span></span> <span data-ttu-id="974be-130">たとえば、テンプレート a/{segment}/c は、中間のセグメントの値を問わず、"a" で始まり "c" で終了する 3 つのセグメントから成る URI のセットを表しています。</span><span class="sxs-lookup"><span data-stu-id="974be-130">For example, the following template expresses the set of all three-segment URIs that begin with "a" and end with "c" without regard to the value of the intermediate segment: a/{segment}/c</span></span>  
  
 <span data-ttu-id="974be-131">このテンプレートによって、次のような URI が記述されます。</span><span class="sxs-lookup"><span data-stu-id="974be-131">This template describes URIs like the following:</span></span>  
  
- <span data-ttu-id="974be-132">a/x/c</span><span class="sxs-lookup"><span data-stu-id="974be-132">a/x/c</span></span>  
  
- <span data-ttu-id="974be-133">a/y/c</span><span class="sxs-lookup"><span data-stu-id="974be-133">a/y/c</span></span>  
  
- <span data-ttu-id="974be-134">a/z/c</span><span class="sxs-lookup"><span data-stu-id="974be-134">a/z/c</span></span>  
  
- <span data-ttu-id="974be-135">その他にもあります。</span><span class="sxs-lookup"><span data-stu-id="974be-135">and so on.</span></span>  
  
 <span data-ttu-id="974be-136">このテンプレートでは、中かっこによる表記 ("{segment}") で、リテラル値ではなく、変数のセグメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="974be-136">In this template, the curly brace notation ("{segment}") indicates a variable segment instead of a literal value.</span></span>  
  
 <span data-ttu-id="974be-137">.NET Framework は <xref:System.UriTemplate> という URI テンプレートでの作業に使用できる新しい API を提供します。</span><span class="sxs-lookup"><span data-stu-id="974be-137">.NET Framework provides an API for working with URI templates called <xref:System.UriTemplate>.</span></span> <span data-ttu-id="974be-138">`UriTemplates` を使用すると、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="974be-138">`UriTemplates` allow you to do the following:</span></span>  
  
- <span data-ttu-id="974be-139">パラメーターのセットを使用してメソッドの1つを呼び出すと `Bind` 、テンプレートに一致する *完全に終了* した URI を生成できます。</span><span class="sxs-lookup"><span data-stu-id="974be-139">You can call one of the `Bind` methods with a set of parameters to produce a *fully-closed URI* that matches the template.</span></span> <span data-ttu-id="974be-140">つまり、URI テンプレート内の変数がすべて、実際の値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="974be-140">This means all variables within the URI template are replaced with actual values.</span></span>  
  
- <span data-ttu-id="974be-141">候補の URI を使用して `Match`() を呼び出すことができます。このメソッドは、テンプレートを使用して候補の URI を構成要素に分解し、テンプレート内の変数に従って分類される URI のさまざまな要素を収めたディクショナリを返します。</span><span class="sxs-lookup"><span data-stu-id="974be-141">You can call `Match`() with a candidate URI, which uses a template to break up a candidate URI into its constituent parts and returns a dictionary that contains the different parts of the URI labeled according to the variables in the template.</span></span>  
  
- <span data-ttu-id="974be-142">`Bind`() と `Match`() は逆のもので、`Match`( `Bind`( x ) ) を呼び出し、最初と同じ環境に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="974be-142">`Bind`() and `Match`() are inverses so that you can call `Match`( `Bind`( x ) ) and come back with the same environment you started with.</span></span>  
  
 <span data-ttu-id="974be-143">包含されたテンプレートを個別に扱うことができるデータ構造内の一連の <xref:System.UriTemplate> オブジェクトを追跡することが必要になる場合がよくあります (特に、URI に基づいて要求をサービス操作にディスパッチすることが必要なサーバー上)。</span><span class="sxs-lookup"><span data-stu-id="974be-143">There are many times (especially on the server, where dispatching a request to a service operation based on the URI is necessary) that you want to keep track of a set of <xref:System.UriTemplate> objects in a data structure that can independently address each of the contained templates.</span></span> <span data-ttu-id="974be-144"><xref:System.UriTemplateTable> は、URI テンプレートのセットを表し、テンプレート セットと候補の URI が与えられると、最適の組み合わせを選択します。</span><span class="sxs-lookup"><span data-stu-id="974be-144"><xref:System.UriTemplateTable> represents a set of URI templates and selects the best match given a set of templates and a candidate URI.</span></span> <span data-ttu-id="974be-145">これは、必要に応じて使用できるように、特定のネットワークスタック (WCF を含む) には関連していません。</span><span class="sxs-lookup"><span data-stu-id="974be-145">This is not affiliated with any particular networking stack (WCF included) so you can use it wherever necessary.</span></span>  
  
 <span data-ttu-id="974be-146">WCF サービス モデルは、<xref:System.UriTemplate> および <xref:System.UriTemplateTable> を使用して、<xref:System.UriTemplate> によって記述された URI セットにサービス操作を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="974be-146">The WCF Service Model makes use of <xref:System.UriTemplate> and <xref:System.UriTemplateTable> to associate service operations with a set of URIs described by a <xref:System.UriTemplate>.</span></span> <span data-ttu-id="974be-147">サービス操作は、<xref:System.UriTemplate> または <xref:System.ServiceModel.Web.WebGetAttribute> によって <xref:System.ServiceModel.Web.WebInvokeAttribute> に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="974be-147">A service operation is associated with a <xref:System.UriTemplate>, using either the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="974be-148">およびの詳細について <xref:System.UriTemplate> <xref:System.UriTemplateTable> は、「 [UriTemplate と UriTemplateTable](uritemplate-and-uritemplatetable.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-148">For more information about <xref:System.UriTemplate> and <xref:System.UriTemplateTable>, see [UriTemplate and UriTemplateTable](uritemplate-and-uritemplatetable.md)</span></span>  
  
## <a name="webget-and-webinvoke-attributes"></a><span data-ttu-id="974be-149">WebGet および WebInvoke 属性</span><span class="sxs-lookup"><span data-stu-id="974be-149">WebGet and WebInvoke Attributes</span></span>  

 <span data-ttu-id="974be-150">WCF WEB HTTP サービスは、さまざまな呼び出し動詞 (HTTP POST、PUT、DELETE など) に加えて、取得動詞 (HTTP GET など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="974be-150">WCF WEB HTTP services make use of retrieval verbs (for example HTTP GET) in addition to various invoke verbs (for example HTTP POST, PUT, and DELETE).</span></span> <span data-ttu-id="974be-151">WCF WEB HTTP プログラミングモデルでは、サービス開発者はとを使用して、サービス操作に関連付けられた URI テンプレートと動詞の両方を制御でき <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="974be-151">The WCF WEB HTTP programming model allows service developers to control the both the URI template and verb associated with their service operations with the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="974be-152"><xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用すると、個々の操作を URI と、それらの URI に関連付けられている HTTP メソッドにバインドする方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="974be-152">The <xref:System.ServiceModel.Web.WebGetAttribute> and the <xref:System.ServiceModel.Web.WebInvokeAttribute> allow you to control how individual operations get bound to URIs and the HTTP methods associated with those URIs.</span></span> <span data-ttu-id="974be-153">たとえば、次のコードでは、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を追加します。</span><span class="sxs-lookup"><span data-stu-id="974be-153">For example, adding <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> in the following code.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 <span data-ttu-id="974be-154">上記のコードを使用すると、次の HTTP 要求を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="974be-154">The preceding code allows you to make the following HTTP requests.</span></span>  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <span data-ttu-id="974be-155"><xref:System.ServiceModel.Web.WebInvokeAttribute> は、既定で POST に設定されていますが、他の動詞にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="974be-155"><xref:System.ServiceModel.Web.WebInvokeAttribute> defaults to POST but you can use it for other verbs too.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 <span data-ttu-id="974be-156">Wcf WEB HTTP プログラミングモデルを使用する WCF サービスの完全なサンプルについては、「[方法: 基本的な Wcf WEB Http サービスを作成](how-to-create-a-basic-wcf-web-http-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-156">To see a complete sample of a WCF service that uses the WCF WEB HTTP programming model, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md)</span></span>  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a><span data-ttu-id="974be-157">UriTemplate クエリ文字列パラメーターと URL</span><span class="sxs-lookup"><span data-stu-id="974be-157">UriTemplate Query String Parameters and URLs</span></span>  

 <span data-ttu-id="974be-158">サービス操作に関連付けられた URL を入力することによって、Web ブラウザーから Web スタイルのサービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="974be-158">Web-style services can be called from a Web browser by typing a URL that is associated with a service operation.</span></span> <span data-ttu-id="974be-159">このようなサービス操作は、文字列形式で指定する必要があるクエリ文字列パラメーターを URL 内で受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="974be-159">These service operations may take query string parameters that must be specified in a string form within the URL.</span></span> <span data-ttu-id="974be-160">次の表に、URL 内で渡すことができる型と、使用される形式を示します。</span><span class="sxs-lookup"><span data-stu-id="974be-160">The following table shows the types that can be passed within a URL and the format used.</span></span>  
  
|<span data-ttu-id="974be-161">種類</span><span class="sxs-lookup"><span data-stu-id="974be-161">Type</span></span>|<span data-ttu-id="974be-162">書式</span><span class="sxs-lookup"><span data-stu-id="974be-162">Format</span></span>|  
|----------|------------|  
|<xref:System.Byte>|<span data-ttu-id="974be-163">0 から 255</span><span class="sxs-lookup"><span data-stu-id="974be-163">0 - 255</span></span>|  
|<xref:System.SByte>|<span data-ttu-id="974be-164">-128 - 127</span><span class="sxs-lookup"><span data-stu-id="974be-164">-128 - 127</span></span>|  
|<xref:System.Int16>|<span data-ttu-id="974be-165">-32768 - 32767</span><span class="sxs-lookup"><span data-stu-id="974be-165">-32768 - 32767</span></span>|  
|<xref:System.Int32>|<span data-ttu-id="974be-166">-2,147,483,648 - 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="974be-166">-2,147,483,648 - 2,147,483,647</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="974be-167">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="974be-167">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="974be-168">0 - 65535</span><span class="sxs-lookup"><span data-stu-id="974be-168">0 - 65535</span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="974be-169">0 - 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="974be-169">0 - 4,294,967,295</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="974be-170">0 - 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="974be-170">0 - 18,446,744,073,709,551,615</span></span>|  
|<xref:System.Single>|<span data-ttu-id="974be-171">-3.402823e38 - 3.402823e38 (指数表記は要求されない)</span><span class="sxs-lookup"><span data-stu-id="974be-171">-3.402823e38 - 3.402823e38 (exponent notation is not required)</span></span>|  
|<xref:System.Double>|<span data-ttu-id="974be-172">-1.79769313486232e308 - 1.79769313486232e308 (指数表記は要求されない)</span><span class="sxs-lookup"><span data-stu-id="974be-172">-1.79769313486232e308 - 1.79769313486232e308 (exponent notation is not required)</span></span>|  
|<xref:System.Char>|<span data-ttu-id="974be-173">任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="974be-173">Any single character</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="974be-174">標準表記による任意の小数 (指数なし)</span><span class="sxs-lookup"><span data-stu-id="974be-174">Any decimal in standard notation (no exponent)</span></span>|  
|<xref:System.Boolean>|<span data-ttu-id="974be-175">True または False (大文字と小文字は区別されません)</span><span class="sxs-lookup"><span data-stu-id="974be-175">True or False (case insensitive)</span></span>|  
|<xref:System.String>|<span data-ttu-id="974be-176">任意の文字列 (null 文字列はサポートされず、エスケープは行われない)</span><span class="sxs-lookup"><span data-stu-id="974be-176">Any string (null string is not supported and no escaping is done)</span></span>|  
|<xref:System.DateTime>|<span data-ttu-id="974be-177">MM/DD/YYYY</span><span class="sxs-lookup"><span data-stu-id="974be-177">MM/DD/YYYY</span></span><br /><br /> <span data-ttu-id="974be-178">MM/DD/YYYY HH: MM: SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="974be-178">MM/DD/YYYY HH:MM:SS [AM&#124;PM]</span></span><br /><br /> <span data-ttu-id="974be-179">月 日 年</span><span class="sxs-lookup"><span data-stu-id="974be-179">Month Day Year</span></span><br /><br /> <span data-ttu-id="974be-180">Month Day Year HH: MM: SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="974be-180">Month Day Year HH:MM:SS [AM&#124;PM]</span></span>|  
|<xref:System.TimeSpan>|<span data-ttu-id="974be-181">DD.HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="974be-181">DD.HH:MM:SS</span></span><br /><br /> <span data-ttu-id="974be-182">DD = 日、HH = 時、MM = 分、SS = 秒</span><span class="sxs-lookup"><span data-stu-id="974be-182">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<xref:System.Guid>|<span data-ttu-id="974be-183">GUID。たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="974be-183">A GUID, for example:</span></span><br /><br /> <span data-ttu-id="974be-184">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span><span class="sxs-lookup"><span data-stu-id="974be-184">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span></span>|  
|<xref:System.DateTimeOffset>|<span data-ttu-id="974be-185">MM/DD/YYYY HH:MM:SS MM:SS</span><span class="sxs-lookup"><span data-stu-id="974be-185">MM/DD/YYYY HH:MM:SS MM:SS</span></span><br /><br /> <span data-ttu-id="974be-186">DD = 日、HH = 時、MM = 分、SS = 秒</span><span class="sxs-lookup"><span data-stu-id="974be-186">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<span data-ttu-id="974be-187">列挙型</span><span class="sxs-lookup"><span data-stu-id="974be-187">Enumerations</span></span>|<span data-ttu-id="974be-188">列挙値。たとえば、次のコードのように列挙体を定義します。</span><span class="sxs-lookup"><span data-stu-id="974be-188">The enumeration value for example, which defines the enumeration as shown in the following code.</span></span><br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> <span data-ttu-id="974be-189">クエリ文字列に、任意の列挙値 (またはそれぞれに対応する integer 値) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="974be-189">Any of the individual enumeration values (or their corresponding integer values) may be specified in the query string.</span></span>|  
|<span data-ttu-id="974be-190">型と文字列表現を双方向に変換できる `TypeConverterAttribute` を持つ型。</span><span class="sxs-lookup"><span data-stu-id="974be-190">Types that have a `TypeConverterAttribute` that can convert the type to and from a string representation.</span></span>|<span data-ttu-id="974be-191">型コンバーターによって異なります。</span><span class="sxs-lookup"><span data-stu-id="974be-191">Depends on the Type Converter.</span></span>|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a><span data-ttu-id="974be-192">形式と WCF WEB HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="974be-192">Formats and the WCF WEB HTTP Programming Model</span></span>  

 <span data-ttu-id="974be-193">WCF WEB HTTP プログラミングモデルには、さまざまなデータ形式を使用するための新機能があります。</span><span class="sxs-lookup"><span data-stu-id="974be-193">The WCF WEB HTTP programming model has new features to work with many different data formats.</span></span> <span data-ttu-id="974be-194"><xref:System.ServiceModel.WebHttpBinding> は、バインディング層で次のさまざまな種類のデータを読み書きできます。</span><span class="sxs-lookup"><span data-stu-id="974be-194">At the binding layer, the <xref:System.ServiceModel.WebHttpBinding> can read and write the following different kinds of data:</span></span>  
  
- <span data-ttu-id="974be-195">XML</span><span class="sxs-lookup"><span data-stu-id="974be-195">XML</span></span>  
  
- <span data-ttu-id="974be-196">JSON</span><span class="sxs-lookup"><span data-stu-id="974be-196">JSON</span></span>  
  
- <span data-ttu-id="974be-197">不透明なバイナリ ストリーム</span><span class="sxs-lookup"><span data-stu-id="974be-197">Opaque binary streams</span></span>  
  
 <span data-ttu-id="974be-198">つまり、WCF WEB HTTP プログラミングモデルではあらゆる種類のデータを処理できますが、に対してプログラミングすることができ <xref:System.IO.Stream> ます。</span><span class="sxs-lookup"><span data-stu-id="974be-198">This means the WCF WEB HTTP programming model can handle any type of data but, you may be programming against <xref:System.IO.Stream>.</span></span>  
  
 <span data-ttu-id="974be-199">.NET Framework 3.5 では、JSON データ (AJAX) と配信フィード (ATOM と RSS を含む) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="974be-199">.NET Framework 3.5 provides support for JSON data (AJAX) as well as Syndication feeds (including ATOM and RSS).</span></span> <span data-ttu-id="974be-200">これらの機能の詳細については、「 [Wcf WEB HTTP 書式設定](wcf-web-http-formatting.md)」、「 [Wcf 配信の概要](wcf-syndication-overview.md)」、および「 [AJAX の統合と JSON のサポート](ajax-integration-and-json-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-200">For more information about these features, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md), [WCF Syndication Overview](wcf-syndication-overview.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span>  
  
## <a name="wcf-web-http-programming-model-and-security"></a><span data-ttu-id="974be-201">WCF WEB HTTP プログラミング モデルとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="974be-201">WCF WEB HTTP Programming Model and Security</span></span>  

<span data-ttu-id="974be-202">WCF WEB HTTP プログラミングモデルでは WS-\* プロトコルがサポートされていないため、WCF WEB HTTP サービスをセキュリティで保護する唯一の方法は、SSL を使用して HTTPS 経由でサービスを公開することです。</span><span class="sxs-lookup"><span data-stu-id="974be-202">Because the WCF WEB HTTP programming model does not support the WS-\* protocols, the only way to secure a WCF WEB HTTP service is to expose the service over HTTPS using SSL.</span></span> <span data-ttu-id="974be-203">IIS 7.0 での SSL の設定の詳細については、「 [iis で ssl を実装する方法](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="974be-203">For more information about setting up SSL with IIS 7.0, see [How to implement SSL in IIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).</span></span>
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a><span data-ttu-id="974be-204">WCF WEB HTTP プログラミング モデルのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="974be-204">Troubleshooting the WCF WEB HTTP Programming Model</span></span>  

 <span data-ttu-id="974be-205"><xref:System.ServiceModel.Channels.ChannelFactoryBase%601> を使用してチャネルを作成するために WCF WEB HTTP サービスを呼び出すと、異なる <xref:System.ServiceModel.Description.WebHttpBehavior> が <xref:System.ServiceModel.EndpointAddress> に渡されるとしても、<xref:System.ServiceModel.EndpointAddress> は構成ファイルに設定されている <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="974be-205">When calling WCF WEB HTTP services using a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> to create a channel, the <xref:System.ServiceModel.Description.WebHttpBehavior> uses the <xref:System.ServiceModel.EndpointAddress> set in the configuration file even if a different <xref:System.ServiceModel.EndpointAddress> is passed to the <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974be-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="974be-206">See also</span></span>

- [<span data-ttu-id="974be-207">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="974be-207">WCF Syndication</span></span>](wcf-syndication.md)
- [<span data-ttu-id="974be-208">WCF Web HTTP プログラミング オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="974be-208">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="974be-209">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="974be-209">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
