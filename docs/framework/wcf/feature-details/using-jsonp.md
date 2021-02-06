---
description: 詳細については、JSONP の使用に関するページをご覧ください。
title: JSONP の使用
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: f4d21670cf468328b8579fa8a9cf2c2e06f09337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632192"
---
# <a name="using-jsonp"></a><span data-ttu-id="b3a25-103">JSONP の使用</span><span class="sxs-lookup"><span data-stu-id="b3a25-103">Using JSONP</span></span>

<span data-ttu-id="b3a25-104">JSONP (JSON with Padding) は、Web ブラウザーでクロスサイト スクリプトの利用を可能にするためのメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="b3a25-104">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="b3a25-105">JSONP は、現在読み込まれているドキュメントを取得したサイトとは異なるサイトから、スクリプトを読み込むための Web ブラウザーの機能を軸に設計されています。</span><span class="sxs-lookup"><span data-stu-id="b3a25-105">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="b3a25-106">このメカニズムは、次の例に示すように、JSON ペイロードにユーザー定義のコールバック関数の名前を埋め込むことで機能します。</span><span class="sxs-lookup"><span data-stu-id="b3a25-106">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="b3a25-107">上記の例では、JSON ペイロード `{"a" = \\"b\\"}` が、関数呼び出し `callback` にラップされています。</span><span class="sxs-lookup"><span data-stu-id="b3a25-107">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="b3a25-108">コールバック関数は、現在の Web ページで定義済みである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3a25-108">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="b3a25-109">JSONP 応答のコンテンツタイプは `application/javascript` です。</span><span class="sxs-lookup"><span data-stu-id="b3a25-109">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="b3a25-110">JSONP は自動的には有効化されません。</span><span class="sxs-lookup"><span data-stu-id="b3a25-110">JSONP is not automatically enabled.</span></span> <span data-ttu-id="b3a25-111">有効にするには、次の例のように、HTTP の標準エンドポイントのいずれか (`javascriptCallbackEnabled` または `true`) で、<xref:System.ServiceModel.Description.WebHttpEndpoint> 属性を <xref:System.ServiceModel.Description.WebScriptEndpoint> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3a25-111">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="b3a25-112">コールバック関数名は、次の URL に示すように、callback というクエリ変数で指定できます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-112">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="b3a25-113">このサービスを呼び出すと、次のような応答が送信されます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-113">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="b3a25-114">コールバック関数名は、次の例のように、サービス クラスに <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> を適用して指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-114">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="b3a25-115">上に示したサービスでは、要求は次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="b3a25-115">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="b3a25-116">このサービスを呼び出すと、次のような応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-116">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="b3a25-117">HTTP 状態コード</span><span class="sxs-lookup"><span data-stu-id="b3a25-117">HTTP Status Codes</span></span>

<span data-ttu-id="b3a25-118">HTTP 状態コードが 200 以外の JSONP 応答には、次の例のように、HTTP 状態コードの数値表現が 2 つ目のパラメーターとして付加されます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-118">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="b3a25-119">確認</span><span class="sxs-lookup"><span data-stu-id="b3a25-119">Validations</span></span>

<span data-ttu-id="b3a25-120">JSONP が有効な場合、以下の検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-120">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="b3a25-121">`javascriptCallback` が有効になっており、要求にコールバック クエリ文字列のパラメーターが含まれ、応答形式が JSON に設定されている場合は、WCF インフラストラクチャから例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-121">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="b3a25-122">要求にコールバック クエリ文字列のパラメーターが含まれているが、操作が HTTP GET ではない場合は、コールバック パラメーターが無視されます。</span><span class="sxs-lookup"><span data-stu-id="b3a25-122">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="b3a25-123">コールバック名が `null` または空の文字列の場合は、応答の形式が JSONP に設定されません。</span><span class="sxs-lookup"><span data-stu-id="b3a25-123">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3a25-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3a25-124">See also</span></span>

- [<span data-ttu-id="b3a25-125">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="b3a25-125">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
