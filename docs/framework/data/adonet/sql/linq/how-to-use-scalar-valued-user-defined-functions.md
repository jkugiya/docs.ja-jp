---
description: '詳細情報: 方法:スカラー値のユーザー定義関数を使用する'
title: '方法: スカラー値のユーザー定義関数を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: e606dd3f840b8f082928217c6118b48d8d4a2e5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785811"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="57979-103">方法: スカラー値のユーザー定義関数を使用する</span><span class="sxs-lookup"><span data-stu-id="57979-103">How to: Use Scalar-Valued User-Defined Functions</span></span>

<span data-ttu-id="57979-104"><xref:System.Data.Linq.Mapping.FunctionAttribute> 属性を使用することによって、クラスで定義されているクライアント メソッドを、ユーザー定義関数に対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="57979-104">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="57979-105">メソッドの本体は、メソッド呼び出しの目的を反映する式を構築し、変換および実行のためにその式を <xref:System.Data.Linq.DataContext> に渡します。</span><span class="sxs-lookup"><span data-stu-id="57979-105">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57979-106">直接実行は、関数がクエリの外部で呼び出される場合のみ発生します。</span><span class="sxs-lookup"><span data-stu-id="57979-106">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="57979-107">詳細については、[ユーザー定義関数をインラインで呼び出す](how-to-call-user-defined-functions-inline.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57979-107">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57979-108">例</span><span class="sxs-lookup"><span data-stu-id="57979-108">Example</span></span>  

 <span data-ttu-id="57979-109">次の SQL コードは、スカラー値のユーザー定義関数 `ReverseCustName()` を示しています。</span><span class="sxs-lookup"><span data-stu-id="57979-109">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="57979-110">このコードで、次のようなクライアント メソッドを対応付けます。</span><span class="sxs-lookup"><span data-stu-id="57979-110">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="57979-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="57979-111">See also</span></span>

- [<span data-ttu-id="57979-112">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="57979-112">User-Defined Functions</span></span>](user-defined-functions.md)
