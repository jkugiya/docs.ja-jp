---
description: '詳細情報: 生成されたクライアントコードについて'
title: 生成されたクライアント コードの理解
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: c95f02a257cd9417b94190c82fe426a1550f1bf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732957"
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="5d1fe-103">生成されたクライアント コードの理解</span><span class="sxs-lookup"><span data-stu-id="5d1fe-103">Understanding Generated Client Code</span></span>

<span data-ttu-id="5d1fe-104">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) は、クライアント アプリケーションの構築時に使用するクライアント コードとクライアント アプリケーション構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-104">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="5d1fe-105">このトピックでは、標準サービス コントラクトのシナリオ向けに生成されたコード例について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-105">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> <span data-ttu-id="5d1fe-106">生成されたコードを使用してクライアントアプリケーションを構築する方法の詳細については、「 [WCF クライアントの概要](../wcf-client-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-106">For more information about building a client application using the generated code, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5d1fe-107">概要</span><span class="sxs-lookup"><span data-stu-id="5d1fe-107">Overview</span></span>  

 <span data-ttu-id="5d1fe-108">Visual Studio を使用してプロジェクトの Windows Communication Foundation (WCF) クライアントの種類を生成する場合、通常は、生成されたクライアントコードを調べる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-108">If you use Visual Studio to generate Windows Communication Foundation (WCF) client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="5d1fe-109">同じサービスを実行する開発環境を使用していない場合は、Svcutil.exe のようなツールを使用してクライアント コードを生成し、そのコードでクライアント アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-109">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="5d1fe-110">Svcutil.exe には、生成された型情報を変更する多くのオプションがあるため、ここですべてのシナリオを説明することはできません。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-110">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="5d1fe-111">ここでは、生成されたコードの検索に関する標準的な作業の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-111">However, the following standard tasks involve locating generated code:</span></span>  
  
- <span data-ttu-id="5d1fe-112">サービス コントラクト インターフェイスの識別</span><span class="sxs-lookup"><span data-stu-id="5d1fe-112">Identifying service contract interfaces.</span></span>  
  
- <span data-ttu-id="5d1fe-113">WCF クライアントクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-113">Identifying the WCF client class.</span></span>  
  
- <span data-ttu-id="5d1fe-114">データ型の識別</span><span class="sxs-lookup"><span data-stu-id="5d1fe-114">Identifying data types.</span></span>  
  
- <span data-ttu-id="5d1fe-115">双方向サービスのコールバック コントラクトの識別</span><span class="sxs-lookup"><span data-stu-id="5d1fe-115">Identifying callback contracts for duplex services.</span></span>  
  
- <span data-ttu-id="5d1fe-116">ヘルパーのサービス コントラクトのチャネル インターフェイスの識別</span><span class="sxs-lookup"><span data-stu-id="5d1fe-116">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="5d1fe-117">サービス コントラクト インターフェイスの検索</span><span class="sxs-lookup"><span data-stu-id="5d1fe-117">Finding Service Contract Interfaces</span></span>  

 <span data-ttu-id="5d1fe-118">サービス コントラクトをモデル化するインターフェイスを検索するには、 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされたインターフェイスを検索します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-118">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="5d1fe-119">多くの場合、属性自体に設定された他の属性や明示的なプロパティが存在するため、この属性をすばやく読み取って見つけることは簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-119">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="5d1fe-120">サービス コントラクト インターフェイスとクライアント コントラクト インターフェイスは 2 つの別の種類だという点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-120">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="5d1fe-121">次のコード例は、元のサービス コントラクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-121">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="5d1fe-122">次のコード例は、Svcutil.exe で生成された同じサービス コントラクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-122">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="5d1fe-123">生成されたサービスコントラクトインターフェイスをクラスと共に使用して、 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> サービス操作を呼び出すための WCF チャネルオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-123">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a WCF channel object with which to invoke service operations.</span></span> <span data-ttu-id="5d1fe-124">詳細については、「 [方法: ChannelFactory を使用する](how-to-use-the-channelfactory.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-124">For more information, see [How to: Use the ChannelFactory](how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="5d1fe-125">WCF クライアント クラスの検索</span><span class="sxs-lookup"><span data-stu-id="5d1fe-125">Finding WCF Client Classes</span></span>  

 <span data-ttu-id="5d1fe-126">使用するサービスコントラクトを実装する WCF クライアントクラスを検索するには、の拡張を検索し <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ます。ここで、型パラメーターは、以前に配置し、そのインターフェイスを拡張したサービスコントラクトインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-126">To locate the WCF client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="5d1fe-127">次のコード例は、 <xref:System.ServiceModel.ClientBase%601> 型の `ISampleService`クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-127">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="5d1fe-128">この WCF クライアントクラスを使用するには、このクラスの新しいインスタンスを作成し、実装するメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-128">You can use this WCF client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="5d1fe-129">これらのメソッドは、対応しているサービス操作を呼び出し、やり取りを行うように構成されています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-129">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> <span data-ttu-id="5d1fe-130">詳細については、「 [WCF クライアントの概要](../wcf-client-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-130">For more information, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d1fe-131">SvcUtil.exe で WCF クライアント クラスが生成されるとき、 <xref:System.Diagnostics.DebuggerStepThroughAttribute> がクライアント クラスに追加されるため、デバッガーで WCF クライアント クラスをステップ実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-131">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="5d1fe-132">データ型の検索</span><span class="sxs-lookup"><span data-stu-id="5d1fe-132">Finding Data Types</span></span>  

 <span data-ttu-id="5d1fe-133">生成されたコード内でデータ型を検索する最も基本的な方法は、コントラクトに指定された型名を識別し、その型宣言のコードを検索することです。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-133">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="5d1fe-134">たとえば、次のコントラクトには、 `SampleMethod` が型 `microsoft.wcf.documentation.SampleFault`の SOAP エラーを返せることが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-134">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="5d1fe-135">`SampleFault` を検索すると、次の型宣言が見つかります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-135">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="5d1fe-136">この場合、このデータ型は、クライアントの特定の例外 ( <xref:System.ServiceModel.FaultException%601> ) によりスローされる詳細な型です。詳細な型のパラメーターは、 `microsoft.wcf.documentation.SampleFault`です。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-136">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> <span data-ttu-id="5d1fe-137">データ型の詳細については、「 [サービスコントラクトでのデータ転送の指定](specifying-data-transfer-in-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-137">For more information about data types, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="5d1fe-138">クライアントでの例外処理の詳細については、「 [エラーの送受信](../sending-and-receiving-faults.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-138">For more information about handling exceptions in clients, see [Sending and Receiving Faults](../sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="5d1fe-139">双方向サービスのコールバック コントラクトの検索</span><span class="sxs-lookup"><span data-stu-id="5d1fe-139">Finding Callback Contracts for Duplex Services</span></span>  

 <span data-ttu-id="5d1fe-140">コントラクト インターフェイスにより <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> プロパティの値が指定されているサービス コントラクトを検索すると、そのコントラクトには双方向コントラクトが指定されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-140">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="5d1fe-141">二重のコントラクトを使用した場合、クライアント アプリケーションは、コールバック コントラクトを実装するコールバック クラスを作成し、そのクラスのインスタンスを、サービスとの通信に使用する <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> または <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-141">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> <span data-ttu-id="5d1fe-142">双方向クライアントの詳細については、「 [方法: 双方向コントラクトを使用してサービスにアクセスする](how-to-access-services-with-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-142">For more information about duplex clients, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="5d1fe-143">次のコントラクトは、型 `SampleDuplexHelloCallback`のコールバック コントラクトを指定しています。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-143">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="5d1fe-144">このコールバック コントラクトを検索すると、クライアント アプリケーションが実装する必要のある次のインターフェイスが見つかります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-144">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="5d1fe-145">サービス コントラクト チャネル インターフェイスの検索</span><span class="sxs-lookup"><span data-stu-id="5d1fe-145">Finding Service Contract Channel Interfaces</span></span>  

 <span data-ttu-id="5d1fe-146">サービス コントラクト インターフェイスで <xref:System.ServiceModel.ChannelFactory> クラスを使用する場合、明示的にチャネルを開いたり、閉じたり、中止したりするには、 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> インターフェイスにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-146">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="5d1fe-147">処理を容易にするために、Svcutil.exe ツールでは、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel> の両方を実装するヘルパー インターフェイスも生成されます。これにより、キャストを行わずにクライアント チャネル インフラストラクチャとのやりとりを実現できます。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-147">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="5d1fe-148">上記のサービス コントラクトを実装するヘルパー クライアント チャネルの定義を、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5d1fe-148">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="5d1fe-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d1fe-149">See also</span></span>

- [<span data-ttu-id="5d1fe-150">WCF クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="5d1fe-150">WCF Client Overview</span></span>](../wcf-client-overview.md)
