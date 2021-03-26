---
description: '詳細情報: BC30145:アセンブリを作成できません : <error message>'
title: 'アセンブリを作成できません : <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 2ba476b39b6aa441d8778ee0618dcc3dcf3f7ac8
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653283"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="6737a-103">BC30145:アセンブリを作成できません : \<error message></span><span class="sxs-lookup"><span data-stu-id="6737a-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="6737a-104">Visual Basic コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (*Al.exe*、Alink とも呼ばれます) を呼び出し、アセンブリを作成する出力段階でリンカーからエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="6737a-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="6737a-105">**エラー ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="6737a-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6737a-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6737a-106">To correct this error</span></span>

1. <span data-ttu-id="6737a-107">引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)」でより詳細な説明とアドバイスを参照します。</span><span class="sxs-lookup"><span data-stu-id="6737a-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="6737a-108">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) または [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、手動でアセンブリに署名してみてください。</span><span class="sxs-lookup"><span data-stu-id="6737a-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="6737a-109">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="6737a-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="6737a-110">アセンブリを手動で署名するには</span><span class="sxs-lookup"><span data-stu-id="6737a-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="6737a-111">[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、公開キーと秘密キーのペア ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6737a-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="6737a-112">このファイルは *.snk* の拡張子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="6737a-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="6737a-113">エラーが発生している COM 参照をプロジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="6737a-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="6737a-114">[Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を開きます。</span><span class="sxs-lookup"><span data-stu-id="6737a-114">Open [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

4. <span data-ttu-id="6737a-115">アセンブリ ラッパーを格納するディレクトリに、ディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="6737a-115">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="6737a-116">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="6737a-116">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="6737a-117">入力できる実際のコマンドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6737a-117">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="6737a-118">パスやファイルに空白が含まれている場合には、二重引用符を使用します。</span><span class="sxs-lookup"><span data-stu-id="6737a-118">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="6737a-119">Visual Studio で、作成したファイルに .NET アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="6737a-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="6737a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6737a-120">See also</span></span>

- [<span data-ttu-id="6737a-121">Al.exe</span><span class="sxs-lookup"><span data-stu-id="6737a-121">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="6737a-122">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="6737a-122">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="6737a-123">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="6737a-123">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="6737a-124">Visual Studio フィードバック オプション</span><span class="sxs-lookup"><span data-stu-id="6737a-124">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
