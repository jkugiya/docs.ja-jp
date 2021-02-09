---
description: '詳細情報: 方法:行セットを返す'
title: '方法: 行セットを返す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b799ce82542e6929f42485508b3a2c36cc42ee60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723388"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="92f2a-103">方法: 行セットを返す</span><span class="sxs-lookup"><span data-stu-id="92f2a-103">How to: Return Rowsets</span></span>

<span data-ttu-id="92f2a-104">この例では、データベースから行セットを返し、入力パラメーターを使用して結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="92f2a-104">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="92f2a-105">行セットを返すストアド プロシージャを実行する場合は、ストアド プロシージャからの戻り値を格納する "*結果*" クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="92f2a-105">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="92f2a-106">詳しくは、「[LINQ to SQL のソース コードの分析](analyzing-linq-to-sql-source-code.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="92f2a-106">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f2a-107">例</span><span class="sxs-lookup"><span data-stu-id="92f2a-107">Example</span></span>  

 <span data-ttu-id="92f2a-108">次の例は、顧客の行を返し、入力パラメーターを使用して、顧客が在住する市が "London" である行のみを返すストアド プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="92f2a-108">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="92f2a-109">例では、列挙可能な `CustomersByCityResult` クラスを想定しています。</span><span class="sxs-lookup"><span data-stu-id="92f2a-109">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="92f2a-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="92f2a-110">See also</span></span>

- [<span data-ttu-id="92f2a-111">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="92f2a-111">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="92f2a-112">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="92f2a-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
