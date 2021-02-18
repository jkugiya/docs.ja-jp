---
description: '詳細情報: -refonly (Visual Basic)'
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 283aa75fceead38c62c4cf10c1ffe08151aeac9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474136"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="a2b6d-103">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b6d-103">-refonly (Visual Basic)</span></span>

<span data-ttu-id="a2b6d-104">**-refonly** オプションは、コンパイルのプライマリ出力を、実装アセンブリではなく参照アセンブリとする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-104">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="a2b6d-105">`-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="a2b6d-106">構文</span><span class="sxs-lookup"><span data-stu-id="a2b6d-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="a2b6d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="a2b6d-107">Remarks</span></span>

<span data-ttu-id="a2b6d-108">Visual Basic では、バージョン 15.3 以降の `-refonly` スイッチがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-108">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="a2b6d-109">参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要最小限のメタデータのみを含む特殊なアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="a2b6d-110">これには、ビルド ツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれます。ただし、すべてのメンバーの実装と、その API コントラクトに影響を与えないプライベート メンバーの宣言は除外されます。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="a2b6d-111">詳細については、.NET のガイドの「[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="a2b6d-112">`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="a2b6d-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2b6d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2b6d-113">See also</span></span>

- [<span data-ttu-id="a2b6d-114">/refout</span><span class="sxs-lookup"><span data-stu-id="a2b6d-114">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="a2b6d-115">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a2b6d-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a2b6d-116">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="a2b6d-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
