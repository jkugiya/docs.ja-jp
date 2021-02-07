---
description: '詳細情報: 部分信頼のベストプラクティス'
title: 部分信頼のベスト プラクティス
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: abdc0fbbb84581b302bca8d514a5f8f5cc2703e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733555"
---
# <a name="partial-trust-best-practices"></a><span data-ttu-id="cd471-103">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="cd471-103">Partial Trust Best Practices</span></span>

<span data-ttu-id="cd471-104">このトピックでは、Windows Communication Foundation (WCF) を部分信頼環境で実行する場合のベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd471-104">This topic describes best practices when running Windows Communication Foundation (WCF) in a partial trust environment.</span></span>

## <a name="serialization"></a><span data-ttu-id="cd471-105">シリアル化</span><span class="sxs-lookup"><span data-stu-id="cd471-105">Serialization</span></span>

<span data-ttu-id="cd471-106">部分信頼アプリケーションで <xref:System.Runtime.Serialization.DataContractSerializer> を使用する場合は、次の方法を適用します。</span><span class="sxs-lookup"><span data-stu-id="cd471-106">Apply the following practices when using the <xref:System.Runtime.Serialization.DataContractSerializer> in a partially-trusted application.</span></span>

- <span data-ttu-id="cd471-107">すべてのシリアル化可能な型は、`[DataContract]` 属性で明示的にマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-107">All serializable types must be explicitly marked with the `[DataContract]` attribute.</span></span> <span data-ttu-id="cd471-108">次の手法は、部分信頼環境ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cd471-108">The following techniques are not supported in a partial trust environment:</span></span>

- <span data-ttu-id="cd471-109">シリアル化するクラスを <xref:System.SerializableAttribute> でマークする。</span><span class="sxs-lookup"><span data-stu-id="cd471-109">Marking classes to be serialized with the <xref:System.SerializableAttribute>.</span></span>

- <span data-ttu-id="cd471-110">クラスでシリアル化プロセスを制御できるように <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する。</span><span class="sxs-lookup"><span data-stu-id="cd471-110">Implementing the <xref:System.Runtime.Serialization.ISerializable> interface to allow a class to control its serialization process.</span></span>

### <a name="using-datacontractserializer"></a><span data-ttu-id="cd471-111">DataContractSerializer の使用</span><span class="sxs-lookup"><span data-stu-id="cd471-111">Using DataContractSerializer</span></span>

- <span data-ttu-id="cd471-112">`[DataContract]` 属性でマークされたすべての型は、パブリックである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-112">All types marked with the `[DataContract]` attribute must be public.</span></span> <span data-ttu-id="cd471-113">部分信頼環境では、非パブリック型はシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="cd471-113">Non-public types cannot be serialized in a partial trust environment.</span></span>

- <span data-ttu-id="cd471-114">シリアル化できる `[DataContract]` 型のすべての `[DataContract]` メンバーは、パブリックである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-114">All `[DataContract]` members in a serializable `[DataContract]` type must be public.</span></span> <span data-ttu-id="cd471-115">部分信頼環境では、非パブリック `[DataMember]` 型はシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="cd471-115">A type with a non-public `[DataMember]` cannot be serialized in a partial trust environment.</span></span>

- <span data-ttu-id="cd471-116">`OnSerializing`、`OnSerialized`、`OnDeserializing`、`OnDeserialized` などのシリアル化イベントを処理するメソッドは、パブリックとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-116">Methods that handle serialization events (such as `OnSerializing`, `OnSerialized`, `OnDeserializing`, and `OnDeserialized`) must be declared as public.</span></span> <span data-ttu-id="cd471-117">ただし、明示的および暗黙的な <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> の実装は、いずれもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cd471-117">However, both explicit and implicit implementations of <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> are supported.</span></span>

- <span data-ttu-id="cd471-118">`[DataContract]` は、逆シリアル化の間に新しくインスタンス化されたオブジェクトのコンストラクターを呼び出さないため、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> でマークされて、アセンブリで実装された <xref:System.Runtime.Serialization.DataContractSerializer> 型は、型コンストラクターでセキュリティ関連の操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="cd471-118">`[DataContract]` types implemented in assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> must not perform security-related actions in the type constructor, as the <xref:System.Runtime.Serialization.DataContractSerializer> does not call the constructor of the newly-instantiated object during deserialization.</span></span> <span data-ttu-id="cd471-119">特に、`[DataContract]` 型では、次の一般的なセキュリティ手法の使用を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-119">Specifically, the following common security techniques must be avoided for `[DataContract]` types:</span></span>

