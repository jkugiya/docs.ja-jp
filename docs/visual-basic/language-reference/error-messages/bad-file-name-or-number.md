---
description: '詳細情報: ファイル名または番号が正しくありません。'
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 6e568a721fb3606c5b4bc046041c9d6f24b6d126
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797069"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="6f9a4-103">ファイル名または番号が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-103">Bad file name or number</span></span>

<span data-ttu-id="6f9a4-104">指定したファイルにアクセスしようとして、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-104">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="6f9a4-105">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-105">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="6f9a4-106">ステートメントで、`FileOpen` ステートメントに指定されていないファイル名または番号を使用してファイルを参照しているか、または `FileOpen` ステートメントにそれが指定されていても、その後閉じられました。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-106">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="6f9a4-107">ステートメントで、ファイル番号の範囲外の番号を使用してファイルを参照しています。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-107">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="6f9a4-108">ステートメントで、無効なファイル名または番号を参照しています。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-108">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f9a4-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6f9a4-109">To correct this error</span></span>  
  
1. <span data-ttu-id="6f9a4-110">`FileOpen` ステートメントでファイル名が指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-110">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="6f9a4-111">引数を指定せずに `FileClose` ステートメントを呼び出した場合、開いているすべてのファイルが誤って閉じられた可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-111">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="6f9a4-112">コードでアルゴリズムによってファイル番号を生成している場合、番号が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-112">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="6f9a4-113">ファイル名をチェックして、それらがオペレーティング システムの規則に従っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6f9a4-113">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9a4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f9a4-114">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="6f9a4-115">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="6f9a4-115">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
