---
description: '詳細情報: ファクトリ モデルの概要'
title: ファクトリ モデルの概要
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 175b05a298eb260dfe8c59b380ab3b8b9dcba943
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724207"
---
# <a name="factory-model-overview"></a><span data-ttu-id="bc843-103">ファクトリ モデルの概要</span><span class="sxs-lookup"><span data-stu-id="bc843-103">Factory Model Overview</span></span>

<span data-ttu-id="bc843-104">ADO.NET 2.0 では、<xref:System.Data.Common> 名前空間に新しい基本クラスが導入されました。</span><span class="sxs-lookup"><span data-stu-id="bc843-104">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="bc843-105">基本クラスは抽象的な存在です。つまり、直接インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc843-105">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="bc843-106">新しい基本クラスとしては、<xref:System.Data.Common.DbConnection>、<xref:System.Data.Common.DbCommand>、<xref:System.Data.Common.DbDataAdapter> があり、<xref:System.Data.SqlClient> や <xref:System.Data.OleDb> などの .NET Framework データ プロバイダーによって共有されます。</span><span class="sxs-lookup"><span data-stu-id="bc843-106">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="bc843-107">基本クラスが追加されたことで、新しいインターフェイスを作成しなくても、.NET Framework データ プロバイダーに対して容易に機能を追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc843-107">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="bc843-108">また、ADO.NET 2.0 で抽象基本クラスが導入されたことにより、開発者は特定のデータ プロバイダーに依存しない汎用的なデータ アクセス コードを記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc843-108">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="bc843-109">ファクトリ デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="bc843-109">The Factory Design Pattern</span></span>  

 <span data-ttu-id="bc843-110">単一の API で複数プロバイダーのデータベースにアクセスできる "ファクトリ" デザイン パターンの使用は、プロバイダーに依存しないコードを作成するプログラミング モデルの基礎となるものです。</span><span class="sxs-lookup"><span data-stu-id="bc843-110">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="bc843-111">このパターンでは、現実世界の工場のように、他のオブジェクトを作成するためだけに特殊なオブジェクトを使用するため、適切なネーミングがなされていると言えます。</span><span class="sxs-lookup"><span data-stu-id="bc843-111">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="bc843-112">ファクトリ デザイン パターンの詳細な説明については、「[ASP.NET 2.0 および ADO.NET 2.0 での汎用的なデータ アクセス コードの作成](/previous-versions/dotnet/articles/ms971499(v=msdn.10))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc843-112">For a more detailed description of the factory design pattern, see [Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](/previous-versions/dotnet/articles/ms971499(v=msdn.10)).</span></span>
  
 <span data-ttu-id="bc843-113">ADO.NET 2.0 以降では、<xref:System.Data.Common.DbProviderFactories> のインスタンスを作成するための `static` (Visual Basic の場合は `Shared`) メソッドが <xref:System.Data.Common.DbProviderFactory> クラスに用意されています。</span><span class="sxs-lookup"><span data-stu-id="bc843-113">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="bc843-114">このインスタンスにより、実行時に指定したプロバイダー情報と接続文字列に基づいて、厳密に型指定された適切なオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="bc843-114">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc843-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc843-115">See also</span></span>

- [<span data-ttu-id="bc843-116">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="bc843-116">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="bc843-117">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="bc843-117">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="bc843-118">DbDataAdapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="bc843-118">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="bc843-119">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="bc843-119">ADO.NET Overview</span></span>](ado-net-overview.md)
