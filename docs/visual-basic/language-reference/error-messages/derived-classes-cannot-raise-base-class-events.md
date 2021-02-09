---
description: '詳細情報: BC30029:派生クラスで基本クラスのイベントを発生させることはできません。'
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 68546f2654f7c34fcb309d5af68e237d5f1eac79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796601"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="8abef-103">BC30029:派生クラスで基本クラスのイベントを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="8abef-103">BC30029: Derived classes cannot raise base class events</span></span>

<span data-ttu-id="8abef-104">イベントを発生させることができるのは、それが宣言されている宣言領域からのみです。</span><span class="sxs-lookup"><span data-stu-id="8abef-104">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="8abef-105">そのため、クラスは、派生元のクラスであっても、他のクラスからイベントを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="8abef-105">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>

 <span data-ttu-id="8abef-106">**エラー ID:** BC30029</span><span class="sxs-lookup"><span data-stu-id="8abef-106">**Error ID:** BC30029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8abef-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8abef-107">To correct this error</span></span>

- <span data-ttu-id="8abef-108">`Event` ステートメントまたは `RaiseEvent` ステートメントが同じクラス内になるように移動します。</span><span class="sxs-lookup"><span data-stu-id="8abef-108">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8abef-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8abef-109">See also</span></span>

- [<span data-ttu-id="8abef-110">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="8abef-110">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="8abef-111">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="8abef-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
