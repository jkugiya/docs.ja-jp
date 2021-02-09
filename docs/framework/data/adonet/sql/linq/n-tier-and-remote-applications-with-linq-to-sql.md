---
description: '詳細情報: LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション'
title: LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6abaeed8d4953a9b810db32418a4ebd3e78683fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695607"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="e40fd-103">LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e40fd-103">N-Tier and Remote Applications with LINQ to SQL</span></span>

<span data-ttu-id="e40fd-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層つまり多層アプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e40fd-104">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e40fd-105">通常、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のデータ コンテキスト、エンティティ クラス、およびクエリ構築ロジックは、中間層にデータ アクセス層 (DAL) として置かれます。</span><span class="sxs-lookup"><span data-stu-id="e40fd-105">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="e40fd-106">ビジネス ロジックと非永続的データは、エンティティとデータ コンテキストの部分クラスと部分メソッドの中に完全に実装できます。または、別個のクラスに実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="e40fd-106">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>

 <span data-ttu-id="e40fd-107">クライアントまたはプレゼンテーション層は、中間層のリモート インターフェイス上のメソッドを呼び出し、その層の DAL は、<xref:System.Data.Linq.DataContext> メソッドにマップされるクエリまたはストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="e40fd-107">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="e40fd-108">中間層は、通常、エンティティまたはプロキシ オブジェクトの XML 表現としてデータをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="e40fd-108">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>

 <span data-ttu-id="e40fd-109">中間層では、データ コンテキストによってエンティティが作成され、データ コンテキストはエンティティの状態を追跡し、データベースからの遅延読み込み、および変更内容のデータベースへの送信を管理します。</span><span class="sxs-lookup"><span data-stu-id="e40fd-109">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="e40fd-110">これらのエンティティは、`DataContext` にいわばアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="e40fd-110">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="e40fd-111">ただし、シリアル化によってエンティティが別の層に送られた後は、エンティティがデタッチされます。つまり、その状態が `DataContext` によって追跡されなくなります。</span><span class="sxs-lookup"><span data-stu-id="e40fd-111">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="e40fd-112">更新のためにクライアントによって戻されるエンティティは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が変更内容をデータベースに送信する前に、データ コンテキストに再びアタッチされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e40fd-112">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="e40fd-113">オプティミスティック コンカレンシー チェックのために元の値またはタイムスタンプが必要とされる場合、クライアントはこれらを中間層に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e40fd-113">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>

 <span data-ttu-id="e40fd-114">ASP.NET アプリケーションでは、このような複雑な操作の大部分が <xref:System.Web.UI.WebControls.LinqDataSource> によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="e40fd-114">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="e40fd-115">詳細については、「[LinqDataSource Web サーバー コントロールの概要](/previous-versions/aspnet/bb547113(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e40fd-115">For more information, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e40fd-116">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="e40fd-116">Additional Resources</span></span>

 <span data-ttu-id="e40fd-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層アプリケーションの実装方法について、詳しくは以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e40fd-117">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>

- [<span data-ttu-id="e40fd-118">ASP.NET での LINQ to SQL N 層</span><span class="sxs-lookup"><span data-stu-id="e40fd-118">LINQ to SQL N-Tier with ASP.NET</span></span>](linq-to-sql-n-tier-with-aspnet.md)

- [<span data-ttu-id="e40fd-119">Web サービスを使用した LINQ to SQL N 層</span><span class="sxs-lookup"><span data-stu-id="e40fd-119">LINQ to SQL N-Tier with Web Services</span></span>](linq-to-sql-n-tier-with-web-services.md)

- [<span data-ttu-id="e40fd-120">N 層ビジネス ロジックの実装</span><span class="sxs-lookup"><span data-stu-id="e40fd-120">Implementing N-Tier Business Logic</span></span>](implementing-business-logic-linq-to-sql.md)

- [<span data-ttu-id="e40fd-121">N 層アプリケーションでのデータ取得および CUD 操作 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="e40fd-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 <span data-ttu-id="e40fd-122">ADO.NET DataSet を使用する n 層アプリケーションについて詳しくは、「[n 層アプリケーションでのデータセットの操作](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e40fd-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="e40fd-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e40fd-123">See also</span></span>

- [<span data-ttu-id="e40fd-124">背景情報</span><span class="sxs-lookup"><span data-stu-id="e40fd-124">Background Information</span></span>](background-information.md)
