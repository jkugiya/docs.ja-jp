---
description: '詳細情報: Alias 句 (Visual Basic)'
title: Alias 句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: bf0ee1c22105b29aedb99ce45a99ba866f4b93c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674078"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="d6c99-103">Alias 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6c99-103">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="d6c99-104">外部プロシージャがその DLL で別の名前を使用することを示します。</span><span class="sxs-lookup"><span data-stu-id="d6c99-104">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c99-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="d6c99-105">Remarks</span></span>  

 <span data-ttu-id="d6c99-106">`Alias` キーワードは次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6c99-106">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="d6c99-107">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="d6c99-107">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="d6c99-108">次の例では、`Alias` キーワードを使用して、advapi32.dll 内の関数の名前 `GetUserNameA` を指定しています。この例では代わりに `getUserName` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="d6c99-108">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="d6c99-109">関数 `getUserName` はサブ `getUser` で呼び出され、それによって現在のユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6c99-109">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="d6c99-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6c99-110">See also</span></span>

- [<span data-ttu-id="d6c99-111">キーワード</span><span class="sxs-lookup"><span data-stu-id="d6c99-111">Keywords</span></span>](../keywords/index.md)
