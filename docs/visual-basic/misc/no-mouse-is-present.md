---
description: 詳細については、「マウスが存在しません」を参照してください。
title: マウスが存在しません
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 1964f1def655a1e38ce2b8919a69ab2e6ac929a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479128"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="b06f3-103">マウスが存在しません</span><span class="sxs-lookup"><span data-stu-id="b06f3-103">No mouse is present</span></span>

<span data-ttu-id="b06f3-104">`My.Computer.Mouse` オブジェクトのいずれかのプロパティが呼び出されましたが、コンピューターにマウスが接続されていないか、マウス ポートが取り付けられていません。</span><span class="sxs-lookup"><span data-stu-id="b06f3-104">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b06f3-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b06f3-105">To correct this error</span></span>  
  
- <span data-ttu-id="b06f3-106">`Try...Catch` オブジェクトのプロパティの呼び出しを、 `My.Computer.Mouse` ブロックで囲みます。</span><span class="sxs-lookup"><span data-stu-id="b06f3-106">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="b06f3-107">または</span><span class="sxs-lookup"><span data-stu-id="b06f3-107">— or —</span></span>  
  
- <span data-ttu-id="b06f3-108">マウスをコンピューターに取り付けます。</span><span class="sxs-lookup"><span data-stu-id="b06f3-108">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06f3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b06f3-109">See also</span></span>

- [<span data-ttu-id="b06f3-110">My.Computer.Mouse</span><span class="sxs-lookup"><span data-stu-id="b06f3-110">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="b06f3-111">.NET での例外の処理とスロー</span><span class="sxs-lookup"><span data-stu-id="b06f3-111">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="b06f3-112">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="b06f3-112">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
