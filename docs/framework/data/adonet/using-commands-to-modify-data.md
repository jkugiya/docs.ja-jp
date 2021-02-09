---
description: '詳細情報: コマンドを使用したデータ変更'
title: コマンドを使用したデータ変更
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 3addcb93850aa8e26fe441b5c859502779433bfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766557"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="6ed92-103">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="6ed92-103">Using Commands to Modify Data</span></span>

<span data-ttu-id="6ed92-104">.NET Framework データ プロバイダーを使用すると、ストアド プロシージャまたはデータ定義言語のステートメント (たとえば、CREATE TABLE、ALTER COLUMN など) を実行して、データベースやカタログに対するスキーマ操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6ed92-104">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="6ed92-105">これらのコマンドはクエリとは異なり、行を返さないため、**Command** オブジェクトではこれらを処理するために **ExecuteNonQuery** が提供されています。</span><span class="sxs-lookup"><span data-stu-id="6ed92-105">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="6ed92-106">**ExecuteNonQuery** メソッドを使用すると、スキーマを変更できるだけでなく、データを変更するが行を返さない INSERT、UPDATE、DELETE などの SQL ステートメントも処理できます。</span><span class="sxs-lookup"><span data-stu-id="6ed92-106">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="6ed92-107">**ExecuteNonQuery** メソッドでは行は返されませんが、**Command** オブジェクトの **Parameters** コレクションを通じて入力パラメーター、出力パラメーター、および戻り値を受け渡しできます。</span><span class="sxs-lookup"><span data-stu-id="6ed92-107">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ed92-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6ed92-108">In This Section</span></span>  

 [<span data-ttu-id="6ed92-109">データ ソースのデータの更新</span><span class="sxs-lookup"><span data-stu-id="6ed92-109">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="6ed92-110">データベース内のデータを変更するコマンドまたはストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ed92-110">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="6ed92-111">カタログ操作の実行</span><span class="sxs-lookup"><span data-stu-id="6ed92-111">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="6ed92-112">データベース スキーマを変更するコマンドを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ed92-112">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed92-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ed92-113">See also</span></span>

- [<span data-ttu-id="6ed92-114">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="6ed92-114">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="6ed92-115">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="6ed92-115">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="6ed92-116">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="6ed92-116">ADO.NET Overview</span></span>](ado-net-overview.md)
