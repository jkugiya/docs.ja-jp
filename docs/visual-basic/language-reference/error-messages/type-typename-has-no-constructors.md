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
ms.openlocfilehash: 32ae854e9f1b037a17d9c378ce7ee4a3f9b43ad2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641175"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="bf2ed-103">BC30251:型 '\<typename>' にはコンストラクターがありません。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-103">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="bf2ed-104">型が `Sub New()` の呼び出しをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-104">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="bf2ed-105">コンパイラまたはバイナリ ファイルが破損していることが原因の 1 つとして考えられます。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-105">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="bf2ed-106">**エラー ID:** BC30251</span><span class="sxs-lookup"><span data-stu-id="bf2ed-106">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bf2ed-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bf2ed-107">To correct this error</span></span>

1. <span data-ttu-id="bf2ed-108">型が別のプロジェクトまたは参照ファイル内にある場合は、プロジェクトまたはファイルを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-108">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="bf2ed-109">型が同じプロジェクト内にある場合は、型を含むアセンブリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-109">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="bf2ed-110">エラーがまだ発生する場合は、Visual Basic コンパイラを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-110">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="bf2ed-111">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="bf2ed-111">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf2ed-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf2ed-112">See also</span></span>

- [<span data-ttu-id="bf2ed-113">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="bf2ed-113">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="bf2ed-114">ご意見</span><span class="sxs-lookup"><span data-stu-id="bf2ed-114">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
