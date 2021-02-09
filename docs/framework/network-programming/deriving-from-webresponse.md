---
description: '詳細情報: WebResponse からの派生'
title: WebResponse からの派生
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 5e941ce055091c6034640733465020ff62ce3721
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747479"
---
# <a name="deriving-from-webresponse"></a><span data-ttu-id="b9f2d-103">WebResponse からの派生</span><span class="sxs-lookup"><span data-stu-id="b9f2d-103">Deriving from WebResponse</span></span>

<span data-ttu-id="b9f2d-104"><xref:System.Net.WebResponse> クラスは、.NET Framework プラグ可能なプロトコル モデルに適合するプロトコル固有の応答を作成するための基本メソッドとプロパティを提供する抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-104">The <xref:System.Net.WebResponse> class is an abstract base class that provides the basic methods and properties for creating a protocol-specific response that fits the .NET Framework pluggable protocol model.</span></span> <span data-ttu-id="b9f2d-105"><xref:System.Net.WebRequest> クラスを使用してリソースからデータを要求するアプリケーションは、**WebResponse** で応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-105">Applications that use the <xref:System.Net.WebRequest> class to request data from resources receive the responses in a **WebResponse**.</span></span> <span data-ttu-id="b9f2d-106">プロトコル固有の **WebResponse** の子孫は、**WebResponse** クラスの抽象メンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-106">Protocol-specific **WebResponse** descendants must implement the abstract members of the **WebResponse** class.</span></span>  
  
 <span data-ttu-id="b9f2d-107">関連付けられた **WebRequest** クラスは、**WebResponse** の子孫を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-107">The associated **WebRequest** class must create **WebResponse** descendants.</span></span> <span data-ttu-id="b9f2d-108">たとえば、<xref:System.Net.HttpWebResponse> インスタンスは、<xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> または <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType> の呼び出しの結果としてのみ作成されます。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-108">For example, <xref:System.Net.HttpWebResponse> instances are created only as the result of calling <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> or <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b9f2d-109">各 **WebResponse** には、リソースへの要求の結果が含まれており、再利用されることを意図していません。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-109">Each **WebResponse** contains the result of a request to a resource and is not intended to be reused.</span></span>  
  
## <a name="contentlength-property"></a><span data-ttu-id="b9f2d-110">ContentLength プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9f2d-110">ContentLength Property</span></span>  

 <span data-ttu-id="b9f2d-111"><xref:System.Net.WebResponse.ContentLength%2A> プロパティは、<xref:System.Net.WebResponse.GetResponseStream%2A> メソッドによって返されるストリームから利用可能なデータのバイト数を示します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-111">The <xref:System.Net.WebResponse.ContentLength%2A> property indicates the number of bytes of data that are available from the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A> method.</span></span> <span data-ttu-id="b9f2d-112">**ContentLength** プロパティは、サーバーによって返されるヘッダーのバイト数またはメタデータ情報を示しません。要求されたリソース自体のデータのバイト数のみを示します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-112">The **ContentLength** property does not indicate the number of bytes of header or metadata information returned by the server; it indicates only the number of bytes of data in the requested resource itself.</span></span>  
  
## <a name="contenttype-property"></a><span data-ttu-id="b9f2d-113">ContentType プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9f2d-113">ContentType Property</span></span>  

 <span data-ttu-id="b9f2d-114"><xref:System.Net.WebResponse.ContentType%2A> プロパティは、サーバーによって送信中のコンテンツ タイプを識別するためにクライアントに送信するようにプロトコルで求められる特別な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-114">The <xref:System.Net.WebResponse.ContentType%2A> property provides any special information that your protocol requires you to send to the client to identify the type of content being sent by the server.</span></span> <span data-ttu-id="b9f2d-115">通常、これは返される任意のデータの MIME コンテンツ タイプです。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-115">Typically this is the MIME content type of any data returned.</span></span>  
  
