---
description: '詳細情報: -optioncompare'
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 9be4867c75cc16a8f699cf492dc41e9d08b96495
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475930"
---
# <a name="-optioncompare"></a><span data-ttu-id="5f7e0-103">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="5f7e0-103">-optioncompare</span></span>

<span data-ttu-id="5f7e0-104">文字列比較の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-104">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f7e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f7e0-105">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="5f7e0-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="5f7e0-106">Remarks</span></span>

<span data-ttu-id="5f7e0-107">次の 2 つの形式のいずれかで `-optioncompare` を指定できます。バイナリ文字列比較を使用する `-optioncompare:binary` と、テキスト文字列比較を使用する `-optioncompare:text` です。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-107">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="5f7e0-108">コンパイラでは既定で `-optioncompare:binary` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-108">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="5f7e0-109">Microsoft Windows では、現在のコード ページによってバイナリ並べ替え順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-109">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="5f7e0-110">一般的なバイナリ並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-110">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="5f7e0-111">テキストベースの文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-111">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="5f7e0-112">一般的なテキストの並べ替え順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-112">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="5f7e0-113">Visual Studio IDE で -optioncompare を設定するには</span><span class="sxs-lookup"><span data-stu-id="5f7e0-113">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="5f7e0-114">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5f7e0-115">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-115">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="5f7e0-116">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-116">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="5f7e0-117">**[Option Compare]** ボックスで値を変更します。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-117">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="5f7e0-118">-optioncompare をプログラムで設定するには</span><span class="sxs-lookup"><span data-stu-id="5f7e0-118">To set -optioncompare programmatically</span></span>

<span data-ttu-id="5f7e0-119">「[Option Compare ステートメント](../../language-reference/statements/option-compare-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-119">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="5f7e0-120">例</span><span class="sxs-lookup"><span data-stu-id="5f7e0-120">Example</span></span>

<span data-ttu-id="5f7e0-121">次のコードでは `ProjFile.vb` がコンパイルされ、バイナリ文字列比較が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f7e0-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="5f7e0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f7e0-122">See also</span></span>

- [<span data-ttu-id="5f7e0-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="5f7e0-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5f7e0-124">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5f7e0-124">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="5f7e0-125">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="5f7e0-125">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="5f7e0-126">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5f7e0-126">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="5f7e0-127">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="5f7e0-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="5f7e0-128">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="5f7e0-128">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- <span data-ttu-id="5f7e0-129">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="5f7e0-129">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
