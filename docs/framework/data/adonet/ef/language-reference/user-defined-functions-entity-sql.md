---
description: '詳細情報: ユーザー定義関数 (Entity SQL)'
title: ユーザー定義関数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: b5ebff087da08530e13f301e58509ba2d90c3605
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673207"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="a60bb-103">ユーザー定義関数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a60bb-103">User-Defined Functions (Entity SQL)</span></span>

<span data-ttu-id="a60bb-104">Entity SQL では、クエリ内でのユーザー定義関数の呼び出しがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-104">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="a60bb-105">これらの関数は、クエリを使用してインラインで定義する (「[方法:ユーザー定義関数を呼び出す](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))」を参照) ことも、概念モデルの一部として定義する (「[方法:概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照) こともできます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-105">You can define these functions inline with the query (see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="a60bb-106">概念モデル関数は、概念モデルの [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) 要素の [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) 要素における Entity SQL コマンドとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-106">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="a60bb-107">Entity SQL を使用すると、関数をクエリ コマンド自体で定義することができます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-107">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="a60bb-108">[FUNCTION](function-entity-sql.md) 演算子では、インライン関数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-108">The [FUNCTION](function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="a60bb-109">複数の関数を 1 つのコマンドで定義することができます。関数の署名が一意であれば、これら複数の関数に同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a60bb-109">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="a60bb-110">詳細については、「 [Function Overload Resolution](function-overload-resolution-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a60bb-110">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60bb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a60bb-111">See also</span></span>

- [<span data-ttu-id="a60bb-112">関数</span><span class="sxs-lookup"><span data-stu-id="a60bb-112">Functions</span></span>](functions-entity-sql.md)
