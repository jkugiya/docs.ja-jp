---
description: '詳細情報: ファイルは既に開かれています。'
title: ファイルは既に開かれています。
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 2f3345c15f4a3095a8e733c2c8424edb25b4dee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796302"
---
# <a name="file-already-open"></a><span data-ttu-id="76bd1-103">ファイルは既に開かれています。</span><span class="sxs-lookup"><span data-stu-id="76bd1-103">File already open</span></span>

<span data-ttu-id="76bd1-104">別の `FileOpen` またはその他の操作を実行する前に、ファイルを閉じる必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="76bd1-104">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="76bd1-105">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="76bd1-105">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="76bd1-106">既に開いているファイルに対して順次出力モードの `FileOpen` 操作が実行されました</span><span class="sxs-lookup"><span data-stu-id="76bd1-106">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="76bd1-107">ステートメントが開いているファイルを参照しています。</span><span class="sxs-lookup"><span data-stu-id="76bd1-107">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="76bd1-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="76bd1-108">To correct this error</span></span>

- <span data-ttu-id="76bd1-109">ステートメントを実行する前に、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="76bd1-109">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="76bd1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="76bd1-110">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
