---
title: コンパイラのエラーと警告
description: F# コンパイラによって生成されるエラーと警告の説明と解決策
ms.date: 12/21/2019
ms.openlocfilehash: 9769ddee989f0774cfae8842e60dbd3fd2065f9c
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190178"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="a49c7-103">F# コンパイラのメッセージ</span><span class="sxs-lookup"><span data-stu-id="a49c7-103">F# compiler messages</span></span>

<span data-ttu-id="a49c7-104">このセクションでは、F# コンパイラが特定のコンストラクトに対して生成するコンパイラのエラーと警告について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a49c7-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="a49c7-105">既定のエラー セットは、次の方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="a49c7-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="a49c7-106">`-warnaserror+` コンパイラ オプションを使用して、特定の警告をエラーとして扱う。</span><span class="sxs-lookup"><span data-stu-id="a49c7-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="a49c7-107">`-nowarn` コンパイラ オプションを使用して特定の警告を無視する</span><span class="sxs-lookup"><span data-stu-id="a49c7-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="a49c7-108">このセクションに、特定の警告またはエラーがまだ記録されていない場合は、次を行います。</span><span class="sxs-lookup"><span data-stu-id="a49c7-108">If a particular warning or error is not yet recorded in this section:</span></span>

- <span data-ttu-id="a49c7-109">このページの最後に移動し、エラーの番号またはテキストを含めてフィードバックを送信する、または</span><span class="sxs-lookup"><span data-stu-id="a49c7-109">Go to the end of this page and send feedback that includes the number or text of the error, or</span></span>
- <span data-ttu-id="a49c7-110">「[Create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx)」の手順に従って、このリポジトリの pull request を開いて、自分で追加する。</span><span class="sxs-lookup"><span data-stu-id="a49c7-110">Add it yourself by following the instructions in [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) and opening a pull request for this repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="a49c7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a49c7-111">See also</span></span>

- [<span data-ttu-id="a49c7-112">F# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="a49c7-112">F# Compiler Options</span></span>](../compiler-options.md)