- <span data-ttu-id="cd471-120">型のコンストラクターを内部またはプライベートにすることにより、部分信頼アクセスを制限する。</span><span class="sxs-lookup"><span data-stu-id="cd471-120">Attempting to restrict partial trust access by making the type's constructor internal or private.</span></span>

- <span data-ttu-id="cd471-121">型のコンストラクターに `[LinkDemand]` を追加することにより、型へのアクセスを制限する。</span><span class="sxs-lookup"><span data-stu-id="cd471-121">Restricting access to the type by adding a `[LinkDemand]` to the type's constructor.</span></span>

- <span data-ttu-id="cd471-122">オブジェクトが正常にインスタンス化されたため、コンストラクターが強制するチェックがすべて正常に終了したと仮定する。</span><span class="sxs-lookup"><span data-stu-id="cd471-122">Assuming that because the object has been successfully instantiated, any validation checks enforced by the constructor have passed successfully.</span></span>

### <a name="using-ixmlserializable"></a><span data-ttu-id="cd471-123">IXmlSerializable の使用</span><span class="sxs-lookup"><span data-stu-id="cd471-123">Using IXmlSerializable</span></span>

<span data-ttu-id="cd471-124"><xref:System.Xml.Serialization.IXmlSerializable> を実装し、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化される型に適用されるベスト プラクティスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd471-124">The following best practices apply for types that implement <xref:System.Xml.Serialization.IXmlSerializable> and are serialized using the <xref:System.Runtime.Serialization.DataContractSerializer>:</span></span>

- <span data-ttu-id="cd471-125">静的 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> メソッドの実装は、`public` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-125">The <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> static method implementations must be `public`.</span></span>

- <span data-ttu-id="cd471-126"><xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装するインスタンス メソッドは、`public` とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-126">The instance methods that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface must be `public`.</span></span>

## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a><span data-ttu-id="cd471-127">部分信頼の呼び出し元から呼び出せる完全信頼のプラットフォーム コードで WCF を使用する</span><span class="sxs-lookup"><span data-stu-id="cd471-127">Using WCF from Fully-Trusted Platform Code that Allows Calls from Partially Trusted Callers</span></span>

<span data-ttu-id="cd471-128">WCF 部分信頼セキュリティモデルでは、WCF のパブリックメソッドまたはプロパティの呼び出し元が、ホストアプリケーションのコードアクセスセキュリティ (CAS) コンテキストで実行されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="cd471-128">The WCF partial trust security model assumes that any caller of a WCF public method or property is running in the code access security (CAS) context of the hosting application.</span></span> <span data-ttu-id="cd471-129">また、WCF では、それぞれに対して1つのアプリケーションセキュリティコンテキストのみが存在 <xref:System.AppDomain> し、このコンテキストが信頼されたホストによって作成時に確立されることを前提としてい <xref:System.AppDomain> ます (たとえば、 <xref:System.AppDomain.CreateDomain%2A> または ASP.NET アプリケーションマネージャーによるまたはの呼び出しによって)。</span><span class="sxs-lookup"><span data-stu-id="cd471-129">WCF also assumes that only one application security context exists for each <xref:System.AppDomain>, and that this context is established at <xref:System.AppDomain> creation time by a trusted host (for example, by a call to <xref:System.AppDomain.CreateDomain%2A> or by the ASP.NET Application Manager).</span></span>

<span data-ttu-id="cd471-130">このセキュリティ モデルは、信頼性が "中" の ASP.NET アプリケーションで実行されているユーザー コードなど、追加の CAS アクセス許可をアサートできないユーザー記述のアプリケーションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cd471-130">This security model applies to user-written applications that cannot assert additional CAS permissions, such as user code running in a Medium Trust ASP.NET application.</span></span> <span data-ttu-id="cd471-131">ただし、完全に信頼されたプラットフォームコード (たとえば、グローバルアセンブリキャッシュにインストールされ、部分信頼コードからの呼び出しを受け入れるサードパーティアセンブリ) は、部分的に信頼されたアプリケーションに代わって WCF を呼び出すときに、アプリケーションレベルのセキュリティの脆弱性が発生しないように、明示的に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-131">However, fully-trusted platform code (for example, a third-party assembly that is installed in the global assembly cache and accepts calls from partially-trusted code) must take explicit care when calling into WCF on behalf of a partially-trusted application to avoid introducing application-level security vulnerabilities.</span></span>

