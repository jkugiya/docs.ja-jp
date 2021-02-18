---
description: '詳細情報: -refout (Visual Basic)'
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 2760f7e60d950aaff90becad843824a2e2b4379f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474123"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="31a8c-103">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31a8c-103">-refout (Visual Basic)</span></span>

<span data-ttu-id="31a8c-104">**-refout** オプションは、参照アセンブリを出力するファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="31a8c-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="31a8c-105">構文</span><span class="sxs-lookup"><span data-stu-id="31a8c-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="31a8c-106">引数</span><span class="sxs-lookup"><span data-stu-id="31a8c-106">Arguments</span></span>

`filepath`  
<span data-ttu-id="31a8c-107">参照アセンブリのパスとファイル名。</span><span class="sxs-lookup"><span data-stu-id="31a8c-107">The path and filename of the reference assembly.</span></span> <span data-ttu-id="31a8c-108">通常はプライマリ アセンブリのサブフォルダーにあるはずです。</span><span class="sxs-lookup"><span data-stu-id="31a8c-108">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="31a8c-109">(MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。</span><span class="sxs-lookup"><span data-stu-id="31a8c-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="31a8c-110">`filepath` 内のすべてのフォルダーが存在している必要があります。コンパイラではこれらは作成されません。</span><span class="sxs-lookup"><span data-stu-id="31a8c-110">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="31a8c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="31a8c-111">Remarks</span></span>

<span data-ttu-id="31a8c-112">Visual Basic では、バージョン 15.3 以降の `-refout` スイッチがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="31a8c-112">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="31a8c-113">参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要最小限のメタデータのみを含む特殊なアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="31a8c-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="31a8c-114">これには、ビルド ツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれます。ただし、すべてのメンバーの実装と、その API コントラクトに影響を与えないプライベート メンバーの宣言は除外されます。</span><span class="sxs-lookup"><span data-stu-id="31a8c-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="31a8c-115">詳細については、.NET のガイドの「[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31a8c-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="31a8c-116">`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="31a8c-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="31a8c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="31a8c-117">See also</span></span>

- [<span data-ttu-id="31a8c-118">/refonly</span><span class="sxs-lookup"><span data-stu-id="31a8c-118">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="31a8c-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="31a8c-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="31a8c-120">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="31a8c-120">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
