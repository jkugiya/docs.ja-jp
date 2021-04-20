---
description: '詳細情報: 内部エラーのため、メモリ情報を取得できませんでした'
title: 内部エラーのため、メモリ情報を取得できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: 08e85371f19f1e6e365e201c1a43bd679d7847e6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463483"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="f2993-103">内部エラーのため、メモリ情報を取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="f2993-103">Could not obtain memory information due to internal error</span></span>

<span data-ttu-id="f2993-104">`My.Computer.Info` オブジェクトのメモリ情報のプロパティの 1 つに対する呼び出しが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f2993-104">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2993-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f2993-105">To correct this error</span></span>  
  
- <span data-ttu-id="f2993-106">`Try...Catch` オブジェクトのメモリ情報プロパティへの呼び出しの周囲に `My.Computer.Info` を追加します。</span><span class="sxs-lookup"><span data-stu-id="f2993-106">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2993-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2993-107">See also</span></span>

- [<span data-ttu-id="f2993-108">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="f2993-108">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [<span data-ttu-id="f2993-109">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="f2993-109">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
