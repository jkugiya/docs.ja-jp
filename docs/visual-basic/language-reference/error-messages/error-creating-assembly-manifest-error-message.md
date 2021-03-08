---
description: '詳細情報: BC30140:アセンブリ マニフェストを作成中にエラーが発生しました : <error message>'
title: 'アセンブリ マニフェストを作成中にエラーが発生しました : <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e2c690ab198e11a70a2fc3bba925ccc4ccb31c79
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103414"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a><span data-ttu-id="d4462-103">BC30140:アセンブリ マニフェストを作成中にエラーが発生しました : \<error message></span><span class="sxs-lookup"><span data-stu-id="d4462-103">BC30140: Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="d4462-104">Visual Basic コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="d4462-104">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="d4462-105">リンカーが、アセンブリの生成前の段階でのエラーを報告しています。</span><span class="sxs-lookup"><span data-stu-id="d4462-105">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>

 <span data-ttu-id="d4462-106">指定したキー ファイルまたはキー コンテナーに原因がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4462-106">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="d4462-107">アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4462-107">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="d4462-108">アセンブリに遅延署名するには、 **[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4462-108">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="d4462-109">アセンブリに遅延署名する場合、秘密キーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d4462-109">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="d4462-110">詳細については、[厳密な名前でアセンブリに署名する](../../../standard/assembly/sign-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4462-110">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

 <span data-ttu-id="d4462-111">**エラー ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="d4462-111">**Error ID:** BC30140</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d4462-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d4462-112">To correct this error</span></span>

1. <span data-ttu-id="d4462-113">引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)」で</span><span class="sxs-lookup"><span data-stu-id="d4462-113">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="d4462-114">エラー AL1019 の詳細な説明とアドバイスを参照してください</span><span class="sxs-lookup"><span data-stu-id="d4462-114">for error AL1019 further explanation and advice</span></span>

2. <span data-ttu-id="d4462-115">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="d4462-115">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4462-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4462-116">See also</span></span>

- [<span data-ttu-id="d4462-117">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="d4462-117">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- <span data-ttu-id="d4462-118">[[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)</span><span class="sxs-lookup"><span data-stu-id="d4462-118">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)</span></span>
- [<span data-ttu-id="d4462-119">Al.exe</span><span class="sxs-lookup"><span data-stu-id="d4462-119">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d4462-120">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="d4462-120">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
