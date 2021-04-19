---
title: サービス コントラクトの設計
description: サービス コントラクトについて説明します。これには、その作成方法、使用可能な操作とデータ型、および WCF プログラミングにおけるサービス コントラクトのその他の側面が含まれます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 11d2019023c7389d27607c93b920946837b5c365
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294829"
---
# <a name="designing-service-contracts"></a><span data-ttu-id="55ca9-103">サービス コントラクトの設計</span><span class="sxs-lookup"><span data-stu-id="55ca9-103">Designing Service Contracts</span></span>

<span data-ttu-id="55ca9-104">ここでは、サービス コントラクトの概要、定義方法、使用できる操作 (および基になるメッセージ交換の影響)、使用するデータ型、およびシナリオの要件を満たす操作を設計する際に役立つその他の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-104">This topic describes what service contracts are, how they are defined, what operations are available (and the implications for the underlying message exchanges), what data types are used, and other issues that help you design operations that satisfy the requirements of your scenario.</span></span>  
  
## <a name="creating-a-service-contract"></a><span data-ttu-id="55ca9-105">サービス コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="55ca9-105">Creating a Service Contract</span></span>  

 <span data-ttu-id="55ca9-106">サービスは複数の操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-106">Services expose a number of operations.</span></span> <span data-ttu-id="55ca9-107">Windows Communication Foundation (WCF) アプリケーションでは、メソッドを作成し、<xref:System.ServiceModel.OperationContractAttribute> 属性でマークすることによって操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-107">In Windows Communication Foundation (WCF) applications, define the operations by creating a method and marking it with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> <span data-ttu-id="55ca9-108">次に、サービス コントラクトを作成するために、<xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされたインターフェイス内で操作を宣言するか、この属性でマークされたクラス内で操作を定義することにより、操作をグループ化します </span><span class="sxs-lookup"><span data-stu-id="55ca9-108">Then, to create a service contract, group together your operations, either by declaring them within an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute, or by defining them in a class marked with the same attribute.</span></span> <span data-ttu-id="55ca9-109">(基本的な例については、「[方法: サービス コントラクトを定義する](how-to-define-a-wcf-service-contract.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="55ca9-109">(For a basic example, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).)</span></span>  
  
 <span data-ttu-id="55ca9-110"><xref:System.ServiceModel.OperationContractAttribute> 属性を持たないメソッドはサービス操作ではないため、WCF サービスによって公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-110">Any methods that do not have a <xref:System.ServiceModel.OperationContractAttribute> attribute are not service operations and are not exposed by WCF services.</span></span>  
  
 <span data-ttu-id="55ca9-111">ここでは、サービス コントラクトの設計時に決定すべき以下のポイントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-111">This topic describes the following decision points when designing a service contract:</span></span>  
  
- <span data-ttu-id="55ca9-112">クラスとインターフェイスのどちらを使用するか</span><span class="sxs-lookup"><span data-stu-id="55ca9-112">Whether to use classes or interfaces.</span></span>  
  
- <span data-ttu-id="55ca9-113">交換するデータ型の指定方法</span><span class="sxs-lookup"><span data-stu-id="55ca9-113">How to specify the data types you want to exchange.</span></span>  
  
- <span data-ttu-id="55ca9-114">使用できる交換パターンの種類</span><span class="sxs-lookup"><span data-stu-id="55ca9-114">The types of exchange patterns you can use.</span></span>  
  
- <span data-ttu-id="55ca9-115">コントラクトのセキュリティ要件の部分を明示的に作成できるかどうか</span><span class="sxs-lookup"><span data-stu-id="55ca9-115">Whether you can make explicit security requirements part of the contract.</span></span>  
  
- <span data-ttu-id="55ca9-116">操作の入力と出力の制限</span><span class="sxs-lookup"><span data-stu-id="55ca9-116">The restrictions for operation inputs and outputs.</span></span>  
  
## <a name="classes-or-interfaces"></a><span data-ttu-id="55ca9-117">クラスとインターフェイス</span><span class="sxs-lookup"><span data-stu-id="55ca9-117">Classes or Interfaces</span></span>  

 <span data-ttu-id="55ca9-118">クラスとインターフェイスは、いずれも機能のグループ化を表します。したがって、どちらを使用しても WCF サービス コントラクトを定義できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-118">Both classes and interfaces represent a grouping of functionality and, therefore, both can be used to define a WCF service contract.</span></span> <span data-ttu-id="55ca9-119">ただし、インターフェイスはサービス コントラクトを直接モデル化するため、インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55ca9-119">However, it is recommended that you use interfaces because they directly model service contracts.</span></span> <span data-ttu-id="55ca9-120">実装のないインターフェイスは、特定のシグネチャを持つメソッドのグループ化を定義しているにすぎません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-120">Without an implementation, interfaces do no more than define a grouping of methods with certain signatures.</span></span> <span data-ttu-id="55ca9-121">サービス コントラクト インターフェイスを実装してはじめて、WCF サービスを実装したことになります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-121">Implement a service contract interface and you have implemented a WCF service.</span></span>  
  
 <span data-ttu-id="55ca9-122">サービス コントラクト インターフェイスには、次のようにマネージド インターフェイスのあらゆる利点がもたらされます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-122">All the benefits of managed interfaces apply to service contract interfaces:</span></span>  
  
- <span data-ttu-id="55ca9-123">サービス コントラクト インターフェイスでは、他のサービス コントラクト インターフェイスをいくつでも拡張できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-123">Service contract interfaces can extend any number of other service contract interfaces.</span></span>  
  
- <span data-ttu-id="55ca9-124">これらのサービス コントラクト インターフェイスを実装することにより、1 つのクラスでサービス コントラクトをいくつでも実装できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-124">A single class can implement any number of service contracts by implementing those service contract interfaces.</span></span>  
  
- <span data-ttu-id="55ca9-125">インターフェイスの実装を変更することにより、同じサービス コントラクトを引き続き使用したまま、そのコントラクトの実装を変更できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-125">You can modify the implementation of a service contract by changing the interface implementation, while the service contract remains the same.</span></span>  
  
- <span data-ttu-id="55ca9-126">以前のインターフェイスと新しいインターフェイスを実装することで、サービスをバージョン管理できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-126">You can version your service by implementing the old interface and the new one.</span></span> <span data-ttu-id="55ca9-127">以前のクライアントは元のバージョンに接続し、新しいクライアントは新しいバージョンに接続できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-127">Old clients connect to the original version, while newer clients can connect to the newer version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55ca9-128">他のサービス コントラクト インターフェイスから継承した場合、操作のプロパティ (名前や名前空間など) をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-128">When inheriting from other service contract interfaces, you cannot override operation properties, such as the name or namespace.</span></span> <span data-ttu-id="55ca9-129">これを行う場合は、現在のサービス コントラクトに新しい操作を作成します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-129">If you attempt to do so, you create a new operation in the current service contract.</span></span>  
  
 <span data-ttu-id="55ca9-130">インターフェイスを使用してサービス コントラクトを作成する例については、「[方法: コントラクト インターフェイスを使用してサービスを作成する](./feature-details/how-to-create-a-service-with-a-contract-interface.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-130">For an example of using an interface to create a service contract, see [How to: Create a Service with a Contract Interface](./feature-details/how-to-create-a-service-with-a-contract-interface.md).</span></span>  
  
 <span data-ttu-id="55ca9-131">クラスを使用すると、サービス コントラクトの定義と実装を一度に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-131">You can, however, use a class to define a service contract and implement that contract at the same time.</span></span> <span data-ttu-id="55ca9-132"><xref:System.ServiceModel.ServiceContractAttribute> と <xref:System.ServiceModel.OperationContractAttribute> をそれぞれクラスとクラスのメソッドに直接適用してサービスを作成する方法には、サービスを迅速かつ簡単に作成できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-132">The advantage of creating your services by applying <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> directly to the class and the methods on the class, respectively, is speed and simplicity.</span></span> <span data-ttu-id="55ca9-133">欠点は、マネージド クラスでは複数の継承をサポートしていないため、サービス コントラクトを一度に 1 つしか実装できないことです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-133">The disadvantages are that managed classes do not support multiple inheritance, and as a result they can only implement one service contract at a time.</span></span> <span data-ttu-id="55ca9-134">また、クラスまたはメソッド シグネチャに変更を加えると、そのサービスのパブリック コントラクトが変更されるため、変更されていないクライアントがサービスを使用できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-134">In addition, any modification to the class or method signatures modifies the public contract for that service, which can prevent unmodified clients from using your service.</span></span> <span data-ttu-id="55ca9-135">詳細については、「[サービス コントラクトの実装](implementing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-135">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
 <span data-ttu-id="55ca9-136">クラスを使用してサービス コントラクトの作成と実装を一度に行う例については、「[方法: コントラクト クラスを使用してサービスを作成する](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-136">For an example that uses a class to create a service contract and implements it at the same time, see [How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).</span></span>  
  
 <span data-ttu-id="55ca9-137">これで、サービス コントラクトを定義する際に、インターフェイスを使用した場合とクラスを使用した場合の違いがわかりました。</span><span class="sxs-lookup"><span data-stu-id="55ca9-137">At this point, you should understand the difference between defining your service contract by using an interface and by using a class.</span></span> <span data-ttu-id="55ca9-138">次に、サービスとクライアント間で受け渡しできるデータを決定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-138">The next step is deciding what data can be passed back and forth between a service and its clients.</span></span>  
  
## <a name="parameters-and-return-values"></a><span data-ttu-id="55ca9-139">パラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="55ca9-139">Parameters and Return Values</span></span>  

 <span data-ttu-id="55ca9-140">各操作は戻り値とパラメーターを持ちます (戻り値とパラメーターが `void` の場合も含まれます)。</span><span class="sxs-lookup"><span data-stu-id="55ca9-140">Each operation has a return value and a parameter, even if these are `void`.</span></span> <span data-ttu-id="55ca9-141">ただし、オブジェクトへの参照をオブジェクト間で渡すことができるローカル メソッドとは異なり、サービス操作ではオブジェクトへの参照を渡しません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-141">However, unlike a local method, in which you can pass references to objects from one object to another, service operations do not pass references to objects.</span></span> <span data-ttu-id="55ca9-142">代わりに、オブジェクトのコピーを渡します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-142">Instead, they pass copies of the objects.</span></span>  
  
 <span data-ttu-id="55ca9-143">これが重要なのは、パラメーターまたは戻り値で使用される各型がシリアル化可能でなければならないためです。つまり、その型のオブジェクトをバイト ストリームに変換でき、バイト ストリームからオブジェクトに変換できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-143">This is significant because each type used in a parameter or return value must be serializable; that is, it must be possible to convert an object of that type into a stream of bytes and from a stream of bytes into an object.</span></span>  
  
 <span data-ttu-id="55ca9-144">プリミティブ型は既定でシリアル化可能であり、.NET Framework の多くの型も同様です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-144">Primitive types are serializable by default, as are many types in the .NET Framework.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55ca9-145">操作シグネチャのパラメーター名の値はコントラクトに含まれ、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-145">The value of the parameter names in the operation signature are part of the contract and are case sensitive.</span></span> <span data-ttu-id="55ca9-146">ローカルでは同じパラメーター名を使用するが、公開されるメタデータでは名前を変更する場合は、<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-146">If you want to use the same parameter name locally but modify the name in the published metadata, see the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.</span></span>  
  
#### <a name="data-contracts"></a><span data-ttu-id="55ca9-147">データ コントラクト</span><span class="sxs-lookup"><span data-stu-id="55ca9-147">Data Contracts</span></span>  

 <span data-ttu-id="55ca9-148">Windows Communication Foundation (WCF) アプリケーションのようなサービス指向アプリケーションは、Microsoft と Microsoft 以外の両方のプラットフォームで、できる限り多くのクライアント アプリケーションと相互運用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="55ca9-148">Service-oriented applications like Windows Communication Foundation (WCF) applications are designed to interoperate with the widest possible number of client applications on both Microsoft and non-Microsoft platforms.</span></span> <span data-ttu-id="55ca9-149">最大限の相互運用性を実現するために、使用する型を <xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性でマークして、データ コントラクトを作成することをお勧めします。データ コントラクトは、サービス コントラクトの一部であり、サービス操作で交換するデータを記述したものです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-149">For the widest possible interoperability, it is recommended that you mark your types with the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create a data contract, which is the portion of the service contract that describes the data that your service operations exchange.</span></span>  
  
 <span data-ttu-id="55ca9-150">データ コントラクトは opt-in 方式のコントラクトです。つまり、データ コントラクト属性を明示的に適用しない限り、型またはデータ メンバーはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-150">Data contracts are opt-in style contracts: No type or data member is serialized unless you explicitly apply the data contract attribute.</span></span> <span data-ttu-id="55ca9-151">データ コントラクトはマネージド コードのアクセス スコープとして関連付けられていません。プライベートのデータ メンバーはシリアル化され、パブリックにアクセスされる他の場所に送信されます </span><span class="sxs-lookup"><span data-stu-id="55ca9-151">Data contracts are unrelated to the access scope of the managed code: Private data members can be serialized and sent elsewhere to be accessed publicly.</span></span> <span data-ttu-id="55ca9-152">(データ コントラクトの基本的な例については、「[方法: クラスまたは構造体に基本的なデータ コントラクトを作成する](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)」を参照してください。)WCF によって、基になる SOAP メッセージの定義が処理されます。これにより、操作の機能が有効になるだけでなく、データ型とメッセージ本文との間での双方向のシリアル化が可能になります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-152">(For a basic example of a data contract, see [How to: Create a Basic Data Contract for a Class or Structure](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF handles the definition of the underlying SOAP messages that enable the operation's functionality as well as the serialization of your data types into and out of the body of the messages.</span></span> <span data-ttu-id="55ca9-153">使用するデータ型がシリアル化可能であれば、操作の設計時に、基盤となるメッセージ交換インフラストラクチャについて考える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-153">As long as your data types are serializable, you do not need to think about the underlying message exchange infrastructure when designing your operations.</span></span>  
  
 <span data-ttu-id="55ca9-154">通常の WCF アプリケーションでは <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を使用して操作のデータ コントラクトが作成されますが、他のシリアル化機構を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-154">Although the typical WCF application uses the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create data contracts for operations, you can use other serialization mechanisms.</span></span> <span data-ttu-id="55ca9-155"><xref:System.Runtime.Serialization.ISerializable>、<xref:System.SerializableAttribute>、および <xref:System.Xml.Serialization.IXmlSerializable> の各標準機構はすべて、基になる SOAP メッセージへのデータ型のシリアル化を処理します。このメッセージはアプリケーション間でデータ型を伝達します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-155">The standard <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> and <xref:System.Xml.Serialization.IXmlSerializable> mechanisms all work to handle the serialization of your data types into the underlying SOAP messages that carry them from one application to another.</span></span> <span data-ttu-id="55ca9-156">使用するデータ型で特別なサポートが必要な場合は、さらに多くのシリアル化方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-156">You can employ more serialization strategies if your data types require special support.</span></span> <span data-ttu-id="55ca9-157">WCF アプリケーションでのデータ型のシリアル化の選択肢について詳しくは、「[サービス コントラクトでのデータ転送の指定](./feature-details/specifying-data-transfer-in-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-157">For more information about the choices for serialization of data types in WCF applications, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span>  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a><span data-ttu-id="55ca9-158">メッセージ交換へのパラメーターと戻り値のマッピング</span><span class="sxs-lookup"><span data-stu-id="55ca9-158">Mapping Parameters and Return Values to Message Exchanges</span></span>  

 <span data-ttu-id="55ca9-159">サービス操作は、特定の標準セキュリティ、トランザクション、およびセッション関連の機能をサポートするためにアプリケーションが必要とするデータに加え、アプリケーション データをやり取りする SOAP メッセージの基になる交換によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-159">Service operations are supported by an underlying exchange of SOAP messages that transfer application data back and forth, in addition to the data required by the application to support certain standard security, transaction, and session-related features.</span></span> <span data-ttu-id="55ca9-160">このため、サービス操作のシグネチャにより、データ転送と操作に必要な機能をサポートできる、基になる "*メッセージ交換パターン*" (MEP: Message Exchange Pattern) を指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-160">Because this is the case, the signature of a service operation dictates a certain underlying *message exchange pattern* (MEP) that can support the data transfer and the features an operation requires.</span></span> <span data-ttu-id="55ca9-161">WCF プログラミング モデルでは、要求/応答、一方向、および双方向の 3 つのメッセージ パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-161">You can specify three patterns in the WCF programming model: request/reply, one-way, and duplex message patterns.</span></span>  
  
##### <a name="requestreply"></a><span data-ttu-id="55ca9-162">要求/応答</span><span class="sxs-lookup"><span data-stu-id="55ca9-162">Request/Reply</span></span>  

 <span data-ttu-id="55ca9-163">要求/応答パターンでは、要求の送信側 (クライアント アプリケーション) は、その要求に関連付けられた応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-163">A request/reply pattern is one in which a request sender (a client application) receives a reply with which the request is correlated.</span></span> <span data-ttu-id="55ca9-164">このパターンでは、1 つの操作において、1 つ以上のパラメーターを操作に渡し、戻り値を呼び出し元に返すことができるため、このパターンが既定の MEP となります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-164">This is the default MEP because it supports an operation in which one or more parameters are passed to the operation and a return value is passed back to the caller.</span></span> <span data-ttu-id="55ca9-165">たとえば、次の C# コード例は、文字列を 1 つ受け取り、文字列を返す基本的なサービス操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="55ca9-165">For example, the following C# code example shows a basic service operation that takes one string and returns a string.</span></span>  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 <span data-ttu-id="55ca9-166">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-166">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 <span data-ttu-id="55ca9-167">この操作シグネチャは、基になるメッセージ交換の形式を指定しています。</span><span class="sxs-lookup"><span data-stu-id="55ca9-167">This operation signature dictates the form of underlying message exchange.</span></span> <span data-ttu-id="55ca9-168">相関関係がない場合、WCF では戻り値の対象となる操作を特定できません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-168">If no correlation existed, WCF cannot determine for which operation the return value is intended.</span></span>  
  
 <span data-ttu-id="55ca9-169">別の基になるメッセージ パターンを指定しない限り、`void` (Visual Basic では `Nothing`) を返すサービス操作も要求/応答メッセージ交換であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-169">Note that unless you specify a different underlying message pattern, even service operations that return `void` (`Nothing` in Visual Basic) are request/reply message exchanges.</span></span> <span data-ttu-id="55ca9-170">クライアントが操作を非同期で呼び出していない場合、通常、メッセージが空の場合でも、戻りメッセージを受信するまでクライアントは処理を中止します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-170">The result for your operation is that unless a client invokes the operation asynchronously, the client stops processing until the return message is received, even though that message is empty in the normal case.</span></span> <span data-ttu-id="55ca9-171">クライアントが応答で空のメッセージを受信するまで制御が戻らない操作の C# コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-171">The following C# code example shows an operation that does not return until the client has received an empty message in response.</span></span>  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="55ca9-172">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-172">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="55ca9-173">上記の例では、実行に時間のかかる操作の場合に、クライアントのパフォーマンスと応答性が低下するおそれがありますが、要求/応答操作で `void` を返す場合でも、この操作には利点があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-173">The preceding example can slow client performance and responsiveness if the operation takes a long time to perform, but there are advantages to request/reply operations even when they return `void`.</span></span> <span data-ttu-id="55ca9-174">最も明らかな利点は、応答メッセージで SOAP エラーを返すことが可能であるということです。これにより、通信と処理のどちらで発生したかに関係なく、サービス関連の何らかのエラー状態が発生したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-174">The most obvious one is that SOAP faults can be returned in the response message, which indicates that some service-related error condition has occurred, whether in communication or processing.</span></span> <span data-ttu-id="55ca9-175">サービス コントラクトに指定された SOAP エラーは、<xref:System.ServiceModel.FaultException%601> オブジェクトとしてクライアント アプリケーションに渡されます。このオブジェクトの型パラメーターは、サービス コントラクトで指定された型です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-175">SOAP faults that are specified in a service contract are passed to the client application as a <xref:System.ServiceModel.FaultException%601> object, where the type parameter is the type specified in the service contract.</span></span> <span data-ttu-id="55ca9-176">これにより、WCF サービスのエラー状態をクライアントに通知しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-176">This makes notifying clients about error conditions in WCF services easy.</span></span> <span data-ttu-id="55ca9-177">例外、SOAP エラー、およびエラー処理の詳細については、「[コントラクトおよびサービスのエラーの指定と処理](specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-177">For more information about exceptions, SOAP faults, and error handling, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span> <span data-ttu-id="55ca9-178">要求/応答サービスとクライアントの例については、「[方法: 要求/応答コントラクトを作成する](./feature-details/how-to-create-a-request-reply-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-178">To see an example of a request/reply service and client, see [How to: Create a Request-Reply Contract](./feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="55ca9-179">要求/応答パターンに関する問題の詳細については、「[要求/応答サービス](./feature-details/request-reply-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-179">For more information about issues with the request-reply pattern, see [Request-Reply Services](./feature-details/request-reply-services.md).</span></span>  
  
##### <a name="one-way"></a><span data-ttu-id="55ca9-180">一方向</span><span class="sxs-lookup"><span data-stu-id="55ca9-180">One-way</span></span>  

 <span data-ttu-id="55ca9-181">WCF サービス アプリケーションのクライアントが操作の完了まで待機する必要がなく、SOAP エラーも処理しない場合は、操作により一方向メッセージ パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-181">If the client of a WCF service application should not wait for the operation to complete and does not process SOAP faults, the operation can specify a one-way message pattern.</span></span> <span data-ttu-id="55ca9-182">一方向操作では、クライアントによって操作が呼び出され、WCF によってメッセージがネットワークに書き込まれた後で処理が続行されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-182">A one-way operation is one in which a client invokes an operation and continues processing after WCF writes the message to the network.</span></span> <span data-ttu-id="55ca9-183">通常、これは、送信メッセージで送信するデータが膨大な量でない限り、(データ送信時にエラーが発生しなければ) クライアントはほぼすぐに実行を続けることを意味します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-183">Typically this means that unless the data being sent in the outbound message is extremely large the client continues running almost immediately (unless there is an error sending the data).</span></span> <span data-ttu-id="55ca9-184">この種のメッセージ交換パターンでは、クライアントからサービス アプリケーションへのイベントのような動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="55ca9-184">This type of message exchange pattern supports event-like behavior from a client to a service application.</span></span>  
  
 <span data-ttu-id="55ca9-185">1 つのメッセージを送信し、何も受信しないメッセージ交換では、`void` 以外の戻り値を指定したサービス操作をサポートすることはできません。この場合、<xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-185">A message exchange in which one message is sent and none are received cannot support a service operation that specifies a return value other than `void`; in this case an <xref:System.InvalidOperationException> exception is thrown.</span></span>  
  
 <span data-ttu-id="55ca9-186">戻りメッセージがないということは、処理または通信時のエラーを示すために SOAP エラーを返すこともできないということです </span><span class="sxs-lookup"><span data-stu-id="55ca9-186">No return message also means that there can be no SOAP fault returned to indicate any errors in processing or communication.</span></span> <span data-ttu-id="55ca9-187">(操作が一方向操作の場合にエラー情報を伝達するには、双方向メッセージ交換パターンが必要です)。</span><span class="sxs-lookup"><span data-stu-id="55ca9-187">(Communicating error information when operations are one-way operations requires a duplex message exchange pattern.)</span></span>  
  
 <span data-ttu-id="55ca9-188">`void` を返す操作で一方向メッセージ交換を指定するには、次の C# コード例に示すように、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-188">To specify a one-way message exchange for an operation that returns `void`, set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as in the following C# code example.</span></span>  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="55ca9-189">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-189">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="55ca9-190">このメソッドは、前述の要求/応答の例と同じです。ただし、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定するということは、メソッドは同じでも、サービス操作は戻りメッセージを送信せず、送信メッセージがチャネル レイヤーに渡されると、すぐにクライアントに制御が戻ることを意味します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-190">This method is identical to the preceding request/reply example, but setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` means that although the method is identical, the service operation does not send a return message and clients return immediately once the outbound message has been handed to the channel layer.</span></span> <span data-ttu-id="55ca9-191">例については、「[方法: 一方向コントラクトを作成する](./feature-details/how-to-create-a-one-way-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-191">For an example, see [How to: Create a One-Way Contract](./feature-details/how-to-create-a-one-way-contract.md).</span></span> <span data-ttu-id="55ca9-192">一方向のパターンの詳細については、「[一方向サービス](./feature-details/one-way-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-192">For more information about the one-way pattern, see [One-Way Services](./feature-details/one-way-services.md).</span></span>  
  
##### <a name="duplex"></a><span data-ttu-id="55ca9-193">二重</span><span class="sxs-lookup"><span data-stu-id="55ca9-193">Duplex</span></span>  

 <span data-ttu-id="55ca9-194">双方向パターンの特徴は、一方向メッセージングと要求/応答メッセージングのどちらを使用しているかに関係なく、サービスとクライアントが共に独立して、相互にメッセージを送信できるという点です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-194">A duplex pattern is characterized by the ability of both the service and the client to send messages to each other independently whether using one-way or request/reply messaging.</span></span> <span data-ttu-id="55ca9-195">二方向通信のこの形式は、サービスがクライアントと直接通信する必要がある場合や、イベントのような動作など、メッセージを交換するどちらの側も非同期で動作できるようにする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-195">This form of two-way communication is useful for services that must communicate directly to the client or for providing an asynchronous experience to either side of a message exchange, including event-like behavior.</span></span>  
  
 <span data-ttu-id="55ca9-196">双方向パターンでは、クライアントと通信するための機構が別途必要になるため、要求/応答パターンや一方向パターンに比べると若干複雑になります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-196">The duplex pattern is slightly more complex than the request/reply or one-way patterns because of the additional mechanism for communicating with the client.</span></span>  
  
 <span data-ttu-id="55ca9-197">双方向コントラクトを設計する場合、コールバック コントラクトも設計し、そのコールバック コントラクトの型を、サービス コントラクトをマークする <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 属性の <xref:System.ServiceModel.ServiceContractAttribute> プロパティに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-197">To design a duplex contract, you must also design a callback contract and assign the type of that callback contract to the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property of the <xref:System.ServiceModel.ServiceContractAttribute> attribute that marks your service contract.</span></span>  
  
 <span data-ttu-id="55ca9-198">双方向パターンを実装するには、クライアントで呼び出されるメソッド宣言を含む 2 つ目のインターフェイスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-198">To implement a duplex pattern, you must create a second interface that contains the method declarations that are called on the client.</span></span>  
  
 <span data-ttu-id="55ca9-199">サービスを作成する例と、そのサービスにアクセスするクライアントについては、「[方法: 双方向コントラクトを作成する](./feature-details/how-to-create-a-duplex-contract.md)」および「[方法: 双方向コントラクトを使用してサービスにアクセスする](./feature-details/how-to-access-services-with-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-199">For an example of creating a service, and a client that accesses that service, see [How to: Create a Duplex Contract](./feature-details/how-to-create-a-duplex-contract.md) and [How to: Access Services with a Duplex Contract](./feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="55ca9-200">作業用サンプルについては、「[二重](./samples/duplex.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-200">For a working sample, see [Duplex](./samples/duplex.md).</span></span> <span data-ttu-id="55ca9-201">双方向コントラクトの使用の詳細については、「[双方向サービス](./feature-details/duplex-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-201">For more information about issues using duplex contracts, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="55ca9-202">サービスは、双方向メッセージを受信すると、その受信メッセージの `ReplyTo` 要素を参照して応答の送信先を決定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-202">When a service receives a duplex message, it looks at the `ReplyTo` element in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="55ca9-203">メッセージの受信に使用するチャネルがセキュリティで保護されていない場合、信頼関係のないクライアントが対象コンピューターの `ReplyTo` を使用して悪意のあるメッセージを送信し、その対象コンピューターのサービス拒否 (DOS: Denial Of Service) を引き起こすおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-203">If the channel that is used to receive the message is not secured, then an untrusted client could send a malicious message with a target machine's `ReplyTo`, leading to a denial of service (DOS) of that target machine.</span></span>  
  
##### <a name="out-and-ref-parameters"></a><span data-ttu-id="55ca9-204">Out パラメーターと Ref パラメーター</span><span class="sxs-lookup"><span data-stu-id="55ca9-204">Out and Ref Parameters</span></span>  

 <span data-ttu-id="55ca9-205">ほとんどの場合、`in` パラメーター (Visual Basic では `ByVal`) と `out` および `ref` パラメーター (Visual Basic では `ByRef`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-205">In most cases, you can use `in` parameters (`ByVal` in Visual Basic) and `out` and `ref` parameters (`ByRef` in Visual Basic).</span></span> <span data-ttu-id="55ca9-206">`out` パラメーターと `ref` パラメーターは、操作からデータが返されることを示すため、操作シグネチャが `void` を返す場合でも、次のような操作シグネチャによって要求/応答操作が必要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-206">Because both `out` and `ref` parameters indicate that data is returned from an operation, an operation signature such as the following specifies that a request/reply operation is required even though the operation signature returns `void`.</span></span>  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 <span data-ttu-id="55ca9-207">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-207">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 <span data-ttu-id="55ca9-208">唯一の例外は、シグネチャに特定の構造体が含まれている場合です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-208">The only exceptions are those cases in which your signature has a particular structure.</span></span> <span data-ttu-id="55ca9-209">たとえば、<xref:System.ServiceModel.NetMsmqBinding> バインディングを使用してクライアントと通信できるのは、操作の宣言に使用されたメソッドが `void` を返す場合だけです。戻り値、`ref` パラメーター、または `out` パラメーターのいずれであるかに関係なく、出力値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-209">For example, you can use the <xref:System.ServiceModel.NetMsmqBinding> binding to communicate with clients only if the method used to declare an operation returns `void`; there can be no output value, whether it is a return value, `ref`, or `out` parameter.</span></span>  
  
 <span data-ttu-id="55ca9-210">また、`out` パラメーターまたは `ref` パラメーターを使用する場合、操作には基になる応答メッセージが必要です。このメッセージが変更されたオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-210">In addition, using `out` or `ref` parameters requires that the operation have an underlying response message to carry back the modified object.</span></span> <span data-ttu-id="55ca9-211">操作が一方向操作の場合、実行時に <xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-211">If your operation is a one-way operation, an <xref:System.InvalidOperationException> exception is thrown at runtime.</span></span>  
  
### <a name="specify-message-protection-level-on-the-contract"></a><span data-ttu-id="55ca9-212">コントラクトでのメッセージ保護レベルの指定</span><span class="sxs-lookup"><span data-stu-id="55ca9-212">Specify Message Protection Level on the Contract</span></span>  

 <span data-ttu-id="55ca9-213">コントラクトの設計時に、コントラクトを実装するサービスのメッセージ保護レベルも決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-213">When designing your contract, you must also decide the message protection level of services that implement your contract.</span></span> <span data-ttu-id="55ca9-214">これは、メッセージ セキュリティをコントラクトのエンドポイントのバインディングに適用する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-214">This is necessary only if message security is applied to the binding in the contract's endpoint.</span></span> <span data-ttu-id="55ca9-215">バインディングのセキュリティが無効になっている場合 (つまり、システム指定のバインディングで <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> の値が <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType> に設定されている場合)、コントラクトのメッセージ保護レベルを決定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-215">If the binding has security turned off (that is, if the system-provided binding sets the <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> to the value <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) then you do not have to decide on the message protection level for the contract.</span></span> <span data-ttu-id="55ca9-216">ほとんどの場合、メッセージ レベルのセキュリティが適用されたシステム指定のバインディングは、十分な保護レベルを備えているため、操作ごとまたはメッセージごとに保護レベルを検討する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-216">In most cases, system-provided bindings with message-level security applied provide a sufficient protection level and you do not have to consider the protection level for each operation or for each message.</span></span>  
  
 <span data-ttu-id="55ca9-217">保護レベルは、サービスをサポートするメッセージ (またはメッセージ部分) が署名されるのか、署名および暗号化されるのか、または署名と暗号化なしで送信されるのかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-217">The protection level is a value that specifies whether the messages (or message parts) that support a service are signed, signed and encrypted, or sent without signatures or encryption.</span></span> <span data-ttu-id="55ca9-218">保護レベルは、さまざまなスコープ (サービス レベル、特定の操作、その操作内のメッセージ、またはメッセージ部分) で設定できます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-218">The protection level can be set at various scopes: At the service level, for a particular operation, for a message within that operation, or a message part.</span></span> <span data-ttu-id="55ca9-219">あるスコープで設定された値は、明示的にオーバーライドしない限り、そのスコープよりも小さなスコープの既定値になります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-219">Values set at one scope become the default value for smaller scopes unless explicitly overridden.</span></span> <span data-ttu-id="55ca9-220">コントラクトに必要とされる最小限の保護レベルをバインド構成で提供できない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-220">If a binding configuration cannot provide the required minimum protection level for the contract, an exception is thrown.</span></span> <span data-ttu-id="55ca9-221">保護レベルの値がコントラクトで明示的に設定されていない場合、バインディングのメッセージ セキュリティが有効であれば、バインド構成によってすべてのメッセージの保護レベルが制御されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-221">And when no protection level values are explicitly set on the contract, the binding configuration controls the protection level for all messages if the binding has message security.</span></span> <span data-ttu-id="55ca9-222">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-222">This is the default behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55ca9-223">一般に、コントラクトのさまざまなスコープを完全な保護レベルである <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> よりも下のレベルに明示的に設定するかどうかは、パフォーマンスの向上と引き換えに、ある程度のセキュリティで妥協できるかどうかという判断によって決まります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-223">Deciding whether to explicitly set various scopes of a contract to less than the full protection level of <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> is generally a decision that trades some degree of security for increased performance.</span></span> <span data-ttu-id="55ca9-224">このような場合、操作および操作で交換するデータの価値に焦点を絞って判断を下す必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-224">In these cases, your decisions must revolve around your operations and the value of the data they exchange.</span></span> <span data-ttu-id="55ca9-225">詳細については、「[サービスのセキュリティ保護](securing-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-225">For more information, see [Securing Services](securing-services.md).</span></span>  
  
 <span data-ttu-id="55ca9-226">たとえば、次のコード例では、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> も、コントラクトの <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> プロパティも設定していません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-226">For example, the following code example does not set either the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> or the <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> property on the contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 <span data-ttu-id="55ca9-227">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-227">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 <span data-ttu-id="55ca9-228">既定の `ISampleService` (既定の <xref:System.ServiceModel.WSHttpBinding> は <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>) を使用するエンドポイントの <xref:System.ServiceModel.SecurityMode.Message> 実装とやり取りする場合は、暗号化と署名が既定の保護レベルであるため、すべてのメッセージが暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-228">When interacting with an `ISampleService` implementation in an endpoint with a default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>), all messages are encrypted and signed because this is the default protection level.</span></span> <span data-ttu-id="55ca9-229">ただし、既定の `ISampleService` (既定の <xref:System.ServiceModel.BasicHttpBinding> は <xref:System.ServiceModel.SecurityMode>) を使用して <xref:System.ServiceModel.SecurityMode.None> サービスを使用すると、すべてのメッセージがテキストとして送信されます。これは、このバインディングにはセキュリティがないため、保護レベルが無視されるためです (つまり、メッセージの暗号化も署名も行われません)。</span><span class="sxs-lookup"><span data-stu-id="55ca9-229">However, when an `ISampleService` service is used with a default <xref:System.ServiceModel.BasicHttpBinding> (the default <xref:System.ServiceModel.SecurityMode>, which is <xref:System.ServiceModel.SecurityMode.None>), all messages are sent as text because there is no security for this binding and so the protection level is ignored (that is, the messages are neither encrypted nor signed).</span></span> <span data-ttu-id="55ca9-230"><xref:System.ServiceModel.SecurityMode> を <xref:System.ServiceModel.SecurityMode.Message> に変更すると、これがこのバインディングの既定の保護レベルになるため、これらのメッセージは暗号化および署名されるようになります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-230">If the <xref:System.ServiceModel.SecurityMode> was changed to <xref:System.ServiceModel.SecurityMode.Message>, then these messages would be encrypted and signed (because that would now be the binding's default protection level).</span></span>  
  
 <span data-ttu-id="55ca9-231">コントラクトの保護要件を明示的に指定または調整する場合は、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティ (またはより小さなスコープの `ProtectionLevel` プロパティのいずれか) をサービス コントラクトに必要なレベルに設定します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-231">If you want to explicitly specify or adjust the protection requirements for your contract, set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property (or any of the `ProtectionLevel` properties at a smaller scope) to the level your service contract requires.</span></span> <span data-ttu-id="55ca9-232">この場合、明示的な設定を使用するには、使用するスコープに少なくともその設定をサポートするバインディングが必要です。</span><span class="sxs-lookup"><span data-stu-id="55ca9-232">In this case, using an explicit setting requires the binding to support that setting at a minimum for the scope used.</span></span> <span data-ttu-id="55ca9-233">たとえば、次のコード例では、<xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 操作の `GetGuid` の値を明示的に指定しています。</span><span class="sxs-lookup"><span data-stu-id="55ca9-233">For example, the following code example specifies one <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> value explicitly, for the `GetGuid` operation.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 <span data-ttu-id="55ca9-234">次のコードは同等の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="55ca9-234">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 <span data-ttu-id="55ca9-235">この `IExplicitProtectionLevelSampleService` コントラクトを実装し、既定の <xref:System.ServiceModel.WSHttpBinding> (既定の <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> は <xref:System.ServiceModel.SecurityMode.Message>) を使用するエンドポイントを持つサービスの動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-235">A service that implements this `IExplicitProtectionLevelSampleService` contract and has an endpoint that uses the default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>) has the following behavior:</span></span>  
  
- <span data-ttu-id="55ca9-236">`GetString` 操作のメッセージは、暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-236">The `GetString` operation messages are encrypted and signed.</span></span>  
  
- <span data-ttu-id="55ca9-237">`GetInt` 操作のメッセージは、暗号化も署名もされない (プレーン) テキストとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-237">The `GetInt` operation messages are sent as unencrypted and unsigned (that is, plain) text.</span></span>  
  
- <span data-ttu-id="55ca9-238">`GetGuid` 操作の <xref:System.Guid?displayProperty=nameWithType> は、暗号化および署名されたメッセージで返されます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-238">The `GetGuid` operation <xref:System.Guid?displayProperty=nameWithType> is returned in a message that is encrypted and signed.</span></span>  
  
 <span data-ttu-id="55ca9-239">保護レベルとその使用方法の詳細については、「[保護レベルの理解](understanding-protection-level.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-239">For more information about protection levels and how to use them, see [Understanding Protection Level](understanding-protection-level.md).</span></span> <span data-ttu-id="55ca9-240">セキュリティの詳細については、「[サービスのセキュリティ保護](securing-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-240">For more information about security, see [Securing Services](securing-services.md).</span></span>  
  
##### <a name="other-operation-signature-requirements"></a><span data-ttu-id="55ca9-241">操作シグネチャのその他の要件</span><span class="sxs-lookup"><span data-stu-id="55ca9-241">Other Operation Signature Requirements</span></span>  

 <span data-ttu-id="55ca9-242">アプリケーションの一部の機能では、特定の種類の操作シグネチャを必要とします。</span><span class="sxs-lookup"><span data-stu-id="55ca9-242">Some application features require a particular kind of operation signature.</span></span> <span data-ttu-id="55ca9-243">たとえば、<xref:System.ServiceModel.NetMsmqBinding> バインディングは、永続的なサービスとクライアントをサポートします。永続的なサービスとクライアントでは、通信の途中でアプリケーションを再起動し、メッセージを失うことなく、アプリケーションが中止された場所を検出できます </span><span class="sxs-lookup"><span data-stu-id="55ca9-243">For example, the <xref:System.ServiceModel.NetMsmqBinding> binding supports durable services and clients, in which an application can restart in the middle of communication and pick up where it left off without missing any messages.</span></span> <span data-ttu-id="55ca9-244">(詳細については、[WCF のキュー](./feature-details/queues-in-wcf.md)に関する記事を参照してください。)ただし、永続的操作では、`in` パラメーターを 1 つしか受け取ることができず、戻り値を持つこともできません。</span><span class="sxs-lookup"><span data-stu-id="55ca9-244">(For more information, see [Queues in WCF](./feature-details/queues-in-wcf.md).) However, durable operations must take only one `in` parameter and have no return value.</span></span>  
  
 <span data-ttu-id="55ca9-245">もう 1 つの例として、操作における <xref:System.IO.Stream> 型の使用が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="55ca9-245">Another example is the use of <xref:System.IO.Stream> types in operations.</span></span> <span data-ttu-id="55ca9-246"><xref:System.IO.Stream> パラメーターにはメッセージの本文全体が含まれるため、入力または出力 (つまり、`ref` パラメーター、`out` パラメーター、または戻り値) が <xref:System.IO.Stream> 型である場合、操作で指定された入力または出力に限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-246">Because the <xref:System.IO.Stream> parameter includes the entire message body, if an input or an output (that is, `ref` parameter, `out` parameter, or return value) is of type <xref:System.IO.Stream>, then it must be the only input or output specified in your operation.</span></span> <span data-ttu-id="55ca9-247">また、パラメーターまたは戻り値の型は <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>、<xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType> のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-247">In addition, the parameter or return type must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, or <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="55ca9-248">ストリームの詳細については、「[大規模データとストリーミング](./feature-details/large-data-and-streaming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca9-248">For more information about streams, see [Large Data and Streaming](./feature-details/large-data-and-streaming.md).</span></span>  
  
##### <a name="names-namespaces-and-obfuscation"></a><span data-ttu-id="55ca9-249">名前、名前空間、および隠ぺい</span><span class="sxs-lookup"><span data-stu-id="55ca9-249">Names, Namespaces, and Obfuscation</span></span>  

 <span data-ttu-id="55ca9-250">コントラクトおよび操作の定義内の .NET 型の名前や名前空間は、コントラクトが WSDL に変換されるとき、およびコントラクト メッセージが作成および送信されるときに重要になります。</span><span class="sxs-lookup"><span data-stu-id="55ca9-250">The names and namespaces of the .NET types in the definition of contracts and operations are significant when contracts are converted into WSDL and when contract messages are created and sent.</span></span> <span data-ttu-id="55ca9-251">したがって、サービス コントラクトの名前と名前空間は、`Name`、`Namespace`、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute> などの、すべてのサポート対象コントラクト属性や、他のコントラクト属性の <xref:System.Runtime.Serialization.DataContractAttribute> プロパティと <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを使用して明示的に設定することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55ca9-251">Therefore, it is strongly recommended that service contract names and namespaces are explicitly set using the `Name` and `Namespace` properties of all supporting contract attributes such as the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>, and other contract attributes.</span></span>  
  
 <span data-ttu-id="55ca9-252">この 1 つの結果として、名前と名前空間が明示的に設定されていない場合、アセンブリで IL 難読化を使用すると、コントラクトの型名と名前空間が変更され、その結果、WSDL が変更され、通常はネットワークでのメッセージ交換に失敗します。</span><span class="sxs-lookup"><span data-stu-id="55ca9-252">One result of this is that if the names and namespaces are not explicitly set, the use of IL obfuscation on the assembly alters the contract type names and namespaces and results in modified WSDL and wire exchanges that typically fail.</span></span> <span data-ttu-id="55ca9-253">コントラクトの名前と名前空間を明示的に設定せずに難読化を使用する場合は、<xref:System.Reflection.ObfuscationAttribute> 属性と <xref:System.Reflection.ObfuscateAssemblyAttribute> 属性を使用して、コントラクトの型名と名前空間が変更されないようにします。</span><span class="sxs-lookup"><span data-stu-id="55ca9-253">If you do not set the contract names and namespaces explicitly but do intend to use obfuscation, use the <xref:System.Reflection.ObfuscationAttribute> and <xref:System.Reflection.ObfuscateAssemblyAttribute> attributes to prevent the modification of the contract type names and namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ca9-254">関連項目</span><span class="sxs-lookup"><span data-stu-id="55ca9-254">See also</span></span>

- [<span data-ttu-id="55ca9-255">方法: 要求/応答コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="55ca9-255">How to: Create a Request-Reply Contract</span></span>](./feature-details/how-to-create-a-request-reply-contract.md)
- [<span data-ttu-id="55ca9-256">方法: 一方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="55ca9-256">How to: Create a One-Way Contract</span></span>](./feature-details/how-to-create-a-one-way-contract.md)
- [<span data-ttu-id="55ca9-257">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="55ca9-257">How to: Create a Duplex Contract</span></span>](./feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="55ca9-258">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="55ca9-258">Specifying Data Transfer in Service Contracts</span></span>](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [<span data-ttu-id="55ca9-259">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="55ca9-259">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="55ca9-260">セッションの使用</span><span class="sxs-lookup"><span data-stu-id="55ca9-260">Using Sessions</span></span>](using-sessions.md)
- [<span data-ttu-id="55ca9-261">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="55ca9-261">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="55ca9-262">Reliable Service</span><span class="sxs-lookup"><span data-stu-id="55ca9-262">Reliable Services</span></span>](reliable-services.md)
- [<span data-ttu-id="55ca9-263">サービスとトランザクション</span><span class="sxs-lookup"><span data-stu-id="55ca9-263">Services and Transactions</span></span>](services-and-transactions.md)
