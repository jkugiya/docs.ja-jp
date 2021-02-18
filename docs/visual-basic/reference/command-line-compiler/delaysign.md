---
description: '詳細情報: -delaysign'
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: fc3e52f63431da870355e369e6ffeb8b7b14c5ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461503"
---
# <a name="-delaysign"></a><span data-ttu-id="94962-103">-delaysign</span><span class="sxs-lookup"><span data-stu-id="94962-103">-delaysign</span></span>

<span data-ttu-id="94962-104">アセンブリに完全に署名するか、部分的に署名するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="94962-104">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="94962-105">構文</span><span class="sxs-lookup"><span data-stu-id="94962-105">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="94962-106">引数</span><span class="sxs-lookup"><span data-stu-id="94962-106">Arguments</span></span>

<span data-ttu-id="94962-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="94962-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="94962-108">任意。</span><span class="sxs-lookup"><span data-stu-id="94962-108">Optional.</span></span> <span data-ttu-id="94962-109">完全署名されたアセンブリを作成する場合は、`-delaysign-` を使用します。</span><span class="sxs-lookup"><span data-stu-id="94962-109">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="94962-110">公開キーをアセンブリに配置し、署名済みハッシュ用に領域を予約する場合は、`-delaysign+` を使用します。</span><span class="sxs-lookup"><span data-stu-id="94962-110">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="94962-111">既定値は、`-delaysign-` です。</span><span class="sxs-lookup"><span data-stu-id="94962-111">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="94962-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="94962-112">Remarks</span></span>

<span data-ttu-id="94962-113">`-delaysign` オプションは、[-keyfile](keyfile.md) または [-keycontainer](keycontainer.md) と共に使用しない場合、無効になります。</span><span class="sxs-lookup"><span data-stu-id="94962-113">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="94962-114">アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。</span><span class="sxs-lookup"><span data-stu-id="94962-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="94962-115">結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="94962-115">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="94962-116">アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="94962-116">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="94962-117">たとえば、`-delaysign+` を使用すると、組織の開発者は、テスト担当者がグローバル アセンブリ キャッシュに登録して使用できるアセンブリの署名なしのテスト バージョンを配布できます。</span><span class="sxs-lookup"><span data-stu-id="94962-117">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="94962-118">アセンブリの作業が完了すると、組織の秘密キーの担当者がアセンブリに完全に署名できるようになります。</span><span class="sxs-lookup"><span data-stu-id="94962-118">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="94962-119">このコンパートメント化により、すべての開発者がアセンブリを操作できるようになると同時に、組織の秘密キーを漏えいから保護します。</span><span class="sxs-lookup"><span data-stu-id="94962-119">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="94962-120">アセンブリへの署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94962-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="94962-121">Visual Studio 統合開発環境で -delaysign を設定するには</span><span class="sxs-lookup"><span data-stu-id="94962-121">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="94962-122">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="94962-122">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="94962-123">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94962-123">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="94962-124">**[署名]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="94962-124">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="94962-125">**[遅延署名のみ]** ボックスに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="94962-125">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="94962-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="94962-126">See also</span></span>

- [<span data-ttu-id="94962-127">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="94962-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="94962-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="94962-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="94962-129">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="94962-129">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="94962-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="94962-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
