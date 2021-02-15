---
description: 詳細については、「引数 ' Life ' を0にすることはできません
title: 引数 'Life' を 0 にすることはできません
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: e07c31ab73d6ad3f055adcbf7f4f67d48311c6cd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474877"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="3e12d-103">引数 'Life' を 0 にすることはできません</span><span class="sxs-lookup"><span data-stu-id="3e12d-103">Argument 'Life' cannot be zero</span></span>

<span data-ttu-id="3e12d-104">`Life`の引数が正しくありません。これは、資産の耐用年数を指定する `Double` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e12d-104">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3e12d-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3e12d-105">To correct this error</span></span>  
  
- <span data-ttu-id="3e12d-106">式の引数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e12d-106">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="3e12d-107">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3e12d-107">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="3e12d-108">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="3e12d-108">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e12d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e12d-109">See also</span></span>

- [<span data-ttu-id="3e12d-110">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="3e12d-110">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
