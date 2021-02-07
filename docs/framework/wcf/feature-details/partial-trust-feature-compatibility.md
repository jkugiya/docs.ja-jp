---
description: '詳細情報: 部分信頼機能の互換性'
title: 部分信頼機能の互換性
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 470cedde3eb38508feb1c2950f7f504390914834
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733529"
---
# <a name="partial-trust-feature-compatibility"></a><span data-ttu-id="917c5-103">部分信頼機能の互換性</span><span class="sxs-lookup"><span data-stu-id="917c5-103">Partial Trust Feature Compatibility</span></span>

<span data-ttu-id="917c5-104">Windows Communication Foundation (WCF) は、部分的に信頼された環境で実行される場合に、限られた機能のサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="917c5-104">Windows Communication Foundation (WCF) supports a limited subset of functionality when running in a partially-trusted environment.</span></span> <span data-ttu-id="917c5-105">部分信頼でサポートされる機能は、「 [Supported Deployment Scenarios](supported-deployment-scenarios.md) 」のトピックで説明される特定のシナリオを念頭にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="917c5-105">The features supported in partial trust are designed around a specific set of scenarios as described in the [Supported Deployment Scenarios](supported-deployment-scenarios.md) topic.</span></span>  
  
## <a name="minimum-permission-requirements"></a><span data-ttu-id="917c5-106">最小のアクセス許可の要件</span><span class="sxs-lookup"><span data-stu-id="917c5-106">Minimum Permission Requirements</span></span>  

 <span data-ttu-id="917c5-107">WCF では、次の標準の名前付きアクセス許可セットのいずれかで実行されるアプリケーションの機能のサブセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="917c5-107">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>  
  
- <span data-ttu-id="917c5-108">中程度の信頼アクセス許可</span><span class="sxs-lookup"><span data-stu-id="917c5-108">Medium Trust permissions</span></span>  
  
- <span data-ttu-id="917c5-109">インターネット ゾーン アクセス許可</span><span class="sxs-lookup"><span data-stu-id="917c5-109">Internet Zone permissions</span></span>  
  
 <span data-ttu-id="917c5-110">部分的に信頼されたアプリケーションで、より制限の厳しいアクセス許可を持つ WCF を使用しようとすると、実行時にセキュリティ例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-110">Attempting to use WCF in partially-trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>  
  
## <a name="contracts"></a><span data-ttu-id="917c5-111">コントラクト</span><span class="sxs-lookup"><span data-stu-id="917c5-111">Contracts</span></span>  

 <span data-ttu-id="917c5-112">部分信頼で実行される場合、コントラクトには次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-112">Contracts are subject to the following restrictions when running under partial trust:</span></span>  
  
- <span data-ttu-id="917c5-113">`[ServiceContract]` インターフェイスを実装するサービス クラスは、 `public` であること、および `public` コンストラクターを持っていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="917c5-113">The service class that implements the `[ServiceContract]` interface must be `public` and have a `public` constructor.</span></span> <span data-ttu-id="917c5-114">このクラスで `[OperationContract]` メソッドを定義する場合、それらも `public`である必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-114">If it defines `[OperationContract]` methods, these must be `public`.</span></span> <span data-ttu-id="917c5-115">代わりに `[ServiceContract]` インターフェイスを実装する場合は、 `private`インターフェイスが `[ServiceContract]` であれば、それらのメソッド実装は明示的でも `public`でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="917c5-115">If it instead implements a `[ServiceContract]` interface, those method implementations can be explicit or `private`, provided that the `[ServiceContract]` interface is `public`.</span></span>  
  
- <span data-ttu-id="917c5-116">`[ServiceKnownType]` 属性を使用するときは、指定するメソッドは `public`である必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-116">When using the `[ServiceKnownType]` attribute, the method specified must be `public`.</span></span>  
  
