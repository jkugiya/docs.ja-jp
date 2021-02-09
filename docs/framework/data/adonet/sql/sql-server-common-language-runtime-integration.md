---
description: '詳細情報: SQL Server の共通言語ランタイム統合'
title: SQL Server の共通言語ランタイム統合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 096bba0d183526ec8e5d272c5ea6a77ad0778e5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767402"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="bc80c-103">SQL Server の共通言語ランタイム統合</span><span class="sxs-lookup"><span data-stu-id="bc80c-103">SQL Server Common Language Runtime Integration</span></span>

<span data-ttu-id="bc80c-104">SQL Server 2005 で、Microsoft Windows 用の .NET Framework の共通言語ランタイム (CLR) コンポーネントの統合が導入されました。</span><span class="sxs-lookup"><span data-stu-id="bc80c-104">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="bc80c-105">つまり、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc80c-105">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="bc80c-106">マネージド コードが Microsoft SQL Server 環境とデータをやり取りできるように、<xref:Microsoft.SqlServer.Server> 名前空間には新しいアプリケーション プログラミング インターフェイス (API) のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc80c-106">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="bc80c-107">このセクションでは、SQL Server の共通言語ランタイム (CLR) 統合および SQL Server のインプロセス固有の ADO.NET の拡張に固有の機能や動作ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-107">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="bc80c-108">このセクションは、SQL Server の CLR 統合を利用したプログラミングを始めるのに十分な情報を提供することを目的としており、包括的な情報の提供は目的としていません。</span><span class="sxs-lookup"><span data-stu-id="bc80c-108">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="bc80c-109">詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc80c-109">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="bc80c-110">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="bc80c-110">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="bc80c-111">CLR (共通言語ランタイム) 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="bc80c-111">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="bc80c-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bc80c-112">In This Section</span></span>  

 [<span data-ttu-id="bc80c-113">SQL Server の CLR 統合の概要</span><span class="sxs-lookup"><span data-stu-id="bc80c-113">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="bc80c-114">SQL Server の CLR 統合の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-114">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="bc80c-115">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="bc80c-115">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="bc80c-116">CLR ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="bc80c-116">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="bc80c-117">テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-117">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="bc80c-118">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="bc80c-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="bc80c-119">CLR のユーザー定義型を実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-119">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="bc80c-120">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="bc80c-120">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="bc80c-121">CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="bc80c-121">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="bc80c-122">CLR のストアド プロシージャを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-122">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="bc80c-123">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="bc80c-123">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="bc80c-124">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="bc80c-124">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="bc80c-125">CLR のトリガーを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-125">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="bc80c-126">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="bc80c-126">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="bc80c-127">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="bc80c-127">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="bc80c-128">コンテキスト接続について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-128">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="bc80c-129">SQL Server のインプロセス固有の ADO.NET の動作</span><span class="sxs-lookup"><span data-stu-id="bc80c-129">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="bc80c-130">SQL Server のインプロセス固有の ADO.NET の拡張およびコンテキスト接続について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc80c-130">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="bc80c-131">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="bc80c-131">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc80c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc80c-132">See also</span></span>

- [<span data-ttu-id="bc80c-133">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bc80c-133">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="bc80c-134">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="bc80c-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
