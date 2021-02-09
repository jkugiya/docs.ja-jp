---
description: '詳細情報: AddHandler ステートメント'
title: AddHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c0c34abd7ff225765ab36278825a555e2b84b0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674104"
---
# <a name="addhandler-statement"></a><span data-ttu-id="86c95-103">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="86c95-103">AddHandler Statement</span></span>

<span data-ttu-id="86c95-104">実行時にイベントをイベント ハンドラーに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="86c95-104">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c95-105">構文</span><span class="sxs-lookup"><span data-stu-id="86c95-105">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="86c95-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="86c95-106">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="86c95-107">event</span><span class="sxs-lookup"><span data-stu-id="86c95-107">event</span></span>|<span data-ttu-id="86c95-108">処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="86c95-108">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="86c95-109">イベントを処理するプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="86c95-109">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="86c95-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="86c95-110">Remarks</span></span>  

 <span data-ttu-id="86c95-111">`AddHandler` および `RemoveHandler` ステートメントを使用すると、プログラムの実行中にいつでもイベント処理を開始および停止できます。</span><span class="sxs-lookup"><span data-stu-id="86c95-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="86c95-112">`eventhandler` プロシージャのシグネチャは、イベント `event` のシグネチャと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86c95-112">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="86c95-113">`Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。</span><span class="sxs-lookup"><span data-stu-id="86c95-113">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="86c95-114">`AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="86c95-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="86c95-115">`Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="86c95-115">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="86c95-116">詳細については、「[Handles](handles-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86c95-116">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86c95-117">カスタム イベントの場合は、`AddHandler` ステートメントによってイベントの `AddHandler` アクセサーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86c95-117">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="86c95-118">カスタム イベントの詳細については、「[Event ステートメント](event-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86c95-118">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86c95-119">例</span><span class="sxs-lookup"><span data-stu-id="86c95-119">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="86c95-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="86c95-120">See also</span></span>

- [<span data-ttu-id="86c95-121">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="86c95-121">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="86c95-122">Handles</span><span class="sxs-lookup"><span data-stu-id="86c95-122">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="86c95-123">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="86c95-123">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="86c95-124">イベント</span><span class="sxs-lookup"><span data-stu-id="86c95-124">Events</span></span>](../../programming-guide/language-features/events/index.md)
