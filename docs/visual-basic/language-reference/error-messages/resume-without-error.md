---
description: '詳細情報: エラーが発生していないときに Resume を実行することはできません。'
title: エラーが発生していないときに Resume を実行することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792012"
---
# <a name="resume-without-error"></a><span data-ttu-id="f5310-103">エラーが発生していないときに Resume を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5310-103">Resume without error</span></span>

<span data-ttu-id="f5310-104">`Resume` ステートメントがエラー処理コードの外側に記述されていたか、エラーが発生していない場合でもコードがエラー ハンドラーにジャンプしました。</span><span class="sxs-lookup"><span data-stu-id="f5310-104">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5310-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f5310-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f5310-106">`Resume` ステートメントをエラー ハンドラー内に移動するか、または削除します。</span><span class="sxs-lookup"><span data-stu-id="f5310-106">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="f5310-107">プロシージャ間でラベルにジャンプすることはできないため、プロシージャでエラー ハンドラーを識別するラベルを検索します。</span><span class="sxs-lookup"><span data-stu-id="f5310-107">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="f5310-108">`On Error GoTo` ステートメントではない `GoTo` ステートメントのターゲットとして重複するラベルが指定されている場合は、その目的のターゲットと一致するように行ラベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="f5310-108">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5310-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5310-109">See also</span></span>

- [<span data-ttu-id="f5310-110">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="f5310-110">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="f5310-111">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="f5310-111">On Error Statement</span></span>](../statements/on-error-statement.md)
