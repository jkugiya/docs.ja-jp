---
description: '詳細情報: オートメーション エラーです。'
title: オートメーション エラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: bf3e61bb9b8fec9a831d211b70abdca322c1fe06
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106606"
---
# <a name="automation-error"></a><span data-ttu-id="95c1a-103">オートメーション エラーです。</span><span class="sxs-lookup"><span data-stu-id="95c1a-103">Automation error</span></span>

<span data-ttu-id="95c1a-104">メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="95c1a-104">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="95c1a-105">エラーは、オブジェクトを作成したアプリケーションによって報告されました。</span><span class="sxs-lookup"><span data-stu-id="95c1a-105">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95c1a-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="95c1a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="95c1a-107">`Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。</span><span class="sxs-lookup"><span data-stu-id="95c1a-107">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="95c1a-108">アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="95c1a-108">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c1a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="95c1a-109">See also</span></span>

- [<span data-ttu-id="95c1a-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="95c1a-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="95c1a-111">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="95c1a-111">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
