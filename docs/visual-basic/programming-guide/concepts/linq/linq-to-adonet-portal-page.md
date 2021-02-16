---
description: '詳細情報: LINQ to ADO.NET (ポータル ページ)'
title: LINQ to ADO.NET (ポータル ページ)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5fe670be0bb87fb9a18ee73b3c3ea341d787b13e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426752"
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="acd6a-103">LINQ to ADO.NET (ポータル ページ)</span><span class="sxs-lookup"><span data-stu-id="acd6a-103">LINQ to ADO.NET (Portal Page)</span></span>

<span data-ttu-id="acd6a-104">LINQ to ADO.NET では、統合言語クエリ (LINQ) プログラミング モデルを使用して ADO.NET 内の列挙可能なオブジェクトに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-104">LINQ to ADO.NET enables you to query over any enumerable object in ADO.NET by using the Language-Integrated Query (LINQ) programming model.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acd6a-105">LINQ to ADO.NET のドキュメントは、.NET Framework SDK の ADO.NET のセクションにあります。「[LINQ と ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)」。</span><span class="sxs-lookup"><span data-stu-id="acd6a-105">The LINQ to ADO.NET documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span></span>
  
 <span data-ttu-id="acd6a-106">ADO.NET 統合言語クエリ (LINQ) には、3 つのテクノロジがあります。LINQ to DataSet、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、LINQ to Entities です。</span><span class="sxs-lookup"><span data-stu-id="acd6a-106">There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and LINQ to Entities.</span></span> <span data-ttu-id="acd6a-107">LINQ to DataSet では、<xref:System.Data.DataSet> に対する高度で最適化されたクエリの実行が提供されます。[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、SQL Server データベース スキーマに対して直接クエリを実行できます。LINQ to Entities では、Entity Data Model のクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-107">LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="acd6a-108">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="acd6a-108">LINQ to DataSet</span></span>  

 <span data-ttu-id="acd6a-109"><xref:System.Data.DataSet> は、ADO.NET で最も幅広く使用されているコンポーネントの 1 つであり、ADO.NET の基礎である非接続型プログラミングの重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="acd6a-109">The <xref:System.Data.DataSet> is one of the most widely used components in ADO.NET, and is a key element of the disconnected programming model that ADO.NET is built on.</span></span> <span data-ttu-id="acd6a-110">こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。</span><span class="sxs-lookup"><span data-stu-id="acd6a-110">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 <span data-ttu-id="acd6a-111">LINQ to DataSet では、他の多くのデータ ソースで使用できるのと同じクエリ機能を使用することで、豊富なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-111">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="acd6a-112">詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acd6a-112">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="acd6a-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="acd6a-113">LINQ to SQL</span></span>  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="acd6a-114">には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="acd6a-114">provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="acd6a-115">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="acd6a-115">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="acd6a-116">アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。</span><span class="sxs-lookup"><span data-stu-id="acd6a-116">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="acd6a-117">データベースから結果が返されると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で元の操作できるオブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-117">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="acd6a-118">には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="acd6a-118">includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="acd6a-119">詳細については、「[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acd6a-119">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="acd6a-120">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="acd6a-120">LINQ to Entities</span></span>  

 <span data-ttu-id="acd6a-121">Entity Data Model では、リレーショナル データが .NET 環境にオブジェクトとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-121">Through the Entity Data Model, relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="acd6a-122">これにより、LINQ の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-122">This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="acd6a-123">この機能は、LINQ to Entities と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="acd6a-123">This capability is known as LINQ to Entities.</span></span> <span data-ttu-id="acd6a-124">LINQ の詳細については、「[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acd6a-124">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd6a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="acd6a-125">See also</span></span>

- [<span data-ttu-id="acd6a-126">LINQ と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="acd6a-126">LINQ and ADO.NET</span></span>](../../../../framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="acd6a-127">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acd6a-127">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
