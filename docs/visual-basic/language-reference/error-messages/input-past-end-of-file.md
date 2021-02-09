---
description: '詳細情報: ファイルにこれ以上データがありません。'
title: ファイルにこれ以上データがありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: b65a57bdc56367518a93880be28781e56c9b99cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796042"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="883aa-103">ファイルにこれ以上データがありません。</span><span class="sxs-lookup"><span data-stu-id="883aa-103">Input past end of file</span></span>

<span data-ttu-id="883aa-104">`Input` ステートメントが空のファイル、またはすべてのデータが使用されているファイルから読み取っているか、またはバイナリ アクセス用に開かれたファイルで `EOF` 関数を使用しました。</span><span class="sxs-lookup"><span data-stu-id="883aa-104">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="883aa-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="883aa-105">To correct this error</span></span>  
  
1. <span data-ttu-id="883aa-106">`Input` ステートメントの直前で `EOF` 関数を使用して、ファイルの末尾を検出します。</span><span class="sxs-lookup"><span data-stu-id="883aa-106">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="883aa-107">ファイルがバイナリ アクセス用に開かれている場合は、`Seek` と `Loc` を使用します。</span><span class="sxs-lookup"><span data-stu-id="883aa-107">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883aa-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="883aa-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
