---
title: 型略称
description: コードを読みやすくするために、よりわかりやすい名前を型に付けるための F# 型略称について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630217"
---
# <a name="type-abbreviations"></a><span data-ttu-id="9fe20-103">型略称</span><span class="sxs-lookup"><span data-stu-id="9fe20-103">Type Abbreviations</span></span>

<span data-ttu-id="9fe20-104">*型略称* は、型の別名または代替名です。</span><span class="sxs-lookup"><span data-stu-id="9fe20-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fe20-105">構文</span><span class="sxs-lookup"><span data-stu-id="9fe20-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="9fe20-106">解説</span><span class="sxs-lookup"><span data-stu-id="9fe20-106">Remarks</span></span>

<span data-ttu-id="9fe20-107">コードを読みやすくするために、型略称を使用して、よりわかりやすい名前を型に付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9fe20-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="9fe20-108">また、それらを使用して、本来記述するのが煩わい型に対して使いやすい名前を作成することもできます。さらに、型略称を使用して、基になる型を使用するすべてのコードを変更することなく、その型を変更しやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9fe20-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="9fe20-109">次に示すのは、簡易的な型略称です。</span><span class="sxs-lookup"><span data-stu-id="9fe20-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="9fe20-110">型略称のアクセシビリティは、既定で `public` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9fe20-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="9fe20-111">次のコードのように、型略称にジェネリック パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9fe20-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="9fe20-112">前のコードで `Transform` は、任意の型の単一の引数を受け取り、同じ型の単一の値を返す関数を表す型略称です。</span><span class="sxs-lookup"><span data-stu-id="9fe20-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="9fe20-113">型略称は .NET Framework MSIL コードに保持されません。</span><span class="sxs-lookup"><span data-stu-id="9fe20-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="9fe20-114">そのため、別の .NET Framework 言語の F# アセンブリを使用する場合は、型略称に基になる型名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fe20-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="9fe20-115">型略称は、測定単位にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="9fe20-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="9fe20-116">詳細については、「[測定単位](units-of-measure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fe20-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe20-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fe20-117">See also</span></span>

- [<span data-ttu-id="9fe20-118">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="9fe20-118">F# Language Reference</span></span>](index.md)
