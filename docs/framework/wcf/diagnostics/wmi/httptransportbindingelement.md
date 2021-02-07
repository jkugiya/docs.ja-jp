---
description: 詳細については、「HttpTransportBindingElement」を参照してください。
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 6c516dd7124d52828145787d55421d12031c2d36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757372"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="03f19-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="03f19-103">HttpTransportBindingElement</span></span>

<span data-ttu-id="03f19-104">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="03f19-104">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03f19-105">構文</span><span class="sxs-lookup"><span data-stu-id="03f19-105">Syntax</span></span>  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="03f19-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="03f19-106">Methods</span></span>  

 <span data-ttu-id="03f19-107">HttpTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="03f19-107">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="03f19-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="03f19-108">Properties</span></span>  

 <span data-ttu-id="03f19-109">HttpTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="03f19-109">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="03f19-110">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="03f19-110">AllowCookies</span></span>  

 <span data-ttu-id="03f19-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="03f19-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="03f19-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-113">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="03f19-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="03f19-114">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="03f19-114">AuthenticationScheme</span></span>  

 <span data-ttu-id="03f19-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-115">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-117">HTTP リスナーにより処理されているクライアント要求の認証に使用する認証方式です。</span><span class="sxs-lookup"><span data-stu-id="03f19-117">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="03f19-118">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="03f19-118">BypassProxyOnLocal</span></span>  

 <span data-ttu-id="03f19-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="03f19-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="03f19-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-121">プロキシをローカル アドレスで無視するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="03f19-121">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="03f19-122">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="03f19-122">HostNameComparisonMode</span></span>  

 <span data-ttu-id="03f19-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-123">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-125">URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="03f19-125">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="03f19-126">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="03f19-126">KeepAliveEnabled</span></span>  

 <span data-ttu-id="03f19-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="03f19-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="03f19-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-129">有効な場合は、HTTP 接続がアクティビティ レベルとは無関係に維持されます。</span><span class="sxs-lookup"><span data-stu-id="03f19-129">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="03f19-130">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="03f19-130">MaxBufferSize</span></span>  

 <span data-ttu-id="03f19-131">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="03f19-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="03f19-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-133">バッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="03f19-133">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="03f19-134">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="03f19-134">ProxyAddress</span></span>  

 <span data-ttu-id="03f19-135">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-135">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-137">HTTP 要求に使用するプロキシのアドレスを格納する URI です。</span><span class="sxs-lookup"><span data-stu-id="03f19-137">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="03f19-138">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="03f19-138">ProxyAuthenticationScheme</span></span>  

 <span data-ttu-id="03f19-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-139">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-141">HTTP プロキシにより処理されているクライアント要求の認証に使用する認証方式です。</span><span class="sxs-lookup"><span data-stu-id="03f19-141">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="03f19-142">Realm</span><span class="sxs-lookup"><span data-stu-id="03f19-142">Realm</span></span>  

 <span data-ttu-id="03f19-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-143">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-145">認証領域。</span><span class="sxs-lookup"><span data-stu-id="03f19-145">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="03f19-146">TransferMode</span><span class="sxs-lookup"><span data-stu-id="03f19-146">TransferMode</span></span>  

 <span data-ttu-id="03f19-147">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="03f19-147">Data type: string</span></span>  
  
 <span data-ttu-id="03f19-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-149">メッセージが要求や応答をバッファーするか、ストリーミングするかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="03f19-149">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="03f19-150">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="03f19-150">UnsafeConnectionNtlmAuthentication</span></span>  

 <span data-ttu-id="03f19-151">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="03f19-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="03f19-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-153">サーバー上で安全ではない接続共有を有効にするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="03f19-153">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="03f19-154">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="03f19-154">UseDefaultWebProxy</span></span>  

 <span data-ttu-id="03f19-155">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="03f19-155">Data type: boolean</span></span>  
  
 <span data-ttu-id="03f19-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="03f19-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03f19-157">ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="03f19-157">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03f19-158">要件</span><span class="sxs-lookup"><span data-stu-id="03f19-158">Requirements</span></span>  
  
|<span data-ttu-id="03f19-159">MOF</span><span class="sxs-lookup"><span data-stu-id="03f19-159">MOF</span></span>|<span data-ttu-id="03f19-160">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="03f19-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="03f19-161">名前空間</span><span class="sxs-lookup"><span data-stu-id="03f19-161">Namespace</span></span>|<span data-ttu-id="03f19-162">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="03f19-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03f19-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="03f19-163">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
