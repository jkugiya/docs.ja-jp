---
description: '詳細情報: @ServiceHost'
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: d16fda68bdc753121f02f6332dabedf236fac257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750313"
---
# <a name="servicehost"></a><span data-ttu-id="2e9fd-102">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="2e9fd-102">\@ServiceHost</span></span>

<span data-ttu-id="2e9fd-103">サービス ホストの生成に使用されるファクトリを、ホストされるサービスと、.svc ファイルで提供されるホスティング コードのアクセスとコンパイルに必要なその他のプログラミング部分に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-103">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e9fd-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e9fd-104">Syntax</span></span>

```aspx-csharp
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="2e9fd-105">属性</span><span class="sxs-lookup"><span data-stu-id="2e9fd-105">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="2e9fd-106">サービス</span><span class="sxs-lookup"><span data-stu-id="2e9fd-106">Service</span></span>

<span data-ttu-id="2e9fd-107">ホストされるサービスの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-107">The CLR type name of the service hosted.</span></span> <span data-ttu-id="2e9fd-108">これは、1 つ以上のサービス コンタクトを実装する型の修飾名にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-108">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="2e9fd-109">ファクトリ</span><span class="sxs-lookup"><span data-stu-id="2e9fd-109">Factory</span></span>

<span data-ttu-id="2e9fd-110">サービス ホストのインスタンス化に使用されるサービス ホスト ファクトリの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-110">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="2e9fd-111">この属性は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-111">This attribute is optional.</span></span> <span data-ttu-id="2e9fd-112">未指定の場合は、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す既定の <xref:System.ServiceModel.ServiceHost> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-112">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="2e9fd-113">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2e9fd-113">Debug</span></span>

<span data-ttu-id="2e9fd-114">デバッグシンボルを使用して Windows Communication Foundation (WCF) サービスをコンパイルする必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-114">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="2e9fd-115">`true` デバッグシンボルを使用して WCF サービスをコンパイルする必要がある場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-115">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="2e9fd-116">言語</span><span class="sxs-lookup"><span data-stu-id="2e9fd-116">Language</span></span>

<span data-ttu-id="2e9fd-117">ファイル (.svc) 内のすべてのインライン コードをコンパイルするときに使用する言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-117">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="2e9fd-118">値は任意のを表すことができます。、、およびを含む、.NET でサポートされている言語 `C#` `VB` `JS` 。それぞれ C#、Visual Basic、JScript .net を参照します。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-118">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="2e9fd-119">この属性は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-119">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="2e9fd-120">分離コード</span><span class="sxs-lookup"><span data-stu-id="2e9fd-120">CodeBehind</span></span>

<span data-ttu-id="2e9fd-121">Xml web サービスを実装するクラスが同じファイル内に存在せず、アセンブリにコンパイルされずに *\bin* ディレクトリに配置されている場合に、xml web サービスを実装するソースファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-121">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e9fd-122">解説</span><span class="sxs-lookup"><span data-stu-id="2e9fd-122">Remarks</span></span>

<span data-ttu-id="2e9fd-123"><xref:System.ServiceModel.ServiceHost>サービスをホストするために使用されるは、Windows Communication Foundation (WCF) プログラミングモデル内の機能拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-123">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="2e9fd-124">ファクトリ パターンは、ホスティング環境が直接インスタンス化できないポリモーフィック型の可能性があるため、<xref:System.ServiceModel.ServiceHost> のインスタンス化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-124">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="2e9fd-125">既定の実装では <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-125">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2e9fd-126">ただし、ディレクティブでファクトリ実装の CLR 型名を指定することで、独自のファクトリ (派生ホストを返すもの) を指定でき `@ServiceHost` ます。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-126">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="2e9fd-127">既定のファクトリの代わりにカスタムサービスホストファクトリを使用するには、次のようにディレクティブに型名を指定するだけ `@ServiceHost` です。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-127">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="2e9fd-128">ファクトリ実装はできるだけ軽量に保持してください。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-128">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="2e9fd-129">多くのカスタム ロジックがある場合は、それらのロジックをファクトリ内部ではなくホスト内部に置くとコードがさらに再利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-129">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="2e9fd-130">たとえば、の AJAX 対応エンドポイントを有効にするには、 `MyService` <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 次の `Factory` <xref:System.ServiceModel.Activation.ServiceHostFactory> `@ServiceHost` 例に示すように、ディレクティブで属性の値としてを指定します。既定値は使用しません。</span><span class="sxs-lookup"><span data-stu-id="2e9fd-130">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="2e9fd-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e9fd-131">See also</span></span>

- [<span data-ttu-id="2e9fd-132">カスタム サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="2e9fd-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
