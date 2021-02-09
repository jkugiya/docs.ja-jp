---
description: "詳細情報: BC40027:関数 '<procedurename>' の戻り値の型は CLS に準拠していません。"
title: 関数 '<procedurename>' の戻り値の型は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: df0cdb10ebc62a833cef89d3e82bc1ed756c556e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675118"
---
# <a name="bc40027-return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="ce001-103">BC40027:関数 '\<procedurename>' の戻り値の型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="ce001-103">BC40027: Return type of function '\<procedurename>' is not CLS-compliant</span></span>

<span data-ttu-id="ce001-104">`Function` プロシージャが `<CLSCompliant(True)>` としてマークされていますが、`<CLSCompliant(False)>` としてマークされている型、マークされていない型、または非準拠の型であるために修飾されていない型を返します。</span><span class="sxs-lookup"><span data-stu-id="ce001-104">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>

 <span data-ttu-id="ce001-105">プロシージャを[言語への非依存性および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce001-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="ce001-106">これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ce001-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>

 <span data-ttu-id="ce001-107">次の Visual Basic データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="ce001-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="ce001-108">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="ce001-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="ce001-109">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="ce001-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="ce001-110">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="ce001-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="ce001-111">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="ce001-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="ce001-112">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="ce001-112">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="ce001-113">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce001-113">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="ce001-114">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ce001-114">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="ce001-115">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="ce001-115">By default, this message is a warning.</span></span> <span data-ttu-id="ce001-116">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ce001-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="ce001-117">**エラー ID:** BC40027</span><span class="sxs-lookup"><span data-stu-id="ce001-117">**Error ID:** BC40027</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ce001-118">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ce001-118">To correct this error</span></span>

- <span data-ttu-id="ce001-119">`Function` プロシージャがこの特定の型を返す必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。</span><span class="sxs-lookup"><span data-stu-id="ce001-119">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="ce001-120">プロシージャは CLS 準拠になりません。</span><span class="sxs-lookup"><span data-stu-id="ce001-120">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="ce001-121">`Function` プロシージャを CLS 準拠にする必要がある場合は、戻り値の型を最も近い CLS 準拠型に変更します。</span><span class="sxs-lookup"><span data-stu-id="ce001-121">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="ce001-122">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce001-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="ce001-123">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce001-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="ce001-124">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が .NET Framework とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce001-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="ce001-125">たとえば、他の多くの環境では `int` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="ce001-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="ce001-126">このようなコンポーネントに 16 ビット整数を返す場合、Visual Basic のマネージド コードでは、`Integer` ではなく `Short` を宣言してください。</span><span class="sxs-lookup"><span data-stu-id="ce001-126">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
