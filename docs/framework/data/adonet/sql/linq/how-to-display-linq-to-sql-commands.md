---
description: '詳細情報: 方法:LINQ to SQL コマンドを表示する'
title: '方法: LINQ to SQL コマンドを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: 480e7c1cbcceb09f0d727d03569d6277e0dd754b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785992"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="3fa2e-103">方法: LINQ to SQL コマンドを表示する</span><span class="sxs-lookup"><span data-stu-id="3fa2e-103">How to: Display LINQ to SQL Commands</span></span>

<span data-ttu-id="3fa2e-104">SQL コマンドとその他の情報を表示するには、<xref:System.Data.Linq.DataContext.GetCommand%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="3fa2e-104">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fa2e-105">例</span><span class="sxs-lookup"><span data-stu-id="3fa2e-105">Example</span></span>  

 <span data-ttu-id="3fa2e-106">クエリからの出力、生成された SQL コマンド、コマンドの種類、および接続の種類をコンソール ウィンドウに表示する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3fa2e-106">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="3fa2e-107">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fa2e-107">Output appears as follows:</span></span>  
  
```console  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```console  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fa2e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fa2e-108">See also</span></span>

- [<span data-ttu-id="3fa2e-109">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="3fa2e-109">Debugging Support</span></span>](debugging-support.md)
