---
description: '詳細情報: 内部エラーのため、完全な操作システム名を取得できませんでした'
title: 内部エラーのために完全な運用システム名を取得できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: d274a08728b084b21309862de69e2fded5c164da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463495"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="fcf7c-103">内部エラーのために完全な運用システム名を取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="fcf7c-103">Could not obtain full operation system name due to internal error</span></span>

<span data-ttu-id="fcf7c-104">内部エラーのために完全な運用システム名を取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-104">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="fcf7c-105">これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-105">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="fcf7c-106">`My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-106">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="fcf7c-107">このエラーの考えられる原因は、Windows Management Instrumentation (WMI) が、現在のコンピューターにインストールされていないことです。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-107">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fcf7c-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fcf7c-108">To correct this error</span></span>  
  
1. <span data-ttu-id="fcf7c-109">`Try...Catch` プロパティの呼び出しの周囲に `My.Computer.Info.OSFullName` ブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-109">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="fcf7c-110">WMI とそのインストール方法の詳細については、「」にアクセスし、「Windows Management Instrumentation Core」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="fcf7c-110">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf7c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcf7c-111">See also</span></span>

- [<span data-ttu-id="fcf7c-112">マイ. Computer. Info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="fcf7c-112">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="fcf7c-113">.NET での例外の処理とスロー</span><span class="sxs-lookup"><span data-stu-id="fcf7c-113">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="fcf7c-114">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="fcf7c-114">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
