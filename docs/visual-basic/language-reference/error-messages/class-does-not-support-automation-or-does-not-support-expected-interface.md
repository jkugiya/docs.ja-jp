---
description: '詳細情報: クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。'
title: クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: c173eeddf3a34d6af169b91066199ce7d03cf4ba
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106632"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="cb432-103">クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cb432-103">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="cb432-104">`GetObject` 関数呼び出しまたは `CreateObject` 関数呼び出しで指定したクラスが外部からプログラム可能なインターフェイスを公開していません。あるいは、.dll から .exe へ、または .exe から .dll へプロジェクトを変更しました。</span><span class="sxs-lookup"><span data-stu-id="cb432-104">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb432-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cb432-105">To correct this error</span></span>  
  
1. <span data-ttu-id="cb432-106">オブジェクトを作成したアプリケーションのドキュメントを参照して、このクラスのオブジェクトでオートメーションを使用する上での制限を確認します。</span><span class="sxs-lookup"><span data-stu-id="cb432-106">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="cb432-107">.dll から .exe へ、または .exe から .dll へプロジェクトを変更した場合は、古い .dll または .exe を手動で登録解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb432-107">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb432-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb432-108">See also</span></span>

- [<span data-ttu-id="cb432-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="cb432-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="cb432-110">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="cb432-110">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
