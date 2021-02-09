---
description: '詳細情報: クリップボードの形式が有効ではありません。'
title: クリップボードの形式が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 58ba6197a14b005cf61d0783e19cb3f957dd2fca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796757"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="a60b2-103">クリップボードの形式が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="a60b2-103">Clipboard format is not valid</span></span>

<span data-ttu-id="a60b2-104">指定されたクリップボードの形式が、実行されるメソッドと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="a60b2-104">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="a60b2-105">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="a60b2-105">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="a60b2-106">クリップボードの `GetText` または `SetText` メソッドに `vbCFText` または `vbCFLink` 以外のクリップボードの形式を使用している。</span><span class="sxs-lookup"><span data-stu-id="a60b2-106">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="a60b2-107">クリップボードの `GetData` または `SetData` メソッドに `vbCFBitmap`、`vbCFDIB`、または `vbCFMetafile` 以外のクリップボードの形式を使用している。</span><span class="sxs-lookup"><span data-stu-id="a60b2-107">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="a60b2-108">クリップボードの形式が Microsoft Windows に登録されていないときに、登録されている形式 (&HC000-& HFFFF) に対して Microsoft Windows によって予約されている範囲内のクリップボードの形式を使用して、`DataObject` の `GetData` または `SetData` メソッドを使用している。</span><span class="sxs-lookup"><span data-stu-id="a60b2-108">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a60b2-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a60b2-109">To correct this error</span></span>  
  
- <span data-ttu-id="a60b2-110">無効な形式を削除して、有効な形式を指定してください。</span><span class="sxs-lookup"><span data-stu-id="a60b2-110">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60b2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a60b2-111">See also</span></span>

- [<span data-ttu-id="a60b2-112">クリップボード: その他の形式の追加</span><span class="sxs-lookup"><span data-stu-id="a60b2-112">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
