---
description: '詳細情報: DLL を正しく呼び出せません。'
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 7e98ce5131d440a12bff4a4630da087102bdc4da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797095"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="128c7-103">DLL を正しく呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="128c7-103">Bad DLL calling convention</span></span>

<span data-ttu-id="128c7-104">ダイナミック リンク ライブラリ (DLL) に渡される引数は、ルーチンによって予期されるものと完全に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="128c7-104">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="128c7-105">呼び出し規則は、引数の数、型、および順序を扱います。</span><span class="sxs-lookup"><span data-stu-id="128c7-105">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="128c7-106">プログラムが DLL 内のルーチンを呼び出しているときに、間違った型または数の引数が渡されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="128c7-106">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="128c7-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="128c7-107">To correct this error</span></span>  
  
1. <span data-ttu-id="128c7-108">すべての引数の型が、呼び出しているルーチンの宣言で指定されている型と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="128c7-108">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="128c7-109">呼び出しているルーチンの宣言で指定したものと同じ数の引数を渡していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="128c7-109">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="128c7-110">DLL ルーチンが値渡しの引数を予期している場合は、ルーチンの宣言でこれらの引数に `ByVal` が指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="128c7-110">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128c7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="128c7-111">See also</span></span>

- [<span data-ttu-id="128c7-112">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="128c7-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="128c7-113">Call ステートメント</span><span class="sxs-lookup"><span data-stu-id="128c7-113">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="128c7-114">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="128c7-114">Declare Statement</span></span>](../statements/declare-statement.md)
