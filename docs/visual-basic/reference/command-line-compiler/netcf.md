---
description: '詳細情報: -netcf'
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 053e177d8d7008b10bfa552ee60cbbd2d5dda565
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434915"
---
# <a name="-netcf"></a><span data-ttu-id="99b13-103">-netcf</span><span class="sxs-lookup"><span data-stu-id="99b13-103">-netcf</span></span>

<span data-ttu-id="99b13-104">.NET Compact Framework を対象とするようにコンパイラを設定します。</span><span class="sxs-lookup"><span data-stu-id="99b13-104">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="99b13-105">構文</span><span class="sxs-lookup"><span data-stu-id="99b13-105">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="99b13-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="99b13-106">Remarks</span></span>

<span data-ttu-id="99b13-107">`-netcf` オプションを指定すると、Visual Basic コンパイラの対象は、完全な .NET Framework ではなく .NET Compact Framework となります。</span><span class="sxs-lookup"><span data-stu-id="99b13-107">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="99b13-108">完全な .NET Framework にのみ存在する言語機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="99b13-108">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="99b13-109">`-netcf` オプションは、[-sdkpath](sdkpath.md) と共に使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="99b13-109">The `-netcf` option is designed to be used with [-sdkpath](sdkpath.md).</span></span> <span data-ttu-id="99b13-110">`-netcf` によって無効にされた言語機能は、`-sdkpath` の対象となるファイルには存在しないものと同じ言語機能です。</span><span class="sxs-lookup"><span data-stu-id="99b13-110">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="99b13-111">`-netcf` オプションは、Visual Studio 開発環境内からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="99b13-111">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="99b13-112">`-netcf` オプションは、Visual Basic デバイス プロジェクトが読み込まれるときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="99b13-112">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="99b13-113">`-netcf` オプションでは、次の言語機能を変更します。</span><span class="sxs-lookup"><span data-stu-id="99b13-113">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="99b13-114">プログラムの実行を終了する、[End \<keyword> ステートメント](../../language-reference/statements/end-keyword-statement.md) キーワードは無効になります。</span><span class="sxs-lookup"><span data-stu-id="99b13-114">The [End \<keyword> Statement](../../language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="99b13-115">次のプログラムは `-netcf` なしでコンパイルされ、実行されますが、`-netcf` を指定するとコンパイル時に失敗します。</span><span class="sxs-lookup"><span data-stu-id="99b13-115">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="99b13-116">すべての形式の遅延バインディングが無効になります。</span><span class="sxs-lookup"><span data-stu-id="99b13-116">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="99b13-117">コンパイル時のエラーは、認識された遅延バインディングのシナリオが検出された場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="99b13-117">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="99b13-118">次のプログラムは `-netcf` なしでコンパイルされ、実行されますが、`-netcf` を指定するとコンパイル時に失敗します。</span><span class="sxs-lookup"><span data-stu-id="99b13-118">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="99b13-119">[Auto](../../language-reference/modifiers/auto.md)、[Ansi](../../language-reference/modifiers/ansi.md)、および [Unicode](../../language-reference/modifiers/unicode.md) 修飾子は無効になります。</span><span class="sxs-lookup"><span data-stu-id="99b13-119">The [Auto](../../language-reference/modifiers/auto.md), [Ansi](../../language-reference/modifiers/ansi.md), and [Unicode](../../language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="99b13-120">[Declare ステートメント](../../language-reference/statements/declare-statement.md)の構文も `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="99b13-120">The syntax of the [Declare Statement](../../language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="99b13-121">次のコードは、コンパイル時の `-netcf` の効果を示しています。</span><span class="sxs-lookup"><span data-stu-id="99b13-121">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="99b13-122">Visual Basic から削除された Visual Basic 6.0 キーワードを使用すると、`-netcf` の使用時に別のエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="99b13-122">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="99b13-123">これは、次のキーワードのエラー メッセージに影響します。</span><span class="sxs-lookup"><span data-stu-id="99b13-123">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="99b13-124">例</span><span class="sxs-lookup"><span data-stu-id="99b13-124">Example</span></span>

<span data-ttu-id="99b13-125">次のコードでは、C ドライブ上の .NET Compact Framework の既定のインストール ディレクトリにある mscorlib.dll と Microsoft.VisualBasic.dll のバージョンを使用して、.NET Compact Framework で `Myfile.vb` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="99b13-125">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="99b13-126">通常は、最新バージョンの .NET Compact Framework を使用します。</span><span class="sxs-lookup"><span data-stu-id="99b13-126">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="99b13-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="99b13-127">See also</span></span>

- [<span data-ttu-id="99b13-128">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="99b13-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="99b13-129">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="99b13-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="99b13-130">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="99b13-130">-sdkpath</span></span>](sdkpath.md)
