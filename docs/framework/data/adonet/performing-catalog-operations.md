---
description: '詳細情報: カタログ操作の実行'
title: カタログ操作の実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c484e3a56d846de66c6e13b374efe58430ab86b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754343"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="aed9e-103">カタログ操作の実行</span><span class="sxs-lookup"><span data-stu-id="aed9e-103">Performing Catalog Operations</span></span>

<span data-ttu-id="aed9e-104">データベースまたはカタログを変更するコマンド (CREATE TABLE ステートメント、CREATE PROCEDURE ステートメントなど) を実行するには、適切な SQL ステートメントと **Connection** オブジェクトを使用して、**Command** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="aed9e-104">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="aed9e-105">**Command** オブジェクトの **ExecuteNonQuery** メソッドでコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="aed9e-105">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="aed9e-106">Microsoft SQL Server データベースにストアド プロシージャを作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="aed9e-106">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="aed9e-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="aed9e-107">See also</span></span>

- [<span data-ttu-id="aed9e-108">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="aed9e-108">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="aed9e-109">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="aed9e-109">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="aed9e-110">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="aed9e-110">ADO.NET Overview</span></span>](ado-net-overview.md)
