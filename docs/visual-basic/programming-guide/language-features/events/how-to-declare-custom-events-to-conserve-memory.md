---
description: '詳細情報: 方法:カスタム イベントを宣言してメモリを節約する (Visual Basic)'
title: '方法: カスタム イベントを宣言してメモリを節約する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 7371ec3df41ad0efd4598e0902f6937881d1e1a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460086"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="31ad1-103">方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31ad1-103">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>

<span data-ttu-id="31ad1-104">場合によっては、アプリのメモリ使用量を抑えなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="31ad1-104">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="31ad1-105">カスタム イベントを使用すると、アプリケーションが使用するメモリを、処理するイベントのものだけに制限できます。</span><span class="sxs-lookup"><span data-stu-id="31ad1-105">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="31ad1-106">既定では、クラスでイベントを宣言すると、メモリがそのイベント情報を格納するフィールドにコンパイラにより割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="31ad1-106">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="31ad1-107">使用されないイベントがクラスに多数含まれている場合、これらによって不必要にメモリが占有されることになります。</span><span class="sxs-lookup"><span data-stu-id="31ad1-107">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="31ad1-108">Visual Basic に備わっている既定のイベント実装ではなく、カスタム イベントを使用することで、メモリ使用量を細かく管理できます。</span><span class="sxs-lookup"><span data-stu-id="31ad1-108">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31ad1-109">例</span><span class="sxs-lookup"><span data-stu-id="31ad1-109">Example</span></span>  

 <span data-ttu-id="31ad1-110">次の例のクラスでは、`Events` フィールドに格納される <xref:System.ComponentModel.EventHandlerList> のインスタンス 1 つを使用して、使用中のイベントに関する情報を格納しています。</span><span class="sxs-lookup"><span data-stu-id="31ad1-110">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="31ad1-111"><xref:System.ComponentModel.EventHandlerList> クラスは、デリゲートの保持向けに最適化された list クラスです。</span><span class="sxs-lookup"><span data-stu-id="31ad1-111">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="31ad1-112">このクラスのイベントはすべて、`Events` フィールドを使用して、各イベントを処理しているメソッドを追跡します。</span><span class="sxs-lookup"><span data-stu-id="31ad1-112">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="31ad1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="31ad1-113">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="31ad1-114">イベント</span><span class="sxs-lookup"><span data-stu-id="31ad1-114">Events</span></span>](index.md)
- [<span data-ttu-id="31ad1-115">方法: カスタム イベントを宣言してブロックを回避する</span><span class="sxs-lookup"><span data-stu-id="31ad1-115">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
