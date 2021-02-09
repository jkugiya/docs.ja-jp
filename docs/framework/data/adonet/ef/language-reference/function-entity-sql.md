---
description: '詳細情報: FUNCTION (Entity SQL)'
title: FUNCTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: d61aafce03dc7b82b678f1eb107afb79c6c3ed2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786317"
---
# <a name="function-entity-sql"></a><span data-ttu-id="c8bb5-103">FUNCTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c8bb5-103">FUNCTION (Entity SQL)</span></span>

<span data-ttu-id="c8bb5-104">Entity SQL クエリ コマンドのスコープに関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-104">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8bb5-105">構文</span><span class="sxs-lookup"><span data-stu-id="c8bb5-105">Syntax</span></span>  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>
        [ ,...n ]  
  ]  
) AS ( function_expression )
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )
                | REF ( data_type )
                | ROW ( row_expression )
        }
```  
  
## <a name="arguments"></a><span data-ttu-id="c8bb5-106">引数</span><span class="sxs-lookup"><span data-stu-id="c8bb5-106">Arguments</span></span>  

 `function-name`  
 <span data-ttu-id="c8bb5-107">関数名。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-107">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="c8bb5-108">関数のパラメーター名。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-108">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="c8bb5-109">関数である有効な Entity SQL 式。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-109">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="c8bb5-110">関数内のコマンドは、関数に渡される `parameter_name` パラメーターに基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-110">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="c8bb5-111">サポートされる型の名前。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-111">Name of a supported type.</span></span>  
  
 <span data-ttu-id="c8bb5-112">COLLECTION ( <型の定義`>` )</span><span class="sxs-lookup"><span data-stu-id="c8bb5-112">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="c8bb5-113">サポートされる型、行、または参照のコレクションを返す式。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-113">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="c8bb5-114">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="c8bb5-114">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="c8bb5-115">エンティティ型への参照を返す式。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-115">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="c8bb5-116">ROW **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="c8bb5-116">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="c8bb5-117">1 つまたは複数の値から構造的に型指定された匿名レコードを返す式。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-117">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="c8bb5-118">詳細については、「 [ROW](row-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-118">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8bb5-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8bb5-119">Remarks</span></span>  

 <span data-ttu-id="c8bb5-120">関数のシグネチャが異なっていれば、名前が同じ複数の関数をインラインで宣言することは可能です。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-120">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="c8bb5-121">詳細については、「 [Function Overload Resolution](function-overload-resolution-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-121">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c8bb5-122">関数がインラインである場合、Entity SQL コマンドに呼び出せるのは、そのコマンド内で定義された後のみです。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-122">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="c8bb5-123">ただし、インライン関数を別のインライン関数内で呼び出す場合には、呼び出される関数が定義される前でも後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-123">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="c8bb5-124">次の例では、関数 B が定義される前に、関数 A が関数 B を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-124">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="c8bb5-125">詳細については、[ユーザー定義関数を呼び出す](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-125">For more information, see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="c8bb5-126">関数をモデル自体で宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-126">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="c8bb5-127">モデルで宣言された関数は、コマンドでインラインで宣言された関数と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-127">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="c8bb5-128">詳しくは、「[ユーザー定義関数](user-defined-functions-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-128">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8bb5-129">例</span><span class="sxs-lookup"><span data-stu-id="c8bb5-129">Example</span></span>  

 <span data-ttu-id="c8bb5-130">次の Entity SQL コマンドは、関数 `Products` を定義します。この関数は、整数値を受け取って、返された製品をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-130">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="c8bb5-131">例</span><span class="sxs-lookup"><span data-stu-id="c8bb5-131">Example</span></span>  

 <span data-ttu-id="c8bb5-132">次の Entity SQL コマンドは、関数 `StringReturnsCollection` を定義します。この関数は、文字列のコレクションを受け取って、返された連絡先をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-132">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="c8bb5-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8bb5-133">See also</span></span>

- [<span data-ttu-id="c8bb5-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c8bb5-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c8bb5-135">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="c8bb5-135">Entity SQL Language</span></span>](entity-sql-language.md)