## <a name="headers-property"></a><span data-ttu-id="b9f2d-116">Headers プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9f2d-116">Headers Property</span></span>  

 <span data-ttu-id="b9f2d-117"><xref:System.Net.WebResponse.Headers%2A> プロパティには、応答に関連付けられているメタデータの名前/値ペアの任意のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-117">The <xref:System.Net.WebResponse.Headers%2A> property contains an arbitrary collection of name/value pairs of metadata associated with the response.</span></span> <span data-ttu-id="b9f2d-118">名前/値のペアとして表すことができるプロトコルで必要なすべてのメタデータは、**Headers** プロパティに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-118">Any metadata needed by the protocol that can be expressed as a name/value pair can be included in the **Headers** property.</span></span>  
  
 <span data-ttu-id="b9f2d-119">ヘッダー メタデータを使用するために **Headers** プロパティを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-119">You are not required to use the **Headers** property to use header metadata.</span></span> <span data-ttu-id="b9f2d-120">プロトコル固有のメタデータをプロパティとして公開することができます。たとえば、<xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> プロパティは、**Last-Modified** HTTP ヘッダーを公開します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-120">Protocol-specific metadata can be exposed as properties; for example, the <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> property exposes the **Last-Modified** HTTP header.</span></span> <span data-ttu-id="b9f2d-121">ヘッダー メタデータをプロパティとして公開する場合、**Headers** プロパティを使用して同じプロパティが設定されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-121">When you expose header metadata as a property, you should not allow the same property to be set using the **Headers** property.</span></span>  
  
## <a name="responseuri-property"></a><span data-ttu-id="b9f2d-122">ResponseUri プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9f2d-122">ResponseUri Property</span></span>  

 <span data-ttu-id="b9f2d-123"><xref:System.Net.WebResponse.ResponseUri%2A> プロパティには、実際に応答を提供したリソースの URI が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-123">The <xref:System.Net.WebResponse.ResponseUri%2A> property contains the URI of the resource that actually provided the response.</span></span> <span data-ttu-id="b9f2d-124">リダイレクトをサポートしないプロトコルの場合、**ResponseUri** は応答を作成した **WebRequest** の <xref:System.Net.WebRequest.RequestUri%2A> プロパティと同じになります。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-124">For protocols that do not support redirection, **ResponseUri** will be the same as the <xref:System.Net.WebRequest.RequestUri%2A> property of the **WebRequest** that created the response.</span></span> <span data-ttu-id="b9f2d-125">プロトコルが要求のリダイレクトをサポートしている場合は、**ResponseUri** に応答の URI が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-125">If the protocol supports redirecting the request, **ResponseUri** will contain the URI of the response.</span></span>  
  
## <a name="close-method"></a><span data-ttu-id="b9f2d-126">Close メソッド</span><span class="sxs-lookup"><span data-stu-id="b9f2d-126">Close Method</span></span>  

 <span data-ttu-id="b9f2d-127"><xref:System.Net.WebResponse.Close%2A> メソッドは、要求と応答によって作成されたすべての接続を閉じ、応答で使用されているリソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-127">The <xref:System.Net.WebResponse.Close%2A> method closes any connections made by the request and response and cleans up resources used by the response.</span></span> <span data-ttu-id="b9f2d-128">**Close** メソッドは、応答で使用されたすべてのストリーム インスタンスを閉じますが、応答ストリームが <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドへの呼び出しにより以前に閉じられた場合は、例外をスローしません。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-128">The **Close** method closes any stream instances used by the response, but it does not throw an exception if the response stream was previously closed by a call to the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="getresponsestream-method"></a><span data-ttu-id="b9f2d-129">GetResponseStream メソッド</span><span class="sxs-lookup"><span data-stu-id="b9f2d-129">GetResponseStream Method</span></span>  

 <span data-ttu-id="b9f2d-130"><xref:System.Net.WebResponse.GetResponseStream%2A> メソッドは要求されたリソースからの応答を含むストリームを返します。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-130">The <xref:System.Net.WebResponse.GetResponseStream%2A> method returns a stream containing the response from the requested resource.</span></span> <span data-ttu-id="b9f2d-131">応答ストリームには、リソースによって返されるデータのみが含まれています。応答に含まれるヘッダーやメタデータをすべて応答から除去し、プロトコル固有のプロパティまたは **Headers** プロパティ使用して、アプリケーションに公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-131">The response stream contains only the data returned by the resource; any header or metadata included in the response should be stripped from the response and exposed to the application through protocol-specific properties or the **Headers** property.</span></span>  
  
 <span data-ttu-id="b9f2d-132">**GetResponseStream** メソッドによって返されるストリーム インスタンスは、アプリケーションによって所有され、**WebResponse** を閉じずに閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-132">The stream instance returned by the **GetResponseStream** method is owned by the application and can be closed without closing the **WebResponse**.</span></span> <span data-ttu-id="b9f2d-133">規則により、**WebResponse.Close** メソッドの呼び出しも **GetResponse** で返されるストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b9f2d-133">By convention, calling the **WebResponse.Close** method also closes the stream returned by **GetResponse**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f2d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9f2d-134">See also</span></span>

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [<span data-ttu-id="b9f2d-135">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="b9f2d-135">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
- [<span data-ttu-id="b9f2d-136">WebRequest からの派生</span><span class="sxs-lookup"><span data-stu-id="b9f2d-136">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
