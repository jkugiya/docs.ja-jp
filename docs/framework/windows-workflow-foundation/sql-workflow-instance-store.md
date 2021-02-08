---
description: 詳細については、「SQL Workflow Instance Store」を参照してください。
title: SQL Workflow Instance Store
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: ca2b6751b69aa65a1e151feb55eee3a62f31895e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798070"
---
# <a name="sql-workflow-instance-store"></a><span data-ttu-id="66285-103">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="66285-103">SQL Workflow Instance Store</span></span>

<span data-ttu-id="66285-104">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には SQL Workflow Instance Store が含まれます。これを使用すると、ワークフロー インスタンスに関する状態情報を SQL Server 2005 または SQL Server 2008 のデータベースに永続化できます。</span><span class="sxs-lookup"><span data-stu-id="66285-104">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ships with the SQL Workflow Instance Store, which allows workflows to persist state information about workflow instances in a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="66285-105">この機能は主に <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスの形式で実装されます。このクラスは永続化フレームワークの <xref:System.Runtime.DurableInstancing.InstanceStore> 抽象クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="66285-105">This feature is primarily implemented in the form of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class, which derives from the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class of the persistence framework.</span></span> <span data-ttu-id="66285-106">SQL Workflow Instance Store 機能によって SQL 永続性プロバイダーを構成します。このプロバイダーは、ホストが永続化コマンドをストアに送信するときに使用する永続化 API の具象実装です。</span><span class="sxs-lookup"><span data-stu-id="66285-106">The SQL Workflow Instance Store feature constitutes a SQL persistence provider, which is a concrete implementation of the persistence API that a host uses to send persistence commands to the store.</span></span>  
  
 <span data-ttu-id="66285-107">SQL Workflow Instance Store は、セルフホストされているワークフローや、<xref:System.Activities.WorkflowApplication> または <xref:System.ServiceModel.WorkflowServiceHost> を使用するワークフロー サービスだけでなく、<xref:System.ServiceModel.WorkflowServiceHost> を使用して WAS でホストされるサービスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="66285-107">The SQL Workflow Instance Store supports both self-hosted workflows or workflow services that use <xref:System.Activities.WorkflowApplication> or <xref:System.ServiceModel.WorkflowServiceHost> as well as services hosted in WAS using <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="66285-108">セルフホストされているサービスの SQL Workflow Instance Store 機能をプログラムで構成するには、この機能が公開しているオブジェクト モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="66285-108">You can configure the SQL Workflow Instance Store feature for self-hosted services programmatically by using the object model exposed by the feature.</span></span> <span data-ttu-id="66285-109">プログラムでオブジェクト モデルや XML 構成ファイルを使用することにより、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるサービスについてこの機能を構成できます。</span><span class="sxs-lookup"><span data-stu-id="66285-109">You can configure this feature for services hosted by <xref:System.ServiceModel.WorkflowServiceHost> both programmatically by using the object model and also by using an XML configuration file.</span></span>  
  
 <span data-ttu-id="66285-110">SQL Workflow Instance Store 機能 (**SqlWorkflowInstanceStore** クラス) にはが実装されていないため、永続 <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> 性のないワークフロー以外の WCF サービスの永続化サポートは提供されません。</span><span class="sxs-lookup"><span data-stu-id="66285-110">The SQL Workflow Instance Store feature (**SqlWorkflowInstanceStore** class) does not implement <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> and hence does not offer persistence support for durable non-workflow WCF services.</span></span> <span data-ttu-id="66285-111">また、<xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> を実装していないため、3.x ワークフローの永続化は提供しません。</span><span class="sxs-lookup"><span data-stu-id="66285-111">It also does not implement <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> and hence does not offer persistence support for 3.x workflows.</span></span> <span data-ttu-id="66285-112">この機能は、WF 4.0 以降のワークフローとワークフロー サービスについてのみ永続化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="66285-112">The feature supports persistence for only WF 4.0 (and later) workflows and workflow services.</span></span> <span data-ttu-id="66285-113">また、SQL Server 2005 と SQL Server 2008 以外のデータベースはサポートしません。</span><span class="sxs-lookup"><span data-stu-id="66285-113">The feature also does not support any databases other than SQL Server 2005 and SQL Server 2008.</span></span>  
  
 <span data-ttu-id="66285-114">このセクションのトピックでは、SQL Workflow Instance Store のプロパティと機能、およびストアの構成方法の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="66285-114">The topics in this section describe properties and features of the SQL Workflow Instance Store and provide you with details on configuring the store.</span></span>  
  
 <span data-ttu-id="66285-115">Windows Server App Fabric には、インスタンス ストアを簡単に構成および使用できる独自のインスタンス ストアとツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="66285-115">Windows Server App Fabric provides its own instance store and tooling to simplify the configuration and use of the instance store.</span></span> <span data-ttu-id="66285-116">詳細については、「 [Windows Server App Fabric インスタンスストア](/previous-versions/appfabric/ff383417(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66285-116">For more information, see [Windows Server App Fabric Instance Store](/previous-versions/appfabric/ff383417(v=azure.10)).</span></span> <span data-ttu-id="66285-117">App Fabric SQL Server 永続性データベースの詳細については、「 [App fabric SQL Server 永続性データベース](/previous-versions/appfabric/ee790819(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66285-117">For more information about the App Fabric SQL Server Persistence Database see [App Fabric SQL Server Persistence Database](/previous-versions/appfabric/ee790819(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66285-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="66285-118">In This Section</span></span>  
  
- [<span data-ttu-id="66285-119">SQL Workflow Instance Store のプロパティ</span><span class="sxs-lookup"><span data-stu-id="66285-119">Properties of SQL Workflow Instance Store</span></span>](properties-of-sql-workflow-instance-store.md)  
  
- [<span data-ttu-id="66285-120">方法: ワークフローとワークフロー サービスの SQL 永続性を有効にする</span><span class="sxs-lookup"><span data-stu-id="66285-120">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [<span data-ttu-id="66285-121">インスタンスのアクティブ化処理</span><span class="sxs-lookup"><span data-stu-id="66285-121">Instance Activation</span></span>](instance-activation.md)  
  
- [<span data-ttu-id="66285-122">クエリのサポート</span><span class="sxs-lookup"><span data-stu-id="66285-122">Support for Queries</span></span>](support-for-queries.md)  
  
- [<span data-ttu-id="66285-123">ストア拡張</span><span class="sxs-lookup"><span data-stu-id="66285-123">Store Extensibility</span></span>](store-extensibility.md)  
  
- [<span data-ttu-id="66285-124">Security</span><span class="sxs-lookup"><span data-stu-id="66285-124">Security</span></span>](security.md)  
  
- [<span data-ttu-id="66285-125">SQL Server 永続性データベース</span><span class="sxs-lookup"><span data-stu-id="66285-125">SQL Server Persistence Database</span></span>](sql-server-persistence-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="66285-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="66285-126">See also</span></span>

- <span data-ttu-id="66285-127">[永続化のサンプル](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="66285-127">[Persistence Samples](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))</span></span>
