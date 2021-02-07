---
description: '詳細情報: エンドポイント作成の概要'
title: エンドポイントの作成の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: ff806428922f2097f0d570118d6b5f7836c1797b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756826"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="caf17-103">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="caf17-103">Endpoint Creation Overview</span></span>

<span data-ttu-id="caf17-104">Windows Communication Foundation (WCF) サービスとの通信はすべて、サービスの *エンドポイント* を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="caf17-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="caf17-105">エンドポイントは、クライアントが WCF サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="caf17-105">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="caf17-106">ここでは、エンドポイントの構造を説明し、構成やコード内にエンドポイントを定義する方法を概説します。</span><span class="sxs-lookup"><span data-stu-id="caf17-106">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="caf17-107">エンドポイントの構造</span><span class="sxs-lookup"><span data-stu-id="caf17-107">The Structure of an Endpoint</span></span>

<span data-ttu-id="caf17-108">各エンドポイントは、そのエンドポイントが存在する場所を示すアドレス、クライアントがエンドポイントと通信するための方法を指定するバインディング、および利用可能なメソッドを特定するコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="caf17-108">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="caf17-109">**アドレス**。</span><span class="sxs-lookup"><span data-stu-id="caf17-109">**Address**.</span></span> <span data-ttu-id="caf17-110">アドレスは、エンドポイントを一意に識別し、潜在的ユーザーにそのサービスの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="caf17-110">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="caf17-111">これは、WCF オブジェクトモデルでは、アドレスによって表されます。このアドレスには、 <xref:System.ServiceModel.EndpointAddress> id、Web サービス記述言語 (WSDL) 要素、および省略可能なヘッダーのコレクションを含む Uniform Resource Identifier (URI) とアドレスのプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="caf17-111">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="caf17-112">オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="caf17-112">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="caf17-113">詳細については、「 [エンドポイントアドレスの指定](specifying-an-endpoint-address.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-113">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="caf17-114">**バインド**。</span><span class="sxs-lookup"><span data-stu-id="caf17-114">**Binding**.</span></span> <span data-ttu-id="caf17-115">バインディングはエンドポイントとの通信方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="caf17-115">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="caf17-116">バインディングでは、使用するトランスポート プロトコル (TCP や HTTP)、メッセージのエンコーディング方法 (テキストやバイナリ)、必要なセキュリティ要件 (SSL (Secure Sockets Layer) や SOAP メッセージ セキュリティ) など、そのエンドポイントがどのように通信を行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="caf17-116">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="caf17-117">詳細については、「バインディングを使用した [サービスとクライアントの構成](using-bindings-to-configure-services-and-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-117">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="caf17-118">**サービスコントラクト**。</span><span class="sxs-lookup"><span data-stu-id="caf17-118">**Service contract**.</span></span> <span data-ttu-id="caf17-119">サービス コントラクトは、エンドポイントがクライアントに公開する機能を示します。</span><span class="sxs-lookup"><span data-stu-id="caf17-119">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="caf17-120">コントラクトは、クライアントが呼び出すことのできる操作、メッセージの形式、操作の呼び出しに必要な入力パラメーターやデータの型、クライアントに提供する処理または応答メッセージの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="caf17-120">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="caf17-121">基本的なメッセージ交換パターン (MEP) に対応する基本的なコントラクトの種類には、データグラム (一方向)、要求/応答、二重 (双方向) の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="caf17-121">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="caf17-122">サービス コントラクトは、データ コントラクトとメッセージ コントラクトを使用して、クライアントが特定のデータ型とメッセージ形式でアクセスするように要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="caf17-122">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="caf17-123">サービスコントラクトを定義する方法の詳細については、「 [サービスコントラクトの設計](designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-123">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="caf17-124">クライアントでは、二重 MEP でサービスからメッセージを受信するために、コールバック コントラクトというサービス定義のコントラクトを実装することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="caf17-124">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="caf17-125">詳細については、「 [双方向サービス](./feature-details/duplex-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-125">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="caf17-126">サービスのエンドポイントはコードを使用して強制的に指定するか、構成を介して宣言として指定できます。</span><span class="sxs-lookup"><span data-stu-id="caf17-126">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="caf17-127">エンドポイントが指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="caf17-127">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="caf17-128">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="caf17-128">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="caf17-129">一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。</span><span class="sxs-lookup"><span data-stu-id="caf17-129">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="caf17-130">バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="caf17-130">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="caf17-131">偽装を行うサービス エンドポイントを追加する場合は、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドまたは <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> メソッドのいずれかを使用して、コントラクトを新しい <xref:System.ServiceModel.Description.ServiceDescription> オブジェクトに適切に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="caf17-131">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="caf17-132">コードでのエンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="caf17-132">Defining Endpoints in Code</span></span>

<span data-ttu-id="caf17-133">次の例は、コードにエンドポイントを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="caf17-133">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="caf17-134">任意 `IEcho` のユーザーの名前を受け取り、応答 "Hello!" を使用してエコーするサービスの種類のコントラクトを定義し \<name> ます。</span><span class="sxs-lookup"><span data-stu-id="caf17-134">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="caf17-135">`Echo` コントラクトで定義された型の `IEcho` サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="caf17-135">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="caf17-136">サービスのエンドポイントアドレスを指定し `http://localhost:8000/Echo` ます。</span><span class="sxs-lookup"><span data-stu-id="caf17-136">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="caf17-137">`Echo` バインディングを使用して <xref:System.ServiceModel.WSHttpBinding> サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="caf17-137">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="caf17-138">サービス ホストはベース アドレスを使用して作成されます。また、残りのアドレス (ベース アドレスの相対アドレス) はエンドポイントの一部として指定されます。</span><span class="sxs-lookup"><span data-stu-id="caf17-138">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="caf17-139">このようにアドレスを分割することで、ホストのサービスで複数のエンドポイントを簡単に定義できるようになります。</span><span class="sxs-lookup"><span data-stu-id="caf17-139">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="caf17-140"><xref:System.ServiceModel.Description.ServiceDescription> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> メソッドの後で、サービス アプリケーションの <xref:System.ServiceModel.ServiceHostBase> の各プロパティを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="caf17-140">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="caf17-141">このメソッドの後で変更すると、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> および `AddServiceEndpoint` の <xref:System.ServiceModel.ServiceHostBase> プロパティや <xref:System.ServiceModel.ServiceHost> メソッドなどの一部のメンバーは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="caf17-141">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="caf17-142">変更を許可するメンバーもありますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="caf17-142">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="caf17-143">同様に、クライアントで、<xref:System.ServiceModel.Description.ServiceEndpoint> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 呼び出しの後で、<xref:System.ServiceModel.ChannelFactory> 値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="caf17-143">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="caf17-144">この呼び出しの後で変更すると、<xref:System.ServiceModel.ChannelFactory.Credentials%2A> プロパティは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="caf17-144">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="caf17-145">その他のクライアント記述値は、エラーを発生させずに変更できますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="caf17-145">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="caf17-146">サービスとクライアントのどちらの場合も、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> の呼び出しの前に記述を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="caf17-146">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="caf17-147">構成でのエンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="caf17-147">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="caf17-148">アプリケーションの作成では、各種決定事項をアプリケーションを展開する管理者に任せる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="caf17-148">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="caf17-149">たとえば、どのサービス アドレス (URI) を使用するかなどの情報は、前もって知るすべがありません。</span><span class="sxs-lookup"><span data-stu-id="caf17-149">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="caf17-150">アドレスをハードコーディングする代わりに、サービスの作成後に管理者が指定する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="caf17-150">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="caf17-151">構成を活用することで、この柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="caf17-151">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="caf17-152">詳細については、「 [サービスの構成](configuring-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-152">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="caf17-153">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)と filename filename スイッチを使用して、 `/config:`  `[,`  `]` 構成ファイルをすばやく作成します。</span><span class="sxs-lookup"><span data-stu-id="caf17-153">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="caf17-154">既定のエンドポイントの使用</span><span class="sxs-lookup"><span data-stu-id="caf17-154">Using Default Endpoints</span></span>

<span data-ttu-id="caf17-155">エンドポイントがコードまたは構成で指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="caf17-155">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="caf17-156">ベース アドレスはコードまたは構成で指定することができ、既定のエンドポイントは、<xref:System.ServiceModel.ICommunicationObject.Open> が <xref:System.ServiceModel.ServiceHost> で呼び出されるときに追加されます。</span><span class="sxs-lookup"><span data-stu-id="caf17-156">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="caf17-157">次の例は上記のセクションの例と同じです。ただし、エンドポイントを指定せず、既定のエンドポイントを追加する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="caf17-157">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="caf17-158">エンドポイントを明示的に指定しない場合、<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> を呼び出す前に、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出すことによって、既定のエンドポイントを引き続き追加できます。</span><span class="sxs-lookup"><span data-stu-id="caf17-158">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="caf17-159">既定のエンドポイントの詳細については、「 [WCF サービスの](./samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf17-159">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="caf17-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="caf17-160">See also</span></span>

- [<span data-ttu-id="caf17-161">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="caf17-161">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
