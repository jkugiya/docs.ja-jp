---
description: "詳細情報: BC40057:プロジェクト レベルのインポート '<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。"
title: プロジェクト レベルのインポート '<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 66ae40ca6a2feff78f80bdbc8886387e801f7db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795691"
---
# <a name="bc40057-namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="785a0-103">BC40057:プロジェクト レベルのインポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="785a0-103">BC40057: Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="785a0-104">プロジェクト レベルのインポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="785a0-104">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="785a0-105">名前空間または型が定義されており、少なくとも 1 つのパブリック メンバーが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="785a0-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="785a0-106">別名の名前に他の別名が含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="785a0-106">Make sure the alias name doesn't contain other aliases.</span></span>

 <span data-ttu-id="785a0-107">プロジェクトの import プロパティが、見つからないか、`Public` メンバーを定義しないコンテナー要素を指定しています。</span><span class="sxs-lookup"><span data-stu-id="785a0-107">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

 <span data-ttu-id="785a0-108">*コンテナー要素* は、名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="785a0-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="785a0-109">コンテナー要素には、変数、プロシージャ、その他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="785a0-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

 <span data-ttu-id="785a0-110">インポートの目的は、コードによって名前空間または型のメンバーに、それらを修飾しなくてもアクセスできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="785a0-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="785a0-111">また、プロジェクトで名前空間や型への参照を追加する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="785a0-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="785a0-112">詳細については、「[宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の "コンテナー要素のインポート" に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="785a0-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

 <span data-ttu-id="785a0-113">コンパイラは、指定したコンテナー要素が見つからない場合、それを使用する参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="785a0-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="785a0-114">要素が見つかったが、要素が `Public` のメンバーを公開していない場合、参照を正常に実行できません。</span><span class="sxs-lookup"><span data-stu-id="785a0-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="785a0-115">どちらの場合も、要素をインポートしても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="785a0-115">In either case it is meaningless to import the element.</span></span>

 <span data-ttu-id="785a0-116">インポートする要素を指定するには、**プロジェクト デザイナー** を使用します。</span><span class="sxs-lookup"><span data-stu-id="785a0-116">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="785a0-117">**[参照]** ページの **[インポートされた名前空間]** セクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="785a0-117">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="785a0-118">**プロジェクト デザイナー** には、**ソリューション エクスプローラー** の **[マイ プロジェクト]** アイコンをダブルクリックするとアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="785a0-118">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>

 <span data-ttu-id="785a0-119">**エラー ID:** BC40057</span><span class="sxs-lookup"><span data-stu-id="785a0-119">**Error ID:** BC40057</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="785a0-120">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="785a0-120">To correct this error</span></span>

1. <span data-ttu-id="785a0-121">**プロジェクト デザイナー** を開き、 **[参照]** ページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="785a0-121">Open the **Project Designer** and switch to the **Reference** page.</span></span>

2. <span data-ttu-id="785a0-122">**[インポートされた名前空間]** セクションで、コンテナー要素がプロジェクトからアクセス可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="785a0-122">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>

3. <span data-ttu-id="785a0-123">コンテナー要素が少なくとも 1 つの `Public` メンバーを公開していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="785a0-123">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="785a0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="785a0-124">See also</span></span>

- <span data-ttu-id="785a0-125">[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="785a0-125">[References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
- [<span data-ttu-id="785a0-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="785a0-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="785a0-127">Public</span><span class="sxs-lookup"><span data-stu-id="785a0-127">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="785a0-128">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="785a0-128">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="785a0-129">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="785a0-129">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
