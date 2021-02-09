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
ms.openlocfilehash: 4116f3293a36f4592712c3e39c988aa730753de4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796536"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a><span data-ttu-id="d9b84-103">BC30140:アセンブリ マニフェストを作成中にエラーが発生しました : \<error message></span><span class="sxs-lookup"><span data-stu-id="d9b84-103">BC30140: Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="d9b84-104">Visual Basic コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="d9b84-104">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="d9b84-105">リンカーが、アセンブリの生成前の段階でのエラーを報告しています。</span><span class="sxs-lookup"><span data-stu-id="d9b84-105">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>

 <span data-ttu-id="d9b84-106">指定したキー ファイルまたはキー コンテナーに原因がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9b84-106">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="d9b84-107">アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9b84-107">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="d9b84-108">アセンブリに遅延署名するには、 **[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9b84-108">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="d9b84-109">アセンブリに遅延署名する場合、秘密キーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d9b84-109">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="d9b84-110">詳細については、[厳密な名前でアセンブリに署名する](../../../standard/assembly/sign-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9b84-110">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

 <span data-ttu-id="d9b84-111">**エラー ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="d9b84-111">**Error ID:** BC30140</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d9b84-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d9b84-112">To correct this error</span></span>

1. <span data-ttu-id="d9b84-113">引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)」で</span><span class="sxs-lookup"><span data-stu-id="d9b84-113">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="d9b84-114">エラー AL1019 の詳細な説明とアドバイスを参照してください</span><span class="sxs-lookup"><span data-stu-id="d9b84-114">for error AL1019 further explanation and advice</span></span>

2. <span data-ttu-id="d9b84-115">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="d9b84-115">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9b84-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9b84-116">See also</span></span>

- [<span data-ttu-id="d9b84-117">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="d9b84-117">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- <span data-ttu-id="d9b84-118">[[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)</span><span class="sxs-lookup"><span data-stu-id="d9b84-118">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)</span></span>
- [<span data-ttu-id="d9b84-119">Al.exe</span><span class="sxs-lookup"><span data-stu-id="d9b84-119">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d9b84-120">ご意見</span><span class="sxs-lookup"><span data-stu-id="d9b84-120">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
