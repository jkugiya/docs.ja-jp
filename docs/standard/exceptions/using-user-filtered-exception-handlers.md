---
title: ユーザー フィルター例外ハンドラーを使用する
description: C# および Visual Basic でユーザー フィルター例外ハンドラーを使用する方法について説明します。
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512672"
---
# <a name="use-user-filtered-exception-handlers"></a><span data-ttu-id="0b34b-103">ユーザー フィルター例外ハンドラーを使用する</span><span class="sxs-lookup"><span data-stu-id="0b34b-103">Use user-filtered exception handlers</span></span>

<span data-ttu-id="0b34b-104">ユーザー フィルター例外ハンドラーは、ユーザーが例外に対して定義した要件に基づいて、例外をキャッチして処理します。</span><span class="sxs-lookup"><span data-stu-id="0b34b-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="0b34b-105">これらのハンドラーからは、`catch` ステートメントが `when` キーワード (Visual Basic では `Catch` と `When`) と共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0b34b-105">These handlers use the `catch` statement with the `when` keyword (`Catch` and `When` in Visual Basic).</span></span>  
  
 <span data-ttu-id="0b34b-106">この手法は、特定の例外オブジェクトが複数のエラーに対応する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0b34b-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="0b34b-107">その場合、オブジェクトには通常、エラーに関連付けられた特定のエラー コードが格納されているプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0b34b-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="0b34b-108">エラー コード プロパティを式で使用すると、その `catch` 句で処理する特定のエラーだけを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="0b34b-108">You can use the error code property in the expression to select only the particular error you want to handle in that `catch` clause.</span></span>  
  
 <span data-ttu-id="0b34b-109">`catch`/`when` ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0b34b-109">The following example illustrates the `catch`/`when` statement.</span></span>

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="0b34b-110">ユーザー フィルター句の式が制限されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0b34b-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="0b34b-111">ユーザー フィルター式の実行中に例外が発生した場合、その例外は破棄され、フィルター式は false と評価されたものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="0b34b-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="0b34b-112">その場合、共通言語ランタイムは、現在の例外に対応するハンドラーの検索を継続します。</span><span class="sxs-lookup"><span data-stu-id="0b34b-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="0b34b-113">特定の例外とユーザー フィルター句の結合</span><span class="sxs-lookup"><span data-stu-id="0b34b-113">Combine the specific exception and the user-filtered clauses</span></span>  

 <span data-ttu-id="0b34b-114">`catch` ステートメントには、特定の例外とユーザー フィルター句の両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0b34b-114">A `catch` statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="0b34b-115">ランタイムは、最初に特定の例外をテストします。</span><span class="sxs-lookup"><span data-stu-id="0b34b-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="0b34b-116">特定の例外がテストを通過すると、ランタイムはユーザー フィルターを実行します。</span><span class="sxs-lookup"><span data-stu-id="0b34b-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="0b34b-117">汎用フィルターには、クラス フィルターで宣言されている変数への参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0b34b-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="0b34b-118">なお、2 つのフィルター句の順序をが逆にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0b34b-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="0b34b-119">次の例は、特定の例外が指定された **catch** ステートメントと、**when** キーワードを使用したユーザー フィルター句を示しています。</span><span class="sxs-lookup"><span data-stu-id="0b34b-119">The following example shows a specific exception in the **catch** statement as well as the user-filtered clause using the **when** keyword.</span></span>  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="0b34b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b34b-120">See also</span></span>

- [<span data-ttu-id="0b34b-121">例外</span><span class="sxs-lookup"><span data-stu-id="0b34b-121">Exceptions</span></span>](index.md)
