---
description: '詳細情報: 方法:カスタム イベントを宣言してブロックを回避する (Visual Basic)'
title: '方法: カスタム イベントを宣言してブロックを回避する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a4ad3162e8f95ebbf7567d427ea00060b19b2235
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469722"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="912ee-103">方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="912ee-103">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>

<span data-ttu-id="912ee-104">場合によっては、あるイベント ハンドラーにより後続のイベント ハンドラーがブロックされないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="912ee-104">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="912ee-105">カスタム イベントを使用すると、イベントでそのイベント ハンドラーを非同期的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="912ee-105">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="912ee-106">既定では、イベント宣言用のバッキングストア フィールドは、すべてのイベント ハンドラーを連続的にまとめたマルチキャスト デリゲートになります。</span><span class="sxs-lookup"><span data-stu-id="912ee-106">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="912ee-107">つまり、あるハンドラーの完了までに長時間かかる場合、他のハンドラーはこのハンドラーが完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="912ee-107">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="912ee-108">(動作が適切なイベント ハンドラーであれば、実行時間が長期間にわたったり、操作をブロックする可能性が出たりすることはありません。)</span><span class="sxs-lookup"><span data-stu-id="912ee-108">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="912ee-109">Visual Basic に備わっている既定のイベント実装ではなく、カスタム イベントを使用することで、イベント ハンドラーを非同期的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="912ee-109">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="912ee-110">例</span><span class="sxs-lookup"><span data-stu-id="912ee-110">Example</span></span>  

 <span data-ttu-id="912ee-111">次の例では、`EventHandlerList` フィールドに格納されている <xref:System.Collections.ArrayList> に対して、`AddHandler` アクセサーで `Click` イベントの各ハンドラーのデリゲートを追加しています。</span><span class="sxs-lookup"><span data-stu-id="912ee-111">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="912ee-112">コードで `Click` イベントが発生すると、`RaiseEvent` アクセサーにより、すべてのイベント ハンドラーのデリゲートが <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> メソッドで非同期的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="912ee-112">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="912ee-113">このメソッドは各ハンドラーをワーカー スレッドで呼び出してすぐに返すため、ハンドラーどうしがブロックし合うことはありません。</span><span class="sxs-lookup"><span data-stu-id="912ee-113">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="912ee-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="912ee-114">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="912ee-115">イベント</span><span class="sxs-lookup"><span data-stu-id="912ee-115">Events</span></span>](index.md)
- [<span data-ttu-id="912ee-116">方法: カスタム イベントを宣言してメモリを節約する</span><span class="sxs-lookup"><span data-stu-id="912ee-116">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)
