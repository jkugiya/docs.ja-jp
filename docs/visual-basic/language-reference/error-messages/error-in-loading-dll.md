---
description: '詳細情報: DLL 読み込み時のエラーです。(Visual Basic)'
title: DLL 読み込み時のエラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 098d05e93d328f3667000bd81290f4b77cf7949e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796510"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="eaab2-103">DLL 読み込み時のエラーです。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaab2-103">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="eaab2-104">ダイナミックリンク ライブラリ (DLL) は、`Declare` ステートメントの `Lib` 句で指定されたライブラリです。</span><span class="sxs-lookup"><span data-stu-id="eaab2-104">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="eaab2-105">このエラーには、次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="eaab2-105">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="eaab2-106">ファイルが DLL 実行可能ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="eaab2-106">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="eaab2-107">ファイルが Microsoft Windows DLL ではありません。</span><span class="sxs-lookup"><span data-stu-id="eaab2-107">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="eaab2-108">DLL が存在しない別の DLL を参照しています。</span><span class="sxs-lookup"><span data-stu-id="eaab2-108">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="eaab2-109">DLL または参照先の DLL が、パスで指定されたディレクトリにありません。</span><span class="sxs-lookup"><span data-stu-id="eaab2-109">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eaab2-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eaab2-110">To correct this error</span></span>  
  
- <span data-ttu-id="eaab2-111">ファイルがソーステキスト ファイルであり、そのため DLL 実行可能ファイルでない場合は、コンパイルして DLL 実行可能形式にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaab2-111">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="eaab2-112">ファイルが Microsoft Windows DLL でない場合は、Microsoft Windows と同等のものを取得します。</span><span class="sxs-lookup"><span data-stu-id="eaab2-112">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="eaab2-113">DLL が存在しない別の DLL を参照している場合は、参照先の DLL を取得して、使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="eaab2-113">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="eaab2-114">DLL または参照先の DLL がパスによって指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="eaab2-114">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaab2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaab2-115">See also</span></span>

- [<span data-ttu-id="eaab2-116">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="eaab2-116">Declare Statement</span></span>](../statements/declare-statement.md)
