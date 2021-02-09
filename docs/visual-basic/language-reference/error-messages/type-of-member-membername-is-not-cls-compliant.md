---
description: "詳細情報: BC40025:メンバー '<membername>' の型は CLS に準拠していません。"
title: メンバー '<membername>' の型は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 4fe83999a0cb2d678ccc0119509a368160dfc3ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774877"
---
# <a name="bc40025-type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="b86a6-103">BC40025:メンバー '\<membername>' の型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-103">BC40025: Type of member '\<membername>' is not CLS-compliant</span></span>

<span data-ttu-id="b86a6-104">このメンバーに指定されたデータ型は、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-104">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="b86a6-105">.NET Framework と Visual Basic では、このデータ型をサポートしているため、コンポーネント内でエラーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-105">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="b86a6-106">ただし、厳密に CLS に準拠しているコードで記述された別のコンポーネントでは、このデータ型をサポートしていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b86a6-106">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="b86a6-107">そのようなコンポーネントでは、使用しているコンポーネントと正常にやり取りできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b86a6-107">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="b86a6-108">次の Visual Basic データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="b86a6-109">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="b86a6-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="b86a6-110">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="b86a6-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="b86a6-111">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="b86a6-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="b86a6-112">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="b86a6-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="b86a6-113">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="b86a6-113">By default, this message is a warning.</span></span> <span data-ttu-id="b86a6-114">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b86a6-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="b86a6-115">**エラー ID:** BC40025</span><span class="sxs-lookup"><span data-stu-id="b86a6-115">**Error ID:** BC40025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b86a6-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b86a6-116">To correct this error</span></span>

- <span data-ttu-id="b86a6-117">コンポーネントが他の .NET Framework コンポーネントとのみやり取りする場合、または他のコンポーネントとやり取りしない場合は、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-117">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="b86a6-118">.NET Framework 用に記述されていないコンポーネントとやり取りする場合は、リフレクションを通じて、またはドキュメントからこのデータ型がサポートされているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="b86a6-118">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="b86a6-119">サポートされている場合は、何も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b86a6-119">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="b86a6-120">このデータ型をサポートしていないコンポーネントとやり取りする場合は、それを最も近い CLS 準拠の型に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b86a6-120">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="b86a6-121">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b86a6-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="b86a6-122">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b86a6-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="b86a6-123">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が .NET Framework とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b86a6-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="b86a6-124">たとえば、他の多くの環境では `uint` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="b86a6-124">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="b86a6-125">そのようなコンポーネントに 16 ビットの引数を渡す場合は、Visual Basic のマネージド コードで、`UInteger` ではなく `UShort` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="b86a6-125">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b86a6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b86a6-126">See also</span></span>

- [<span data-ttu-id="b86a6-127">リフレクション</span><span class="sxs-lookup"><span data-stu-id="b86a6-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
