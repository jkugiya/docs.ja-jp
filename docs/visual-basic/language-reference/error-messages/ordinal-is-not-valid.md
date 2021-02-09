---
description: '詳細情報: 序数が有効ではありません。'
title: 序数が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7c58675a08d3821cd05ba0109e5ce0107c68e497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795522"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="d3310-103">序数が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3310-103">Ordinal is not valid</span></span>

<span data-ttu-id="d3310-104">ダイナミック リンク ライブラリ (DLL) への呼び出しが、`#num` 構文を使用して、プロシージャ名の代わりに数値を使用するように指定されています。</span><span class="sxs-lookup"><span data-stu-id="d3310-104">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="d3310-105">このエラーには、次のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="d3310-105">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="d3310-106">`#num` 式を序数に変換しようとして失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d3310-106">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="d3310-107">指定された `#num` が、DLL 内の関数を指定していません。</span><span class="sxs-lookup"><span data-stu-id="d3310-107">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="d3310-108">タイプ ライブラリに無効な宣言が含まれているため、無効な序数が内部で使用されています。</span><span class="sxs-lookup"><span data-stu-id="d3310-108">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3310-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d3310-109">To correct this error</span></span>  
  
1. <span data-ttu-id="d3310-110">式が有効な数値を表していること、または名前によってプロシージャを呼び出していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3310-110">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="d3310-111">`#num` が DLL 内の有効な関数を識別することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3310-111">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="d3310-112">コードをコメント アウトすることで、問題の原因となっているプロシージャ呼び出しを分離します。</span><span class="sxs-lookup"><span data-stu-id="d3310-112">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="d3310-113">プロシージャの `Declare` ステートメントを記述し、その問題をタイプ ライブラリのベンダーに報告します。</span><span class="sxs-lookup"><span data-stu-id="d3310-113">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3310-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3310-114">See also</span></span>

- [<span data-ttu-id="d3310-115">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="d3310-115">Declare Statement</span></span>](../statements/declare-statement.md)
