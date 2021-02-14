---
description: "詳細情報: BC30941:構造体 '<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません"
title: 構造体 '<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 08596997decd9d739ac95ad3e4191cb126b3efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641448"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="781e1-103">BC30941:構造体 '\<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。</span><span class="sxs-lookup"><span data-stu-id="781e1-103">BC30941: Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="781e1-104">構造体の定義には、非共有の変数または非共有の非カスタム イベントは含まれません。</span><span class="sxs-lookup"><span data-stu-id="781e1-104">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>

 <span data-ttu-id="781e1-105">すべての構造体には、すべてのインスタンスに対して集合的に ([Shared](../modifiers/shared.md)) ではなく、特定の各インスタンスに対して (非共有) 適用される変数またはイベントが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="781e1-105">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="781e1-106">非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。</span><span class="sxs-lookup"><span data-stu-id="781e1-106">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="781e1-107">さらに、非共有の変数がなく、1 つの非共有イベントのみが存在する場合、そのイベントを `Custom` イベントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="781e1-107">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>

 <span data-ttu-id="781e1-108">**エラー ID:** BC30941</span><span class="sxs-lookup"><span data-stu-id="781e1-108">**Error ID:** BC30941</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="781e1-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="781e1-109">To correct this error</span></span>

- <span data-ttu-id="781e1-110">`Shared` ではない変数またはイベントを少なくとも 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="781e1-110">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="781e1-111">イベントを 1 つだけ定義する場合、非共有にするだけでなく、非カスタムにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="781e1-111">If you define only one event, it must be noncustom as well as nonshared.</span></span>

## <a name="see-also"></a><span data-ttu-id="781e1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="781e1-112">See also</span></span>

- [<span data-ttu-id="781e1-113">構造体</span><span class="sxs-lookup"><span data-stu-id="781e1-113">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="781e1-114">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="781e1-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="781e1-115">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="781e1-115">Structure Statement</span></span>](../statements/structure-statement.md)
