---
description: "詳細情報: BC30251:型 '<typename>' にはコンストラクターがありません。"
title: 型 '<typename>' にはコンストラクターがありません。
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 3961ba557ad2afd9c94f071b6615573419d7325b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106580"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="5df01-103">BC30251:型 '\<typename>' にはコンストラクターがありません。</span><span class="sxs-lookup"><span data-stu-id="5df01-103">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="5df01-104">型が `Sub New()` の呼び出しをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5df01-104">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="5df01-105">コンパイラまたはバイナリ ファイルが破損していることが原因の 1 つとして考えられます。</span><span class="sxs-lookup"><span data-stu-id="5df01-105">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="5df01-106">**エラー ID:** BC30251</span><span class="sxs-lookup"><span data-stu-id="5df01-106">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5df01-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5df01-107">To correct this error</span></span>

1. <span data-ttu-id="5df01-108">型が別のプロジェクトまたは参照ファイル内にある場合は、プロジェクトまたはファイルを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="5df01-108">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="5df01-109">型が同じプロジェクト内にある場合は、型を含むアセンブリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="5df01-109">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="5df01-110">エラーがまだ発生する場合は、Visual Basic コンパイラを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="5df01-110">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="5df01-111">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="5df01-111">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="5df01-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5df01-112">See also</span></span>

- [<span data-ttu-id="5df01-113">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="5df01-113">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="5df01-114">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="5df01-114">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
