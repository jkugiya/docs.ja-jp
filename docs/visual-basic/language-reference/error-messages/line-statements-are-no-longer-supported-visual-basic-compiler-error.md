---
description: "詳細情報: BC30830:'Line' ステートメントは現在サポートされていません"
title: "'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 16696856cee365171000e7b0abc206c42d3f3174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795873"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="81145-103">BC30830:'Line' ステートメントは現在サポートされていません</span><span class="sxs-lookup"><span data-stu-id="81145-103">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="81145-104">Line ステートメントは現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="81145-104">Line statements are no longer supported.</span></span> <span data-ttu-id="81145-105">ファイル I/O 機能は `Microsoft.VisualBasic.FileSystem.LineInput` として使用でき、グラフィックス機能は `System.Drawing.Graphics.DrawLine` として使用できます。</span><span class="sxs-lookup"><span data-stu-id="81145-105">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="81145-106">**エラー ID:** BC30830</span><span class="sxs-lookup"><span data-stu-id="81145-106">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="81145-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="81145-107">To correct this error</span></span>

- <span data-ttu-id="81145-108">ファイル アクセスを実行する場合は、`Microsoft.VisualBasic.FileSystem.LineInput` を使用します。</span><span class="sxs-lookup"><span data-stu-id="81145-108">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="81145-109">グラフィックス処理を行っている場合は、 `System.Drawing.Graphics.Drawline`を使用します。</span><span class="sxs-lookup"><span data-stu-id="81145-109">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="81145-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="81145-110">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="81145-111">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="81145-111">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
