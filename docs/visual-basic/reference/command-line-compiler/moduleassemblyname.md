---
description: '詳細情報: -moduleassemblyname'
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 1b5daac8fea264e86b7200f3cead4cb657641000
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434317"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="d24d5-103">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="d24d5-103">-moduleassemblyname</span></span>

<span data-ttu-id="d24d5-104">このモジュールが一部となるアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d24d5-104">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d24d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="d24d5-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="d24d5-106">引数</span><span class="sxs-lookup"><span data-stu-id="d24d5-106">Arguments</span></span>  
  
|<span data-ttu-id="d24d5-107">用語</span><span class="sxs-lookup"><span data-stu-id="d24d5-107">Term</span></span>|<span data-ttu-id="d24d5-108">定義</span><span class="sxs-lookup"><span data-stu-id="d24d5-108">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="d24d5-109">このモジュールが一部となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="d24d5-109">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d24d5-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d24d5-110">Remarks</span></span>  

 <span data-ttu-id="d24d5-111">`-target:module` オプションが指定されている場合にのみ、コンパイラで `-moduleassemblyname` オプションが処理されます。</span><span class="sxs-lookup"><span data-stu-id="d24d5-111">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="d24d5-112">これにより、コンパイラでモジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d24d5-112">This causes the compiler to create a module.</span></span> <span data-ttu-id="d24d5-113">コンパイラによって作成されたモジュールは、`-moduleassemblyname` オプションで指定されたアセンブリに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="d24d5-113">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="d24d5-114">モジュールを別のアセンブリに配置すると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d24d5-114">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="d24d5-115">`-moduleassemblyname` オプションは、次の条件に該当する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="d24d5-115">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="d24d5-116">モジュール内のデータ型が、参照アセンブリの `Friend` 型にアクセスする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="d24d5-116">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="d24d5-117">参照アセンブリに、モジュールをビルドするアセンブリへのフレンド アセンブリのアクセス権が付与されている場合。</span><span class="sxs-lookup"><span data-stu-id="d24d5-117">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="d24d5-118">モジュールの作成の詳細については、「[-target (Visual Basic)](target.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d24d5-118">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="d24d5-119">フレンド アセンブリの詳細については、「[フレンド アセンブリ](../../../standard/assembly/friend.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d24d5-119">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d24d5-120">`-moduleassemblyname` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド プロンプトからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d24d5-120">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24d5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d24d5-121">See also</span></span>

- [<span data-ttu-id="d24d5-122">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="d24d5-122">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="d24d5-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d24d5-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d24d5-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d24d5-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="d24d5-125">-main</span><span class="sxs-lookup"><span data-stu-id="d24d5-125">-main</span></span>](main.md)
- [<span data-ttu-id="d24d5-126">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d24d5-126">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="d24d5-127">-addmodule</span><span class="sxs-lookup"><span data-stu-id="d24d5-127">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="d24d5-128">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="d24d5-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="d24d5-129">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="d24d5-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="d24d5-130">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="d24d5-130">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
