---
description: '詳細情報: ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした'
title: ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 5fb0bf1d761faf9d3d0c64e8815e28e14841b1fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463521"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="c1164-103">ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした</span><span class="sxs-lookup"><span data-stu-id="c1164-103">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="c1164-104">循環操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c1164-104">A cyclic operation has failed.</span></span> <span data-ttu-id="c1164-105">循環操作は循環しているため、完了できません。</span><span class="sxs-lookup"><span data-stu-id="c1164-105">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="c1164-106">たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="c1164-106">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c1164-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c1164-107">To correct this error</span></span>  
  
- <span data-ttu-id="c1164-108">継承を行うときには、参照の循環がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1164-108">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1164-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1164-109">See also</span></span>

- [<span data-ttu-id="c1164-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="c1164-110">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="c1164-111">Visual Studio デバッガーでブレークポイントを使用する</span><span class="sxs-lookup"><span data-stu-id="c1164-111">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
