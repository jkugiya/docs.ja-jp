---
description: '詳細情報: <httpListener> 要素 (ネットワーク設定)'
title: <httpListener> 要素 (ネットワーク設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 18c139ad7767370ecd3a4116e352b7614914d199
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652862"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="83f2b-103">\<httpListener> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="83f2b-103">\<httpListener> Element (Network Settings)</span></span>

<span data-ttu-id="83f2b-104">クラスによって使用されるパラメーターをカスタマイズ <xref:System.Net.HttpListener> します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-104">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="83f2b-105">構文</span><span class="sxs-lookup"><span data-stu-id="83f2b-105">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="83f2b-106">Type</span><span class="sxs-lookup"><span data-stu-id="83f2b-106">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83f2b-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="83f2b-107">Attributes and Elements</span></span>  

 <span data-ttu-id="83f2b-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83f2b-109">属性</span><span class="sxs-lookup"><span data-stu-id="83f2b-109">Attributes</span></span>  
  
|<span data-ttu-id="83f2b-110">属性</span><span class="sxs-lookup"><span data-stu-id="83f2b-110">Attribute</span></span>|<span data-ttu-id="83f2b-111">説明</span><span class="sxs-lookup"><span data-stu-id="83f2b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83f2b-112">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="83f2b-112">unescapeRequestUrl</span></span>|<span data-ttu-id="83f2b-113">インスタンスが、 <xref:System.Net.HttpListener> 変換後の uri ではなく、未加工のエスケープされていない uri を使用するかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="83f2b-113">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83f2b-114">子要素</span><span class="sxs-lookup"><span data-stu-id="83f2b-114">Child Elements</span></span>  

 <span data-ttu-id="83f2b-115">なし。</span><span class="sxs-lookup"><span data-stu-id="83f2b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83f2b-116">親要素</span><span class="sxs-lookup"><span data-stu-id="83f2b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="83f2b-117">**要素**</span><span class="sxs-lookup"><span data-stu-id="83f2b-117">**Element**</span></span>|<span data-ttu-id="83f2b-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="83f2b-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83f2b-119">設定</span><span class="sxs-lookup"><span data-stu-id="83f2b-119">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="83f2b-120"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-120">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f2b-121">解説</span><span class="sxs-lookup"><span data-stu-id="83f2b-121">Remarks</span></span>  

 <span data-ttu-id="83f2b-122">**UnescapeRequestUrl** 属性は、が変換された uri では <xref:System.Net.HttpListener> なく、生のエスケープされていない uri を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-122">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="83f2b-123">インスタンスは、 <xref:System.Net.HttpListener> サービスを介して要求を受け取ると、 `http.sys` によって提供される URI 文字列のインスタンスを作成 `http.sys` し、プロパティとして公開し <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-123">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="83f2b-124">サービスは、 `http.sys` 次の2つの要求 URI 文字列を公開します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-124">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="83f2b-125">未加工の URI</span><span class="sxs-lookup"><span data-stu-id="83f2b-125">Raw URI</span></span>  
  
- <span data-ttu-id="83f2b-126">変換された URI</span><span class="sxs-lookup"><span data-stu-id="83f2b-126">Converted URI</span></span>  
  
 <span data-ttu-id="83f2b-127">未加工 URI は、 <xref:System.Uri?displayProperty=nameWithType> HTTP 要求の要求行で指定されるです。</span><span class="sxs-lookup"><span data-stu-id="83f2b-127">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="83f2b-128">前述の要求に対してによって提供される未加工の URI `http.sys` は、"/path/" です。</span><span class="sxs-lookup"><span data-stu-id="83f2b-128">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="83f2b-129">これは、ネットワーク経由で送信された HTTP 動詞に続く文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-129">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="83f2b-130">サービスは、 `http.sys` HTTP 要求行に指定された uri とホストヘッダーを使用して、要求で提供される情報から変換された uri を作成し、要求の転送先となる配信元サーバーを決定します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-130">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="83f2b-131">これは、要求の情報を一連の登録済み URI プレフィックスと比較することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-131">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="83f2b-132">HTTP Server SDK のドキュメントでは、この変換された URI を HTTP_COOKED_URL 構造として参照します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-132">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="83f2b-133">要求を登録済みの URI プレフィックスと比較できるようにするには、要求の正規化を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="83f2b-133">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="83f2b-134">上記のサンプルの場合、変換後の URI は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="83f2b-134">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="83f2b-135">サービスは、 `http.sys` <xref:System.Uri.Host%2A?displayProperty=nameWithType> 要求行にプロパティ値と文字列を結合して、変換された URI を作成します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-135">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="83f2b-136">さらに、 `http.sys` クラスは <xref:System.Uri?displayProperty=nameWithType> 次のことも行います。</span><span class="sxs-lookup"><span data-stu-id="83f2b-136">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="83f2b-137">パーセントでエンコードされたすべての値をエスケープ解除します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-137">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="83f2b-138">パーセントでエンコードされた非 ASCII 文字を UTF-16 文字表現に変換します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-138">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="83f2b-139">UTF-8 および ANSI/DBCS 文字は、Unicode 文字 (% uXXXX 形式を使用した Unicode エンコード) でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83f2b-139">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="83f2b-140">パスの圧縮など、その他の正規化手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-140">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="83f2b-141">パーセントでエンコードされた値に使用されるエンコーディングに関する情報が要求に含まれていないため、パーセントでエンコードされた値を解析するだけで、正しいエンコーディングを判断できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="83f2b-141">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="83f2b-142">このため `http.sys` 、プロセスを変更するには、次の2つのレジストリキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-142">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="83f2b-143">レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="83f2b-143">Registry Key</span></span>|<span data-ttu-id="83f2b-144">既定値</span><span class="sxs-lookup"><span data-stu-id="83f2b-144">Default Value</span></span>|<span data-ttu-id="83f2b-145">説明</span><span class="sxs-lookup"><span data-stu-id="83f2b-145">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="83f2b-146">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="83f2b-146">EnableNonUTF8</span></span>|<span data-ttu-id="83f2b-147">1</span><span class="sxs-lookup"><span data-stu-id="83f2b-147">1</span></span>|<span data-ttu-id="83f2b-148">ゼロの場合、は `http.sys` utf-8 でエンコードされた url のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-148">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="83f2b-149">0以外の場合、 `http.sys` は、要求で ANSI エンコードまたは DBCS でエンコードされた url も受け入れます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-149">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="83f2b-150">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="83f2b-150">FavorUTF8</span></span>|<span data-ttu-id="83f2b-151">1</span><span class="sxs-lookup"><span data-stu-id="83f2b-151">1</span></span>|<span data-ttu-id="83f2b-152">0以外の場合、は `http.sys` 常に utf-8 として URL をデコードしようとします。変換に失敗し、EnableNonUTF8 が0以外の場合、Http.sys は ANSI または DBCS としてデコードしようとします。</span><span class="sxs-lookup"><span data-stu-id="83f2b-152">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="83f2b-153">ゼロ (および EnableNonUTF8 が0以外) の場合、は `http.sys` ANSI または DBCS としてデコードしようとします。成功しなかった場合は、utf-8 変換を試行します。</span><span class="sxs-lookup"><span data-stu-id="83f2b-153">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="83f2b-154">は、要求を受信すると、変換された <xref:System.Net.HttpListener> URI をから `http.sys` プロパティへの入力として使用し <xref:System.Net.HttpListenerRequest.Url%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-154">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="83f2b-155">Uri の文字と数字以外の文字をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83f2b-155">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="83f2b-156">例として、次の URI があります。これは、顧客番号 "1/3812" の顧客情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-156">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="83f2b-157">Uri (% 2F) のパーセントでエンコードされたスラッシュに注意してください。</span><span class="sxs-lookup"><span data-stu-id="83f2b-157">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="83f2b-158">この場合は、スラッシュ文字がパス区切り記号ではなく、データを表すために必要です。</span><span class="sxs-lookup"><span data-stu-id="83f2b-158">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="83f2b-159">文字列を Uri コンストラクターに渡すと、次の URI になります。</span><span class="sxs-lookup"><span data-stu-id="83f2b-159">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="83f2b-160">パスをセグメントに分割すると、次の要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-160">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="83f2b-161">これは、要求の送信者の意図ではありません。</span><span class="sxs-lookup"><span data-stu-id="83f2b-161">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="83f2b-162">**UnescapeRequestUrl** 属性が **false** に設定されている場合、が要求を受信すると、から変換された uri ではなく、 <xref:System.Net.HttpListener> 未加工の uri が `http.sys` プロパティへの入力として使用され <xref:System.Net.HttpListenerRequest.Url%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-162">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="83f2b-163">**UnescapeRequestUrl** 属性の既定値は **true** です。</span><span class="sxs-lookup"><span data-stu-id="83f2b-163">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="83f2b-164">プロパティは、 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> 適用可能な構成ファイルから **unescapeRequestUrl** 属性の現在の値を取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="83f2b-164">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f2b-165">例</span><span class="sxs-lookup"><span data-stu-id="83f2b-165">Example</span></span>  

 <span data-ttu-id="83f2b-166">次の例は、変換され <xref:System.Net.HttpListener> た uri ではなく、未加工の uri を使用するように要求を受け取ったときに、プロパティへの入力としてクラスを構成する方法を示して `http.sys` <xref:System.Net.HttpListenerRequest.Url%2A> います。</span><span class="sxs-lookup"><span data-stu-id="83f2b-166">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="83f2b-167">要素情報</span><span class="sxs-lookup"><span data-stu-id="83f2b-167">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="83f2b-168">名前空間</span><span class="sxs-lookup"><span data-stu-id="83f2b-168">Namespace</span></span>|<span data-ttu-id="83f2b-169">System.Net</span><span class="sxs-lookup"><span data-stu-id="83f2b-169">System.Net</span></span>|  
|<span data-ttu-id="83f2b-170">スキーマ名</span><span class="sxs-lookup"><span data-stu-id="83f2b-170">Schema Name</span></span>||  
|<span data-ttu-id="83f2b-171">検証ファイル</span><span class="sxs-lookup"><span data-stu-id="83f2b-171">Validation File</span></span>||  
|<span data-ttu-id="83f2b-172">空にすることができます</span><span class="sxs-lookup"><span data-stu-id="83f2b-172">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="83f2b-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="83f2b-173">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="83f2b-174">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="83f2b-174">Network Settings Schema</span></span>](index.md)
