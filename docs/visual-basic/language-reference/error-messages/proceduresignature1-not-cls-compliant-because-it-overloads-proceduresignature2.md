---
description: '詳細情報: BC40035: <proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる <proceduresignature2> をオーバーロードするため、CLS に準拠していません。'
title: <proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる <proceduresignature2> をオーバーロードするため、CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 056683033a4eacdc6ad783f5056b639e849e3507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795392"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="d6cdb-103">BC40035: \<proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる \<proceduresignature2> をオーバーロードするため、CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-103">BC40035: \<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="d6cdb-104">プロシージャまたはプロパティが別のプロシージャまたはプロパティをオーバーライドする場合、そのプロシージャまたはプロパティは `<CLSCompliant(True)>` としてマークされます。それらのパラメーター リスト間の唯一の違いは、ジャグ配列または配列のランクの入れ子レベルです。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-104">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>

 <span data-ttu-id="d6cdb-105">次の宣言では、2 番目と 3 番目の宣言によってこのエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-105">In the following declarations, the second and third declarations generate this error:</span></span>

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 <span data-ttu-id="d6cdb-106">2 番目の宣言では、元の 1 次元パラメーター `arrayParam` を配列の配列に変更します。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-106">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="d6cdb-107">3 番目の宣言は、`arrayParam` を 2 次元配列 (ランク 2) に変更します。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-107">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="d6cdb-108">Visual Basic では、これらの変更のいずれかによってのみオーバーロードが異なることが許可されますが、そのようなオーバーロードは、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-108">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>

 <span data-ttu-id="d6cdb-109">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-109">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d6cdb-110">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-110">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="d6cdb-111">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-111">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="d6cdb-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-112">By default, this message is a warning.</span></span> <span data-ttu-id="d6cdb-113">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-113">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="d6cdb-114">**エラー ID:** BC40035</span><span class="sxs-lookup"><span data-stu-id="d6cdb-114">**Error ID:** BC40035</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d6cdb-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d6cdb-115">To correct this error</span></span>

- <span data-ttu-id="d6cdb-116">CLS 準拠が必要な場合は、このヘルプ ページで言及されている変更だけよりも多くの点で、相互に異なるようにオーバーロードを定義します。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-116">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="d6cdb-117">このヘルプ ページで言及されている変更によってのみオーバーロードが異なるようにする必要がある場合は、それらの定義から <xref:System.CLSCompliantAttribute> を削除するか、それらを `<CLSCompliant(False)>` とマークします。</span><span class="sxs-lookup"><span data-stu-id="d6cdb-117">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6cdb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6cdb-118">See also</span></span>

- [<span data-ttu-id="d6cdb-119">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="d6cdb-119">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d6cdb-120">Overloads</span><span class="sxs-lookup"><span data-stu-id="d6cdb-120">Overloads</span></span>](../modifiers/overloads.md)
