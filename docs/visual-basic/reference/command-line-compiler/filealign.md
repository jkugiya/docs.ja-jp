---
description: '詳細情報: -filealign'
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: f32ae370c0ef832b501f085351eadb9b6156c730
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470292"
---
# <a name="-filealign"></a><span data-ttu-id="85fae-103">-filealign</span><span class="sxs-lookup"><span data-stu-id="85fae-103">-filealign</span></span>

<span data-ttu-id="85fae-104">出力ファイルでセクションをアラインするサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="85fae-104">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fae-105">構文</span><span class="sxs-lookup"><span data-stu-id="85fae-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="85fae-106">引数</span><span class="sxs-lookup"><span data-stu-id="85fae-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="85fae-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="85fae-107">Required.</span></span> <span data-ttu-id="85fae-108">出力ファイルにセクションの配置を指定する値です。</span><span class="sxs-lookup"><span data-stu-id="85fae-108">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="85fae-109">有効値は 512、1024、2048、4096、および 8192 です。</span><span class="sxs-lookup"><span data-stu-id="85fae-109">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="85fae-110">これらの値はバイト単位です。</span><span class="sxs-lookup"><span data-stu-id="85fae-110">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85fae-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="85fae-111">Remarks</span></span>  

 <span data-ttu-id="85fae-112">`-filealign` オプションは、ご自分の出力ファイルにセクションの配置を指定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="85fae-112">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="85fae-113">セクションは、コードまたはデータのいずれかを含む、移植可能な実行可能 (PE) ファイルの連続したメモリのブロックです。</span><span class="sxs-lookup"><span data-stu-id="85fae-113">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="85fae-114">`-filealign` オプションを使用すると、非標準の配置でご自分のアプリケーションをコンパイルできます。ほとんどの開発者は、このオプションを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="85fae-114">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="85fae-115">各セクションは、`-filealign` 値の倍数の境界上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="85fae-115">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="85fae-116">固定の既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="85fae-116">There is no fixed default.</span></span> <span data-ttu-id="85fae-117">`-filealign` を指定しない場合、コンパイル時にコンパイラによって既定が選択されます。</span><span class="sxs-lookup"><span data-stu-id="85fae-117">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="85fae-118">セクションのサイズを指定すると、出力ファイルのサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="85fae-118">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="85fae-119">セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。</span><span class="sxs-lookup"><span data-stu-id="85fae-119">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85fae-120">`-filealign` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="85fae-120">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fae-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fae-121">See also</span></span>

- [<span data-ttu-id="85fae-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="85fae-122">Visual Basic Command-Line Compiler</span></span>](index.md)
