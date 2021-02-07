---
description: '詳細情報: ワークフローセキュリティ'
title: ワークフローのセキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: afaf5c9f5a8b0bcf707dae0e9e9669d63c5f8176
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754863"
---
# <a name="workflow-security"></a><span data-ttu-id="fd0cd-103">ワークフローのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="fd0cd-103">Workflow Security</span></span>

<span data-ttu-id="fd0cd-104">Windows Workflow Foundation (WF) は、Microsoft SQL Server や Windows Communication Foundation (WCF) など、いくつかの異なるテクノロジと統合されています。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-104">Windows Workflow Foundation (WF) is integrated with several different technologies, such as Microsoft SQL Server and Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fd0cd-105">これらのテクノロジと相互作用するうえで、不適切に実行された場合にワークフローでセキュリティの問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-105">Interacting with these technologies may introduce security issues into your workflow if done improperly.</span></span>

## <a name="persistence-security-concerns"></a><span data-ttu-id="fd0cd-106">永続化のセキュリティに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="fd0cd-106">Persistence Security Concerns</span></span>

1. <span data-ttu-id="fd0cd-107"><xref:System.Activities.Statements.Delay> アクティビティと永続化を使用するワークフローは、サービスによって再アクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-107">Workflows that use a <xref:System.Activities.Statements.Delay> activity and persistence need to be reactivated by a service.</span></span> <span data-ttu-id="fd0cd-108">Windows AppFabric はワークフロー管理サービス (WMS) を使用して、タイマーが期限切れのワークフローを再アクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-108">Windows AppFabric uses the Workflow Management Service (WMS) to reactivate workflows with expired timers.</span></span> <span data-ttu-id="fd0cd-109">WMS は <xref:System.ServiceModel.WorkflowServiceHost> を作成して、再アクティブ化されたワークフローをホストします。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-109">WMS creates a <xref:System.ServiceModel.WorkflowServiceHost> to host the reactivated workflow.</span></span> <span data-ttu-id="fd0cd-110">WMS サービスが停止した場合、永続化されたワークフローはタイマーが時間切れになっていると再アクティブ化されません。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-110">If the WMS service is stopped, persisted workflows will not be reactivated when their timers expire.</span></span>

2. <span data-ttu-id="fd0cd-111">永続的なインスタンスへのアクセスは、アプリケーション ドメイン外の安全でないエンティティから保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-111">Access to durable instancing should be protected against malicious entities external to the application domain.</span></span> <span data-ttu-id="fd0cd-112">また、開発者は、悪意のあるコードが永続性インスタンス化コードと同じアプリケーション ドメインで実行できないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-112">In addition, developers should ensure that malicious code can't be executed in the same application domain as the durable instancing code.</span></span>

3. <span data-ttu-id="fd0cd-113">永続性インスタンス化は、高い (管理者の) アクセス許可で実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-113">Durable instancing should not be run with elevated (Administrator) permissions.</span></span>

4. <span data-ttu-id="fd0cd-114">アプリケーション ドメインの外部で処理されるデータは、保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-114">Data being processed outside the application domain should be protected.</span></span>

5. <span data-ttu-id="fd0cd-115">セキュリティの分離を必要とするアプリケーションは、スキーマ抽象化と同じインスタンスを共有しないようにします。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-115">Applications that require security isolation should not share the same instance of the schema abstraction.</span></span> <span data-ttu-id="fd0cd-116">このようなアプリケーションは、異なるストア プロバイダーを使用するか、別のストアのインスタンス化を使用するように構成されたストア プロバイダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-116">Such applications should use different store providers, or store providers configured to use different store instantiations.</span></span>

## <a name="sql-server-security-concerns"></a><span data-ttu-id="fd0cd-117">SQL サーバーのセキュリティに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="fd0cd-117">SQL Server Security Concerns</span></span>

- <span data-ttu-id="fd0cd-118">子アクティビティ、場所、ブックマーク、ホストの拡張機能、またはスコープを多数使用する場合、またはペイロードが非常に大きいブックマークを使用する場合、メモリが不足したり、永続化の実行中に必要以上のディスク容量が割り当てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-118">When large numbers of child activities, locations, bookmarks, host extensions, or scopes are used, or when bookmarks with very large payloads are used, memory can be exhausted, or undue amounts of database space can be allocated during persistence.</span></span> <span data-ttu-id="fd0cd-119">オブジェクト レベルおよびデータベース レベルのセキュリティを使用すると、このような状態を緩和できます。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-119">This can be mitigated by using object-level and database-level security.</span></span>

- <span data-ttu-id="fd0cd-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する場合、インスタンス ストアをセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-120">When using <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the instance store must be secured.</span></span>

- <span data-ttu-id="fd0cd-121">インスタンス ストアの機密情報は暗号化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-121">Sensitive data in the instance store should be encrypted.</span></span> <span data-ttu-id="fd0cd-122">詳細については、「 [SQL Server の暗号化](/sql/relational-databases/security/encryption/sql-server-encryption)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-122">For more information, see [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption).</span></span>

