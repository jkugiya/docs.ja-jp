---
description: '詳細情報: オートメーション エラーです。'
title: オートメーション エラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: e4d283b16b4c54e2488fedfc58d3c881cf6b0218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797121"
---
# <a name="automation-error"></a><span data-ttu-id="e5cc3-103">オートメーション エラーです。</span><span class="sxs-lookup"><span data-stu-id="e5cc3-103">Automation error</span></span>

<span data-ttu-id="e5cc3-104">メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e5cc3-104">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="e5cc3-105">エラーは、オブジェクトを作成したアプリケーションによって報告されました。</span><span class="sxs-lookup"><span data-stu-id="e5cc3-105">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5cc3-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e5cc3-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e5cc3-107">`Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。</span><span class="sxs-lookup"><span data-stu-id="e5cc3-107">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="e5cc3-108">アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="e5cc3-108">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cc3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5cc3-109">See also</span></span>

- [<span data-ttu-id="e5cc3-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="e5cc3-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="e5cc3-111">ご意見</span><span class="sxs-lookup"><span data-stu-id="e5cc3-111">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