- <span data-ttu-id="917c5-117">`[MessageContract]` クラスとそのメンバーは、 `public`である場合があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-117">`[MessageContract]` classes and their members can be `public`.</span></span> <span data-ttu-id="917c5-118">`[MessageContract]` クラスがアプリケーション アセンブリで定義されている場合は、 `internal` であり、 `internal` メンバーを持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-118">If the `[MessageContract]` class is defined in the application assembly it can be `internal` and have `internal` members.</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="917c5-119">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="917c5-119">System-Provided Bindings</span></span>  

 <span data-ttu-id="917c5-120">部分信頼環境では、 <xref:System.ServiceModel.BasicHttpBinding> と <xref:System.ServiceModel.WebHttpBinding> が完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="917c5-120">The <xref:System.ServiceModel.BasicHttpBinding> and <xref:System.ServiceModel.WebHttpBinding> are fully supported in a partial trust environment.</span></span> <span data-ttu-id="917c5-121"><xref:System.ServiceModel.WSHttpBinding> は、トランスポート セキュリティ モードでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="917c5-121">The <xref:System.ServiceModel.WSHttpBinding> is supported for Transport security mode only.</span></span>  
  
 <span data-ttu-id="917c5-122"><xref:System.ServiceModel.NetTcpBinding>、 <xref:System.ServiceModel.NetNamedPipeBinding>、または <xref:System.ServiceModel.NetMsmqBinding>など、HTTP 以外のトランスポートを使用するバインディングは、部分信頼環境で実行される場合はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-122">Bindings that use transports other than HTTP, such as the <xref:System.ServiceModel.NetTcpBinding>, the <xref:System.ServiceModel.NetNamedPipeBinding>, or the <xref:System.ServiceModel.NetMsmqBinding>, are not supported when running in a partial trust environment.</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="917c5-123">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="917c5-123">Custom Bindings</span></span>  

 <span data-ttu-id="917c5-124">部分信頼環境ではカスタム バインディングの作成と使用が可能ですが、このセクションに示した制限に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-124">Custom bindings can be created and used in a partial trust environment, but must follow the restrictions specified in this section.</span></span>  
  
### <a name="transports"></a><span data-ttu-id="917c5-125">トランスポート</span><span class="sxs-lookup"><span data-stu-id="917c5-125">Transports</span></span>  

 <span data-ttu-id="917c5-126">使用できるトランスポート バインド要素は、 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> と <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>に限られます。</span><span class="sxs-lookup"><span data-stu-id="917c5-126">The only allowed transport binding elements are <xref:System.ServiceModel.Channels.HttpTransportBindingElement> and <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
### <a name="encoders"></a><span data-ttu-id="917c5-127">エンコーダー</span><span class="sxs-lookup"><span data-stu-id="917c5-127">Encoders</span></span>  

 <span data-ttu-id="917c5-128">次のエンコーダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="917c5-128">The following encoders are allowed:</span></span>  
  
