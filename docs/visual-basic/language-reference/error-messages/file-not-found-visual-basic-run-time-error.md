---
description: '詳細情報: ファイルが見つかりません。(Visual Basic ランタイム エラー)'
title: ファイルが見つかりません。(Visual Basic ランタイム エラー)
ms.date: 07/20/2015
f1_keywords:
- vbrID53
ms.assetid: 57addb16-6f9a-444d-8af8-dda52431daca
ms.openlocfilehash: da249093a18936a94099b3d5b727e666597f5b6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796263"
---
# <a name="file-not-found-visual-basic-run-time-error"></a><span data-ttu-id="038ef-103">ファイルが見つかりません。(Visual Basic ランタイム エラー)</span><span class="sxs-lookup"><span data-stu-id="038ef-103">File not found (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="038ef-104">指定された場所でファイルが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="038ef-104">The file was not found where specified.</span></span> <span data-ttu-id="038ef-105">このエラーには、次のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="038ef-105">The error has the following possible causes:</span></span>

- <span data-ttu-id="038ef-106">ステートメントが、存在しないファイルを参照しています。</span><span class="sxs-lookup"><span data-stu-id="038ef-106">A statement refers to a file that does not exist.</span></span>

- <span data-ttu-id="038ef-107">ダイナミック リンク ライブラリ (DLL) でプロシージャを呼び出そうとしましたが、`Declare` ステートメントの `Lib` 句で指定されたライブラリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="038ef-107">An attempt was made to call a procedure in a dynamic-link library (DLL), but the library specified in the `Lib` clause of the `Declare` statement cannot be found.</span></span>

- <span data-ttu-id="038ef-108">プロジェクトを開こうとしたか、存在しないテキスト ファイルを読み込もうとしました。</span><span class="sxs-lookup"><span data-stu-id="038ef-108">You attempted to open a project or load a text file that does not exist.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="038ef-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="038ef-109">To correct this error</span></span>

- <span data-ttu-id="038ef-110">ファイル名とパスの指定のスペルを確認してください。</span><span class="sxs-lookup"><span data-stu-id="038ef-110">Check the spelling of the file name and the path specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="038ef-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="038ef-111">See also</span></span>

- [<span data-ttu-id="038ef-112">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="038ef-112">Declare Statement</span></span>](../statements/declare-statement.md)
