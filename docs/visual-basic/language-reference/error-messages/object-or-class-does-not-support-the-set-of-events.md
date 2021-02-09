---
description: '詳細情報: オブジェクトまたはクラスがこのイベント セットをサポートしていません。'
title: オブジェクトまたはクラスがこのイベント セットをサポートしていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: f13d47a6bb75a5e8394f5344b954afa523bedab3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795601"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="93016-103">オブジェクトまたはクラスがこのイベント セットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="93016-103">Object or class does not support the set of events</span></span>

<span data-ttu-id="93016-104">指定されたイベント セットのイベント ソースとして機能しないコンポーネントで、`WithEvents` 変数を使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="93016-104">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="93016-105">たとえば、オブジェクトのイベントをシンクしてから、最初のオブジェクトを `Implements` する別のオブジェクトを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="93016-105">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="93016-106">実装されたオブジェクトからイベントをシンクできると思うかもしれませんが、常にそうであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="93016-106">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="93016-107">`Implements` は、メソッドとプロパティのインターフェイスのみを実装します。</span><span class="sxs-lookup"><span data-stu-id="93016-107">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="93016-108">`WithEvents` は、`ObjectEvent` を発生させるために必要な型情報が実行時に使用できないため、非公開の `UserControls` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="93016-108">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="93016-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="93016-109">To correct this error</span></span>

- <span data-ttu-id="93016-110">イベントを発生させないコンポーネントのイベントをシンクすることはできません。</span><span class="sxs-lookup"><span data-stu-id="93016-110">You cannot sink events for a component that does not source events.</span></span>

## <a name="see-also"></a><span data-ttu-id="93016-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="93016-111">See also</span></span>

- [<span data-ttu-id="93016-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="93016-112">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="93016-113">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="93016-113">Implements Statement</span></span>](../statements/implements-statement.md)