- <span data-ttu-id="917c5-129">テキスト エンコーダー (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="917c5-129">The text encoder (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="917c5-130">バイナリ エンコーダー (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="917c5-130">The binary encoder (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="917c5-131">Web メッセージ エンコーダー (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="917c5-131">The Web Message encoder (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).</span></span>  
  
 <span data-ttu-id="917c5-132">MTOM (Message Transmission Optimization Mechanism) エンコーダーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-132">The Message Transmission Optimization Mechanism (MTOM) encoders are not supported.</span></span>  
  
### <a name="security"></a><span data-ttu-id="917c5-133">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="917c5-133">Security</span></span>  

 <span data-ttu-id="917c5-134">部分的に信頼されたアプリケーションでは、WCF のトランスポートレベルのセキュリティ機能を使用して、通信をセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="917c5-134">Partially-trusted applications can use WCF's transport-level security features for securing their communication.</span></span> <span data-ttu-id="917c5-135">メッセージ レベルのセキュリティはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-135">Message-level security is not supported.</span></span> <span data-ttu-id="917c5-136">メッセージ レベルのセキュリティを使用するようにバインディングを構成すると、実行時に例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="917c5-136">Configuring a binding to use message-level security results in an exception at runtime.</span></span>  
  
### <a name="unsupported-bindings"></a><span data-ttu-id="917c5-137">サポートされないバインディング</span><span class="sxs-lookup"><span data-stu-id="917c5-137">Unsupported Bindings</span></span>  

 <span data-ttu-id="917c5-138">信頼できるメッセージング、トランザクション、またはメッセージ レベルのセキュリティを使用するバインディングはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-138">Bindings that use reliable messaging, transactions, or message-level security are not supported.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="917c5-139">シリアル化</span><span class="sxs-lookup"><span data-stu-id="917c5-139">Serialization</span></span>  

 <span data-ttu-id="917c5-140">部分信頼環境では、 <xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Xml.Serialization.XmlSerializer> の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="917c5-140">Both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported in a partial trust environment.</span></span> <span data-ttu-id="917c5-141">ただし、 <xref:System.Runtime.Serialization.DataContractSerializer> の使用は、次の条件に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-141">However, use of the <xref:System.Runtime.Serialization.DataContractSerializer> is subject to the following conditions:</span></span>  
  
- <span data-ttu-id="917c5-142">シリアル化可能なすべての `[DataContract]` 型は `public`である必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-142">All serializable `[DataContract]` types must be `public`.</span></span>  
  
- <span data-ttu-id="917c5-143">`[DataMember]` 型にあるシリアル化可能なすべての `[DataContract]` フィールドまたはプロパティは、パブリックで読み書き可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-143">All serializable `[DataMember]` fields or properties in a `[DataContract]` type must be public and read/write.</span></span> <span data-ttu-id="917c5-144">部分的に信頼されたアプリケーションで WCF を実行する場合、 [読み取り専用](https://go.microsoft.com/fwlink/?LinkID=98854) フィールドのシリアル化と逆シリアル化はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-144">The serialization and deserialization of [readonly](https://go.microsoft.com/fwlink/?LinkID=98854) fields is not supported when running WCF in a partially-trusted application.</span></span>  
  
- <span data-ttu-id="917c5-145">部分信頼環境では、 `[Serializable]`/ISerializable プログラミング モデルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-145">The `[Serializable]`/ISerializable programming model is not supported in a partial trust environment.</span></span>  
  
- <span data-ttu-id="917c5-146">既知の型はコード内、またはマシン レベルの構成 (machine.config) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-146">Known types must be specified in code or machine-level configuration (machine.config).</span></span> <span data-ttu-id="917c5-147">既知の型はセキュリティ上の理由からアプリケーション レベルの構成では指定できません。</span><span class="sxs-lookup"><span data-stu-id="917c5-147">Known types cannot be specified in application-level configuration for security reasons.</span></span>  
  
- <span data-ttu-id="917c5-148"><xref:System.Runtime.Serialization.IObjectReference> を実装する型は、部分信頼環境では例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="917c5-148">Types that implement <xref:System.Runtime.Serialization.IObjectReference> throw an exception in a partially-trusted environment.</span></span>  
  
 <span data-ttu-id="917c5-149">部分信頼アプリケーションで [T:System.Runtime.Serialization.DataContractSerializer](partial-trust-best-practices.md) を安全に使用する場合のセキュリティ情報の詳細については、「 <xref:System.Runtime.Serialization.DataContractSerializer> 」のシリアル化のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c5-149">See the Serialization section in [Partial Trust Best Practices](partial-trust-best-practices.md) for more information about security when using <xref:System.Runtime.Serialization.DataContractSerializer> safely in a partially-trusted application.</span></span>  
  
### <a name="collection-types"></a><span data-ttu-id="917c5-150">コレクション型</span><span class="sxs-lookup"><span data-stu-id="917c5-150">Collection Types</span></span>  

 <span data-ttu-id="917c5-151">コレクション型の中には、 <xref:System.Collections.Generic.IEnumerable%601> と <xref:System.Collections.IEnumerable>の両方を実装するものがあります。</span><span class="sxs-lookup"><span data-stu-id="917c5-151">Some collection types implement both <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="917c5-152">たとえば、 <xref:System.Collections.Generic.ICollection%601>を実装する型がこれに当たります。</span><span class="sxs-lookup"><span data-stu-id="917c5-152">Examples include types that implement <xref:System.Collections.Generic.ICollection%601>.</span></span> <span data-ttu-id="917c5-153">このような型では、 `public` の `GetEnumerator()`な実装と、 `GetEnumerator()`の明示的な実装を実装できます。</span><span class="sxs-lookup"><span data-stu-id="917c5-153">Such types can implement a `public` implementation of `GetEnumerator()`, and an explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="917c5-154">この場合、 <xref:System.Runtime.Serialization.DataContractSerializer> は `public` の `GetEnumerator()`な実装を呼び出し、 `GetEnumerator()`の明示的な実装は呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="917c5-154">In this case, <xref:System.Runtime.Serialization.DataContractSerializer> invokes the `public` implementation of `GetEnumerator()`, and not the explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="917c5-155">`GetEnumerator()` 実装のいずれも `public` ではなく、すべてが明示的な実装である場合、 <xref:System.Runtime.Serialization.DataContractSerializer> は `IEnumerable.GetEnumerator()`を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="917c5-155">If none of the `GetEnumerator()` implementations are `public` and all are explicit implementations, then <xref:System.Runtime.Serialization.DataContractSerializer> invokes `IEnumerable.GetEnumerator()`.</span></span>  
  
 <span data-ttu-id="917c5-156">WCF が部分信頼環境で実行されている場合、コレクション型の場合、実装のいずれもでない場合、または明示的なインターフェイスの実装でない場合は、 `GetEnumerator()` `public` セキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="917c5-156">For collection types when WCF is running in a partial trust environment, if none of the `GetEnumerator()` implementations are `public`, or none of them are explicit interface implementations, then a security exception is thrown.</span></span>  
  
### <a name="netdatacontractserializer"></a><span data-ttu-id="917c5-157">NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="917c5-157">NetDataContractSerializer</span></span>  

 <span data-ttu-id="917c5-158">部分信頼の場合、 <xref:System.Collections.Generic.List%601>、 <xref:System.Collections.ArrayList>、 <xref:System.Collections.Generic.Dictionary%602> 、および <xref:System.Collections.Hashtable> などの、.NET Framework コレクション型の多くは、 <xref:System.Runtime.Serialization.NetDataContractSerializer> によってサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-158">Many .NET Framework collection types such as <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.Hashtable> are not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span> <span data-ttu-id="917c5-159">これらの型には `[Serializable]` 属性セットがあり、シリアル化のセクションで説明したように、この属性は部分信頼ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-159">These types have the `[Serializable]` attribute set, and as stated previously in the Serialization section, this attribute is not supported in partial trust.</span></span> <span data-ttu-id="917c5-160"><xref:System.Runtime.Serialization.DataContractSerializer> はコレクションを特殊な方法で扱うため、この制限を回避できますが、 <xref:System.Runtime.Serialization.NetDataContractSerializer> には、この制限の適用を避けるメカニズムはありません。</span><span class="sxs-lookup"><span data-stu-id="917c5-160">The <xref:System.Runtime.Serialization.DataContractSerializer> treats collections in a special way and is thus able to get around this restriction, but the <xref:System.Runtime.Serialization.NetDataContractSerializer> has no such mechanism to circumvent this restriction.</span></span>  
  
 <span data-ttu-id="917c5-161"><xref:System.DateTimeOffset> 型は、部分信頼では <xref:System.Runtime.Serialization.NetDataContractSerializer> によってサポートされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-161">The <xref:System.DateTimeOffset> type is not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span>  
  
 <span data-ttu-id="917c5-162">部分信頼で実行するときは、( <xref:System.Runtime.Serialization.NetDataContractSerializer> メカニズムを使用して) <xref:System.Runtime.Serialization.SurrogateSelector> でサロゲートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="917c5-162">A surrogate cannot be used with the <xref:System.Runtime.Serialization.NetDataContractSerializer> (using the <xref:System.Runtime.Serialization.SurrogateSelector> mechanism) when running in partial trust.</span></span> <span data-ttu-id="917c5-163">この制限は、シリアル化ではなく、サロゲートの使用に適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="917c5-163">Note that this restriction applies to using a surrogate, not to serializing it.</span></span>  
  
## <a name="enabling-common-behaviors-to-run"></a><span data-ttu-id="917c5-164">実行する共通動作の有効化</span><span class="sxs-lookup"><span data-stu-id="917c5-164">Enabling Common Behaviors to Run</span></span>  

 <span data-ttu-id="917c5-165">構成ファイルのセクションに追加された属性 (APTCA) でマークされていないサービスまたはエンドポイントの動作 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) は、アプリケーションが部分信頼環境で実行されている場合は実行されず、この発生時に例外がスローされることはありません。</span><span class="sxs-lookup"><span data-stu-id="917c5-165">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment and no exception is thrown when this occurs.</span></span> <span data-ttu-id="917c5-166">共通動作を強制的に実行するには、次のいずれかを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-166">To enforce the running of common behaviors, you must do one of the following options:</span></span>  
  
- <span data-ttu-id="917c5-167">共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="917c5-167">Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a partial trust application.</span></span> <span data-ttu-id="917c5-168">APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。</span><span class="sxs-lookup"><span data-stu-id="917c5-168">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running.</span></span> <span data-ttu-id="917c5-169">.</span><span class="sxs-lookup"><span data-stu-id="917c5-169">.</span></span>  
  
- <span data-ttu-id="917c5-170">アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="917c5-170">Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a partial trust environment.</span></span> <span data-ttu-id="917c5-171">ユーザーがこのような変更を行うことができる場合、動作は実行されず、例外もスローされません。</span><span class="sxs-lookup"><span data-stu-id="917c5-171">If they can do so, the behavior does not run and no exception is thrown.</span></span> <span data-ttu-id="917c5-172">これを確認するには、Caspol.exe を使用した **levelfinal** オプション [ (コードアクセスセキュリティポリシーツール)](../../tools/caspol-exe-code-access-security-policy-tool.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c5-172">To ensure this, see the **levelfinal** option using [Caspol.exe (Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
 <span data-ttu-id="917c5-173">一般的な動作の例については、「 [方法: 企業内のエンドポイントをロックダウンする](../extending/how-to-lock-down-endpoints-in-the-enterprise.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c5-173">For an example of a common behavior, see [How to: Lock Down Endpoints in the Enterprise](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="917c5-174">構成</span><span class="sxs-lookup"><span data-stu-id="917c5-174">Configuration</span></span>  

 <span data-ttu-id="917c5-175">1つの例外を除き、部分信頼コードは、ローカルファイルの WCF 構成セクションのみを読み込むことができ `app.config` ます。</span><span class="sxs-lookup"><span data-stu-id="917c5-175">With one exception, partially-trusted code can only load WCF configuration sections in the local `app.config` file.</span></span> <span data-ttu-id="917c5-176">machine.config またはルート web.config ファイル内の WCF セクションを参照する WCF 構成セクションを読み込むには、ConfigurationPermission (無制限) が必要です。</span><span class="sxs-lookup"><span data-stu-id="917c5-176">To load WCF configuration sections that reference WCF sections in machine.config or in a root web.config file requires ConfigurationPermission(Unrestricted).</span></span> <span data-ttu-id="917c5-177">このアクセス許可がない場合、ローカル構成ファイルの外部にある WCF 構成セクション (動作、バインド) を参照すると、構成の読み込み時に例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="917c5-177">Without this permission, references to WCF configuration sections (behaviors, bindings) outside of the local configuration file results in an exception when the configuration is loaded.</span></span>  
  
 <span data-ttu-id="917c5-178">例外は、このトピックのシリアル化のセクションで説明したように、シリアル化の既知の型の構成です。</span><span class="sxs-lookup"><span data-stu-id="917c5-178">The one exception is known-type configuration for serialization, as described in the Serialization section of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="917c5-179">構成の拡張は、完全信頼で実行される場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="917c5-179">Configuration extensions are only supported when running under Full Trust.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="917c5-180">診断</span><span class="sxs-lookup"><span data-stu-id="917c5-180">Diagnostics</span></span>  
  
### <a name="event-logging"></a><span data-ttu-id="917c5-181">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="917c5-181">Event Logging</span></span>  

 <span data-ttu-id="917c5-182">部分信頼では、限定されたイベント ログがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="917c5-182">Limited event logging is supported under partial trust.</span></span> <span data-ttu-id="917c5-183">イベント ログには、サービス アクティベーション エラーおよびトレース/メッセージ ログ エラーのみが記録されます。</span><span class="sxs-lookup"><span data-stu-id="917c5-183">Only service activation faults and tracing/message logging failures are logged to the Event Log.</span></span> <span data-ttu-id="917c5-184">イベント ログに過剰な数のメッセージが書き込まれないように、ログに記録できるイベントの最大数は 5 つです。</span><span class="sxs-lookup"><span data-stu-id="917c5-184">The maximum number of events that can be logged by a process is 5, to avoid writing excessive messages to the Event Log.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="917c5-185">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="917c5-185">Message Logging</span></span>  

 <span data-ttu-id="917c5-186">WCF が部分信頼環境で実行されている場合、メッセージログは機能しません。</span><span class="sxs-lookup"><span data-stu-id="917c5-186">Message logging does not work when WCF is run in a partial trust environment.</span></span> <span data-ttu-id="917c5-187">部分信頼環境下で有効になっても、サービスのアクティブ化には失敗しませんが、メッセージはログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="917c5-187">If enabled under partial trust, it does not fail service activation, but no message is logged.</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="917c5-188">トレース</span><span class="sxs-lookup"><span data-stu-id="917c5-188">Tracing</span></span>  

 <span data-ttu-id="917c5-189">部分信頼環境で実行される場合、利用できるトレース機能には制限があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-189">Restricted tracing functionality is available when running in a partial trust environment.</span></span> <span data-ttu-id="917c5-190">`listeners`構成ファイルの <> 要素では、追加できる型は <xref:System.Diagnostics.TextWriterTraceListener> と新しいだけです <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="917c5-190">In the <`listeners`> element in the configuration file, the only types that you can add are <xref:System.Diagnostics.TextWriterTraceListener> and the new <xref:System.Diagnostics.EventSchemaTraceListener>.</span></span> <span data-ttu-id="917c5-191">標準の <xref:System.Diagnostics.XmlWriterTraceListener> を使用すると、ログが不完全または不正確になります。</span><span class="sxs-lookup"><span data-stu-id="917c5-191">Use of the standard <xref:System.Diagnostics.XmlWriterTraceListener> may result in incomplete or incorrect logs.</span></span>  
  
 <span data-ttu-id="917c5-192">次のトレース ソースがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="917c5-192">Supported trace sources are:</span></span>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <span data-ttu-id="917c5-193"><xref:System.IdentityModel.Claims>、<xref:System.IdentityModel.Policy>、<xref:System.IdentityModel.Selectors>、<xref:System.IdentityModel.Tokens>。</span><span class="sxs-lookup"><span data-stu-id="917c5-193"><xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, and <xref:System.IdentityModel.Tokens>.</span></span>  
  
 <span data-ttu-id="917c5-194">次のトレース ソースはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-194">The following trace sources are not supported:</span></span>  
  
- <span data-ttu-id="917c5-195">CardSpace</span><span class="sxs-lookup"><span data-stu-id="917c5-195">CardSpace</span></span>  
  
- <xref:System.IO.Log>  

- <span data-ttu-id="917c5-196">[System.servicemodel. 内部. TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span><span class="sxs-lookup"><span data-stu-id="917c5-196">[System.ServiceModel.Internal.TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span></span>
  
 <span data-ttu-id="917c5-197"><xref:System.Diagnostics.TraceOptions> 列挙体の次のメンバーは指定できません。</span><span class="sxs-lookup"><span data-stu-id="917c5-197">The following members of the <xref:System.Diagnostics.TraceOptions> enumeration should not be specified:</span></span>  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 <span data-ttu-id="917c5-198">部分信頼環境でトレースを使用する場合は、アプリケーションにトレース リスナーの出力を保存するための十分なアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="917c5-198">When using tracing in a partial trust environment, ensure that the application has sufficient permissions to store the output of the trace listener.</span></span> <span data-ttu-id="917c5-199">たとえば、 <xref:System.Diagnostics.TextWriterTraceListener> を使用してトレース出力をテキスト ファイルに書き込む場合は、アプリケーションにトレース ファイルを書き込むために必要な FileIOPermission があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="917c5-199">For example, when using the <xref:System.Diagnostics.TextWriterTraceListener> to write trace output to a text file, ensure that the application has the necessary FileIOPermission required to successfully write to the trace file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="917c5-200">重複したエラーによってトレースファイルのフラッディングを回避するために、最初のセキュリティエラーが発生した後、WCF はリソースまたはアクションのトレースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="917c5-200">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="917c5-201">リソースへのアクセスまたはアクションの実行が初めて行われようとしたとき、例外トレースはリソース アクセスの各失敗に対して、1 回だけ行われます。</span><span class="sxs-lookup"><span data-stu-id="917c5-201">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="wcf-service-host"></a><span data-ttu-id="917c5-202">WCF サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="917c5-202">WCF Service Host</span></span>  

 <span data-ttu-id="917c5-203">WCF サービスホストは部分信頼をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="917c5-203">WCF service host does not support partial trust.</span></span> <span data-ttu-id="917c5-204">部分信頼で WCF サービスを使用する場合は、サービスをビルドするために Visual Studio で WCF サービスライブラリプロジェクトテンプレートを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="917c5-204">If you want to use a WCF service in partial trust, do not use the WCF Service Library Project template in Visual Studio to build your service.</span></span> <span data-ttu-id="917c5-205">代わりに、wcf 部分信頼がサポートされている Web サーバーでサービスをホストできる WCF サービス Web サイトテンプレートを選択して、Visual Studio で新しい Web サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="917c5-205">Instead, create a new Web site in Visual Studio by choosing the WCF service Web site template, which can host the service in a Web server on which WCF partial trust is supported.</span></span>  
  
## <a name="other-limitations"></a><span data-ttu-id="917c5-206">他の制約</span><span class="sxs-lookup"><span data-stu-id="917c5-206">Other Limitations</span></span>  

  <span data-ttu-id="917c5-207">WCF は、一般に、ホスティングアプリケーションによって課せられるセキュリティ上の考慮事項に限定されます。</span><span class="sxs-lookup"><span data-stu-id="917c5-207">WCF is generally limited to the security considerations imposed upon it by the hosting application.</span></span> <span data-ttu-id="917c5-208">たとえば、WCF が XAML ブラウザーアプリケーション (XBAP) でホストされている場合、「 [Windows Presentation Foundation 部分信頼セキュリティ](/dotnet/desktop/wpf/wpf-partial-trust-security)」で説明されているように、xbap の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="917c5-208">For example, if WCF is hosted in a XAML Browser Application (XBAP), it is subject to XBAP limitations, as described in [Windows Presentation Foundation Partial Trust Security](/dotnet/desktop/wpf/wpf-partial-trust-security).</span></span>  
  
 <span data-ttu-id="917c5-209">次の追加機能は indigo2 が部分信頼環境で実行されていると有効になりません。</span><span class="sxs-lookup"><span data-stu-id="917c5-209">The following additional features are not enabled when running indigo2 in a partial trust environment:</span></span>  
  
- <span data-ttu-id="917c5-210">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="917c5-210">Windows Management Instrumentation (WMI)</span></span>  
  
- <span data-ttu-id="917c5-211">イベント ログは部分的にしか有効になりません (診断のセクションの説明を参照  )。</span><span class="sxs-lookup"><span data-stu-id="917c5-211">Event logging is only partially enabled (see discussion in **Diagnostics** section).</span></span>  
  
- <span data-ttu-id="917c5-212">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="917c5-212">Performance counters</span></span>  
  
 <span data-ttu-id="917c5-213">部分信頼環境でサポートされていない WCF 機能を使用すると、実行時に例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="917c5-213">Use of WCF features that are not supported in a partial trust environment may result in exceptions at runtime.</span></span>  
  
## <a name="unlisted-features"></a><span data-ttu-id="917c5-214">記載されていない機能</span><span class="sxs-lookup"><span data-stu-id="917c5-214">Unlisted Features</span></span>  

 <span data-ttu-id="917c5-215">部分信頼環境で利用できない情報やアクションを見つけ出す最善の方法は、リソースへのアクセスまたはアクションの実行を `try` ブロックの内側で試みて、エラーを `catch` することです。</span><span class="sxs-lookup"><span data-stu-id="917c5-215">The best way to discover that a piece of information or action is unavailable when running in a partial trust environment is to try to access the resource or do the action inside of a `try` block, and then `catch` the failure.</span></span> <span data-ttu-id="917c5-216">重複したエラーによってトレースファイルのフラッディングを回避するために、最初のセキュリティエラーが発生した後、WCF はリソースまたはアクションのトレースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="917c5-216">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="917c5-217">リソースへのアクセスまたはアクションの実行が初めて行われようとしたとき、例外トレースはリソース アクセスの各失敗に対して、1 回だけ行われます。</span><span class="sxs-lookup"><span data-stu-id="917c5-217">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917c5-218">関連項目</span><span class="sxs-lookup"><span data-stu-id="917c5-218">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="917c5-219">サポートされている配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="917c5-219">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)
- [<span data-ttu-id="917c5-220">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="917c5-220">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)