<span data-ttu-id="cd471-132">完全信頼コードでは <xref:System.Security.PermissionSet.Assert%2A> 、 <xref:System.Security.PermissionSet.PermitOnly%2A> 部分的に信頼された <xref:System.Security.PermissionSet.Deny%2A> コードの代わりに WCF api を呼び出す前に、、、またはを呼び出して、現在のスレッドの CAS アクセス許可セットを変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-132">Full-trust code should avoid altering the CAS permission set of the current thread (by calling <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, or <xref:System.Security.PermissionSet.Deny%2A>) prior to calling WCF APIs on behalf of partially-trusted code.</span></span> <span data-ttu-id="cd471-133">アプリケーション レベルのセキュリティ コンテキストに依存しないスレッド固有のアクセス許可コンテキストのアサート、拒否、または作成により、予期しない動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="cd471-133">Asserting, denying, or otherwise creating a thread-specific permission context that is independent of the application-level security context can result in unexpected behavior.</span></span> <span data-ttu-id="cd471-134">アプリケーションによっては、この動作がアプリケーション レベルのセキュリティの脆弱性となることがあります。</span><span class="sxs-lookup"><span data-stu-id="cd471-134">Depending on the application, this behavior may result in application-level security vulnerabilities.</span></span>

<span data-ttu-id="cd471-135">スレッド固有のアクセス許可コンテキストを使用して WCF を呼び出すコードは、次のような状況に対処できるように準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-135">Code that calls into WCF using a thread-specific permission context must be prepared to handle the following situations that may arise:</span></span>

- <span data-ttu-id="cd471-136">スレッド固有のセキュリティ コンテキストを処理の期間全体にわたっては保持できない場合があり、このときセキュリティの例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-136">The thread-specific security context may not be maintained for the duration of the operation, which results in potential security exceptions.</span></span>

- <span data-ttu-id="cd471-137">内部 WCF コードおよびユーザーが指定したコールバックは、呼び出し元が開始されたものとは異なるセキュリティコンテキストで実行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd471-137">Internal WCF code as well as any user-provided callbacks may run in a different security context than the one under which the call was originally initiated.</span></span> <span data-ttu-id="cd471-138">次のようなコンテキストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd471-138">These contexts include:</span></span>

  - <span data-ttu-id="cd471-139">アプリケーションのアクセス許可コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="cd471-139">The application permission context.</span></span>

  - <span data-ttu-id="cd471-140">現在実行中のの有効期間中に WCF を呼び出すために使用された他のユーザースレッドによって以前に作成された、スレッド固有のアクセス許可コンテキスト。 <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="cd471-140">Any thread-specific permission context previously created by other user threads used to call into WCF during the lifetime of the currently running <xref:System.AppDomain>.</span></span>

<span data-ttu-id="cd471-141">WCF パブリック Api を呼び出す前に、完全に信頼されたコンポーネントによってアサートされる場合を除き、部分信頼コードで完全信頼のアクセス許可を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="cd471-141">WCF guarantees that partially-trusted code cannot obtain full-trust permissions unless such permissions are asserted by a fully-trusted component prior to calling into WCF public APIs.</span></span> <span data-ttu-id="cd471-142">ただし、完全信頼をアサートした効果が特定のスレッド、操作、またはユーザー操作として隔離されることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="cd471-142">However, it does not guarantee that the effects of asserting full trust is isolated to a particular thread, operation, or user action.</span></span>

<span data-ttu-id="cd471-143"><xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A>、または <xref:System.Security.PermissionSet.Deny%2A> を呼び出すことにより、スレッド固有のアクセス許可コンテキストを作成しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd471-143">As a best practice, avoid creating thread-specific permission context by calling <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, or <xref:System.Security.PermissionSet.Deny%2A>.</span></span> <span data-ttu-id="cd471-144">代わりに、<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A>、または <xref:System.Security.PermissionSet.PermitOnly%2A> が不要となるように、アプリケーション自体に特権を付与するか、特権を拒否します。</span><span class="sxs-lookup"><span data-stu-id="cd471-144">Instead, grant or deny the privilege to the application itself, so that no <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, or <xref:System.Security.PermissionSet.PermitOnly%2A> is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd471-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd471-145">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
