---
description: '詳細情報: NULL 値が許容される構造化型 (Entity SQL)'
title: NULL 値が許容される構造化型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: bf303c9cd61fad2c2a8ffedf338bb3a8876db27b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802087"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="7a4e0-103">NULL 値が許容される構造化型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7a4e0-103">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="7a4e0-104">構造化型の `null` インスタンスは、存在しないインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-104">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="7a4e0-105">これは、すべてのプロパティの値が `null` であるインスタンスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-105">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="7a4e0-106">このトピックでは、NULL 値が許容される構造化型について説明します。この内容には、NULL 値が許容される型、および構造化 NULL 値が許容される型の `null` インスタンスを生成するコード パターンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-106">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="7a4e0-107">NULL 値が許容される構造化型の種類</span><span class="sxs-lookup"><span data-stu-id="7a4e0-107">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="7a4e0-108">NULL 値が許容される構造化型には、3 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-108">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="7a4e0-109">行型。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-109">Row types.</span></span>  
  
- <span data-ttu-id="7a4e0-110">複合型。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-110">Complex types.</span></span>  
  
- <span data-ttu-id="7a4e0-111">エンティティ型。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-111">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="7a4e0-112">構造化型の NULL インスタンスを生成するコード パターン</span><span class="sxs-lookup"><span data-stu-id="7a4e0-112">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="7a4e0-113">次のシナリオは、`null` インスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7a4e0-113">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="7a4e0-114">構造化型としての `null` の構造化</span><span class="sxs-lookup"><span data-stu-id="7a4e0-114">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="7a4e0-115">派生型に対する基本データ型のキャスト</span><span class="sxs-lookup"><span data-stu-id="7a4e0-115">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="7a4e0-116">false の条件での外部結合</span><span class="sxs-lookup"><span data-stu-id="7a4e0-116">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="7a4e0-117">--または</span><span class="sxs-lookup"><span data-stu-id="7a4e0-117">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="7a4e0-118">--または</span><span class="sxs-lookup"><span data-stu-id="7a4e0-118">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="7a4e0-119">`null` 参照の逆参照</span><span class="sxs-lookup"><span data-stu-id="7a4e0-119">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="7a4e0-120">空のコレクションからの ANYELEMENT の取得</span><span class="sxs-lookup"><span data-stu-id="7a4e0-120">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="7a4e0-121">構造化型の `null` インスタンスのチェック</span><span class="sxs-lookup"><span data-stu-id="7a4e0-121">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a4e0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a4e0-122">See also</span></span>

- [<span data-ttu-id="7a4e0-123">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="7a4e0-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
