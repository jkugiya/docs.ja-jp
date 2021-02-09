---
description: '詳細情報: SQL Server における XML データ'
title: SQL Server における XML データ
ms.date: 03/30/2017
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
ms.openlocfilehash: fb087aeb0893ce9de9c5beb7728ff1af3259d3e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766934"
---
# <a name="xml-data-in-sql-server"></a><span data-ttu-id="bc182-103">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="bc182-103">XML Data in SQL Server</span></span>

<span data-ttu-id="bc182-104">SQL Server は、.NET Framework 内部の SQLXML の機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="bc182-104">SQL Server exposes the functionality of SQLXML inside the .NET Framework.</span></span> <span data-ttu-id="bc182-105">開発者は、SQL Server のインスタンスから XML データにアクセスし、データを .NET Framework 環境に持ち込んで処理し、更新を SQL Server に送り返すアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bc182-105">Developers can write applications that access XML data from an instance of SQL Server, bring the data into the .NET Framework environment, process the data, and send the updates back to SQL Server.</span></span> <span data-ttu-id="bc182-106">SQL Server では、XML データをデータ ストレージなどの目的に、あるいはデータを取得するときのパラメーター値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc182-106">XML data can be used in several ways in SQL Server, including data storage, and as parameter values for retrieving data.</span></span> <span data-ttu-id="bc182-107">.NET Framework の **SqlXml** クラスは、SQL Server 内の XML 列に格納されたデータのクライアント側の操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="bc182-107">The **SqlXml** class in the .NET Framework provides the client-side support for working with data stored in an XML column within SQL Server.</span></span> <span data-ttu-id="bc182-108">詳細については、SQL Server オンライン ブックの「SQLXML マネージド クラス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc182-108">For more information, see "SQLXML Managed Classes" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc182-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bc182-109">In This Section</span></span>  

 [<span data-ttu-id="bc182-110">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="bc182-110">SQL XML Column Values</span></span>](sql-xml-column-values.md)  
 <span data-ttu-id="bc182-111">SQL Server から XML データを取得し、使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc182-111">Demonstrates how to retrieve and work with XML data retrieved from SQL Server.</span></span>  
  
 [<span data-ttu-id="bc182-112">パラメーターとしての XML 値の指定</span><span class="sxs-lookup"><span data-stu-id="bc182-112">Specifying XML Values as Parameters</span></span>](specifying-xml-values-as-parameters.md)  
 <span data-ttu-id="bc182-113">コマンドに XML データをパラメーターとして渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc182-113">Demonstrates how to pass XML data as a parameter to a command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc182-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc182-114">See also</span></span>

- [<span data-ttu-id="bc182-115">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bc182-115">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="bc182-116">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="bc182-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
