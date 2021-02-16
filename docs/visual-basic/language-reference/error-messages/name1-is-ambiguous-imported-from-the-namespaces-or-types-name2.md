---
description: '詳細情報: BC30561: "<name1>" 名前空間または型からインポートされた "<name2>" があいまいです。'
title: "'<name1>' 名前空間または型からインポートされた '<name2>' があいまいです。"
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: d338d16c563be988c215dd19ac59174d79a8c7a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483574"
---
# <a name="bc30561-name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="e46dd-103">BC30561: "\<name1>" 名前空間または型からインポートされた "\<name2>" があいまいです。</span><span class="sxs-lookup"><span data-stu-id="e46dd-103">BC30561: '\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>

<span data-ttu-id="e46dd-104">あいまいな名前を指定したため、別の名前と競合しています。</span><span class="sxs-lookup"><span data-stu-id="e46dd-104">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="e46dd-105">Visual Basic コンパイラには、競合解決規則がありません。ユーザー自身が名前のあいまいさを解消する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46dd-105">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>

 <span data-ttu-id="e46dd-106">**エラー ID:** BC30561</span><span class="sxs-lookup"><span data-stu-id="e46dd-106">**Error ID:** BC30561</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e46dd-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e46dd-107">To correct this error</span></span>

- <span data-ttu-id="e46dd-108">名前空間のインポートを削除して、名前のあいまいさをなくします。</span><span class="sxs-lookup"><span data-stu-id="e46dd-108">Disambiguate the name by removing namespace imports.</span></span>

- <span data-ttu-id="e46dd-109">名前を完全修飾します。</span><span class="sxs-lookup"><span data-stu-id="e46dd-109">Fully qualify the name.</span></span>

## <a name="see-also"></a><span data-ttu-id="e46dd-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e46dd-110">See also</span></span>

- [<span data-ttu-id="e46dd-111">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="e46dd-111">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="e46dd-112">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="e46dd-112">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="e46dd-113">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="e46dd-113">Namespace Statement</span></span>](../statements/namespace-statement.md)