- <span data-ttu-id="fd0cd-123">多くの場合、データベース接続文字列は構成ファイルに含まれているので、Windows レベルのセキュリティ (ACL) を使用して、構成ファイル (通常は Web.Config) が安全であるように、またログインとパスワードの情報が接続文字列に含まれないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-123">Since the database connection string is often included in a configuration file, windows-level security (ACL) should be used to ensure that the configuration file (Web.Config usually) is secure, and that login and password information are not included in the connection string.</span></span> <span data-ttu-id="fd0cd-124">Windows 認証をデータベースと Web サーバー間で代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-124">Windows authentication should be used between the database and the web server instead.</span></span>

## <a name="considerations-for-workflowservicehost"></a><span data-ttu-id="fd0cd-125">WorkflowServiceHost に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fd0cd-125">Considerations for WorkflowServiceHost</span></span>

- <span data-ttu-id="fd0cd-126">ワークフローで使用される Windows Communication Foundation (WCF) エンドポイントはセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-126">Windows Communication Foundation (WCF) endpoints used in workflows should be secured.</span></span> <span data-ttu-id="fd0cd-127">詳細については、「 [WCF セキュリティの概要](../wcf/feature-details/security-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-127">For more information, see [WCF Security Overview](../wcf/feature-details/security-overview.md).</span></span>

- <span data-ttu-id="fd0cd-128"><xref:System.ServiceModel.ServiceAuthorizationManager> を使用して、ホスト レベルの認証を実装できます。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-128">Host-level authorization can be implemented by using <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span> <span data-ttu-id="fd0cd-129">詳細については、「 [方法: サービスのカスタム承認マネージャーを作成](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-129">See [How To: Create a Custom Authorization Manager for a Service](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) for details.</span></span>

- <span data-ttu-id="fd0cd-130">受信メッセージの ServiceSecurityContext は、OperationContext へのアクセスによって、ワーク フロー内からも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-130">The ServiceSecurityContext for the incoming message is also available from within workflow by accessing OperationContext.</span></span>

## <a name="wf-security-pack-ctp"></a><span data-ttu-id="fd0cd-131">WF Security Pack CTP</span><span class="sxs-lookup"><span data-stu-id="fd0cd-131">WF Security Pack CTP</span></span>

 <span data-ttu-id="fd0cd-132">Microsoft WF Security Pack community テクノロジプレビュー (CTP) 1 は、 [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) および[Windows IDENTITY Foundation (WIF)](/previous-versions/dotnet/framework/security/index)の[Windows Workflow Foundation](index.md)に基づく一連のアクティビティとその実装です。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-132">The Microsoft WF Security Pack community technology preview (CTP) 1 is a set of activities and their implementation based on [Windows Workflow Foundation](index.md) in [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) and [Windows Identity Foundation (WIF)](/previous-versions/dotnet/framework/security/index).</span></span> <span data-ttu-id="fd0cd-133">Microsoft WF Security Pack CTP 1 には、アクティビティおよび、ワークフローを使用してさまざまなセキュリティ関連のシナリオを簡単に有効にする方法を示すそのデザイナーの両方が含まれています。これらには以下のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-133">The Microsoft WF Security Pack CTP 1 contains both activities and their designers which illustrate how to easily enable various security-related scenarios using workflow, including:</span></span>

1. <span data-ttu-id="fd0cd-134">ワークフローのクライアント ID の偽装</span><span class="sxs-lookup"><span data-stu-id="fd0cd-134">Impersonating a client identity in the workflow</span></span>

2. <span data-ttu-id="fd0cd-135">PrincipalPermission やクレームの検証などの内部ワークフローの認証</span><span class="sxs-lookup"><span data-stu-id="fd0cd-135">In-workflow authorization, such as PrincipalPermission and validation of Claims</span></span>

3. <span data-ttu-id="fd0cd-136">ユーザー名/パスワードやセキュリティ トークン サービス (STS) から取得するトークンなど、ワークフローで指定される ClientCredentials を使用した認証されたメッセージ</span><span class="sxs-lookup"><span data-stu-id="fd0cd-136">Authenticated messaging using ClientCredentials specified in the workflow, such as username/password or a token retrieved from a Security Token Service (STS)</span></span>

4. <span data-ttu-id="fd0cd-137">WS-Trust ActAs を使用して、クライアント セキュリティ トークンをバックエンド サービス (クレーム ベースの委任) にフロー</span><span class="sxs-lookup"><span data-stu-id="fd0cd-137">Flowing a client security token to a back-end service (claims-based delegation) using WS-Trust ActAs</span></span>

<span data-ttu-id="fd0cd-138">WF Security Pack CTP の詳細とダウンロードについては、「 [Wf Security pack ctp (Wf セキュリティパック ctp](https://archive.codeplex.com/?p=wf) )」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0cd-138">For more information and to download the WF Security Pack CTP, see: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)</span></span>
