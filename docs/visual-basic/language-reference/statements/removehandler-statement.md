---
description: '詳細情報: RemoveHandler ステートメント'
title: RemoveHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 699db9edfc029b4149246e8b654645040ae6d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741303"
---
# <a name="removehandler-statement"></a><span data-ttu-id="f8c03-103">RemoveHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8c03-103">RemoveHandler Statement</span></span>

<span data-ttu-id="f8c03-104">イベントとイベント ハンドラー間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="f8c03-104">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c03-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8c03-105">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="f8c03-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="f8c03-106">Parts</span></span>  
  
|<span data-ttu-id="f8c03-107">用語</span><span class="sxs-lookup"><span data-stu-id="f8c03-107">Term</span></span>|<span data-ttu-id="f8c03-108">定義</span><span class="sxs-lookup"><span data-stu-id="f8c03-108">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="f8c03-109">処理されるイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="f8c03-109">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="f8c03-110">イベントを現在処理しているプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="f8c03-110">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8c03-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8c03-111">Remarks</span></span>  

 <span data-ttu-id="f8c03-112">`AddHandler` および `RemoveHandler` ステートメントを使用すると、プログラムの実行中に、特定のイベントのイベント処理をいつでも開始および停止できます。</span><span class="sxs-lookup"><span data-stu-id="f8c03-112">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8c03-113">カスタム イベントの場合は、`RemoveHandler` ステートメントによってイベントの `RemoveHandler` アクセサーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f8c03-113">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="f8c03-114">カスタム イベントの詳細については、「[Event ステートメント](event-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8c03-114">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c03-115">例</span><span class="sxs-lookup"><span data-stu-id="f8c03-115">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f8c03-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8c03-116">See also</span></span>

- [<span data-ttu-id="f8c03-117">AddHandler ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8c03-117">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="f8c03-118">Handles</span><span class="sxs-lookup"><span data-stu-id="f8c03-118">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="f8c03-119">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="f8c03-119">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="f8c03-120">イベント</span><span class="sxs-lookup"><span data-stu-id="f8c03-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
