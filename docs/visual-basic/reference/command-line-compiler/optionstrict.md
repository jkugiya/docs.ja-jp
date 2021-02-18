---
description: '詳細情報: -optionstrict'
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: ad58c7775eaa77c1bf693629cf12cc70e4222920
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475904"
---
# <a name="-optionstrict"></a><span data-ttu-id="22b0b-103">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="22b0b-103">-optionstrict</span></span>

<span data-ttu-id="22b0b-104">厳密な型のセマンティクスが強制され、暗黙的な型変換が制限されます。</span><span class="sxs-lookup"><span data-stu-id="22b0b-104">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="22b0b-105">構文</span><span class="sxs-lookup"><span data-stu-id="22b0b-105">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="22b0b-106">引数</span><span class="sxs-lookup"><span data-stu-id="22b0b-106">Arguments</span></span>

<span data-ttu-id="22b0b-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="22b0b-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="22b0b-108">任意。</span><span class="sxs-lookup"><span data-stu-id="22b0b-108">Optional.</span></span> <span data-ttu-id="22b0b-109">`-optionstrict+` オプションは、暗黙的な型変換を制限します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-109">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="22b0b-110">このオプションの既定値は `-optionstrict-` です。</span><span class="sxs-lookup"><span data-stu-id="22b0b-110">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="22b0b-111">`-optionstrict+` オプションは `-optionstrict` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22b0b-111">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="22b0b-112">どちらも制限が少ない型のセマンティクスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="22b0b-112">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="22b0b-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="22b0b-113">Required.</span></span> <span data-ttu-id="22b0b-114">厳密な言語セマンティクスが守られていないときに警告します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-114">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="22b0b-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="22b0b-115">Remarks</span></span>

<span data-ttu-id="22b0b-116">`-optionstrict+` が有効な場合は、拡大型の変換のみを暗黙的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="22b0b-116">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="22b0b-117">整数型のオブジェクトへの `Decimal` 型オブジェクトの割り当てなど、暗黙的な縮小の型変換は、エラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="22b0b-117">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="22b0b-118">暗黙的な縮小の型変換に関する警告を生成するには、`-optionstrict:custom` を使用します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-118">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="22b0b-119">特定の警告を無視するには `-nowarn:numberlist` を使用し、特定の警告をエラーとして扱うには `-warnaserror:numberlist` を使用します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-119">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="22b0b-120">Visual Studio IDE で -optionstrict を設定するには</span><span class="sxs-lookup"><span data-stu-id="22b0b-120">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="22b0b-121">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="22b0b-122">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22b0b-122">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="22b0b-123">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="22b0b-123">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="22b0b-124">**[Option Strict]** ボックスで値を変更します。</span><span class="sxs-lookup"><span data-stu-id="22b0b-124">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="22b0b-125">-optionstrict をプログラムで設定するには</span><span class="sxs-lookup"><span data-stu-id="22b0b-125">To set -optionstrict programmatically</span></span>

<span data-ttu-id="22b0b-126">「[Option Strict ステートメント](../../language-reference/statements/option-strict-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22b0b-126">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="22b0b-127">例</span><span class="sxs-lookup"><span data-stu-id="22b0b-127">Example</span></span>

<span data-ttu-id="22b0b-128">次のコードでは、厳密な型のセマンティクスを使用して `Test.vb` がコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="22b0b-128">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="22b0b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="22b0b-129">See also</span></span>

- [<span data-ttu-id="22b0b-130">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="22b0b-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="22b0b-131">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="22b0b-131">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="22b0b-132">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="22b0b-132">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="22b0b-133">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="22b0b-133">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="22b0b-134">-nowarn</span><span class="sxs-lookup"><span data-stu-id="22b0b-134">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="22b0b-135">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22b0b-135">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="22b0b-136">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="22b0b-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="22b0b-137">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="22b0b-137">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- <span data-ttu-id="22b0b-138">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="22b0b-138">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
