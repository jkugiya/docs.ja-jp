---
description: "詳細情報: BC40056:インポート '<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。"
title: インポート '<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: e98ba70660823196e763300cd33ec1ba9a9db3b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795704"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="4e649-103">BC40056:インポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4e649-103">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="4e649-104">インポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4e649-104">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="4e649-105">名前空間または型が定義されており、少なくとも 1 つのパブリック メンバーが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4e649-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="4e649-106">別名の名前に他の別名が含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4e649-106">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="4e649-107">`Imports` ステートメントは、見つからないか、`Public` メンバーを定義しないコンテナー要素を指定しています。</span><span class="sxs-lookup"><span data-stu-id="4e649-107">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="4e649-108">*コンテナー要素* は、名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4e649-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="4e649-109">コンテナー要素には、変数、プロシージャ、その他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e649-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="4e649-110">インポートの目的は、コードによって名前空間または型のメンバーに、それらを修飾しなくてもアクセスできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="4e649-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="4e649-111">また、プロジェクトで名前空間や型への参照を追加する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4e649-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="4e649-112">詳細については、「[宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の "コンテナー要素のインポート" に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e649-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="4e649-113">コンパイラは、指定したコンテナー要素が見つからない場合、それを使用する参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="4e649-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="4e649-114">要素が見つかったが、要素が `Public` のメンバーを公開していない場合、参照を正常に実行できません。</span><span class="sxs-lookup"><span data-stu-id="4e649-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="4e649-115">どちらの場合も、要素をインポートしても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="4e649-115">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="4e649-116">コンテナー要素をインポートし、それにインポートの別名を割り当てた場合は、その別名を使用して別の要素をインポートできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4e649-116">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="4e649-117">次のコードはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="4e649-117">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="4e649-118">**エラー ID:** BC40056</span><span class="sxs-lookup"><span data-stu-id="4e649-118">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4e649-119">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4e649-119">To correct this error</span></span>

1. <span data-ttu-id="4e649-120">コンテナー要素がプロジェクトからアクセス可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e649-120">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="4e649-121">コンテナー要素の指定に、別のインポートの別名が含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e649-121">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="4e649-122">コンテナー要素が少なくとも 1 つの `Public` メンバーを公開していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e649-122">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e649-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e649-123">See also</span></span>

- [<span data-ttu-id="4e649-124">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="4e649-124">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="4e649-125">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="4e649-125">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="4e649-126">Public</span><span class="sxs-lookup"><span data-stu-id="4e649-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="4e649-127">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="4e649-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="4e649-128">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="4e649-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
