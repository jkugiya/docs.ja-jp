---
title: エントリ ポイント
description: 実行可能ファイルとしてコンパイルされる F# プログラムにエントリ ポイント (実行が正式に開始される位置) を設定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630523"
---
# <a name="entry-point"></a><span data-ttu-id="ea684-103">エントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="ea684-103">Entry Point</span></span>

<span data-ttu-id="ea684-104">このトピックでは、F# プログラムにエントリ ポイントを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea684-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea684-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea684-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="ea684-106">解説</span><span class="sxs-lookup"><span data-stu-id="ea684-106">Remarks</span></span>

<span data-ttu-id="ea684-107">上記の構文で、*let-function-binding* は、`let` バインドで記述した関数の定義です。</span><span class="sxs-lookup"><span data-stu-id="ea684-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="ea684-108">実行可能ファイルとしてコンパイルされるプログラムのエントリ ポイントは、実行が正式に開始される位置です。</span><span class="sxs-lookup"><span data-stu-id="ea684-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="ea684-109">F# アプリケーションにエントリ ポイントを指定するには、プログラムの `main` 関数に `EntryPoint` 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="ea684-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="ea684-110">(`let` バインドを使用して作成される) この関数は、最後にコンパイルされるファイルの最後の関数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea684-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="ea684-111">最後にコンパイルされるファイルは、プロジェクト内の最後のファイル、またはコマンド ラインに渡す最後のファイルです。</span><span class="sxs-lookup"><span data-stu-id="ea684-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="ea684-112">エントリ ポイント関数の型は `string array -> int` です。</span><span class="sxs-lookup"><span data-stu-id="ea684-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="ea684-113">コマンド ラインに指定された引数は、文字列の配列に入れて `main` 関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="ea684-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="ea684-114">配列の最初の要素は、最初の引数です。実行可能ファイルの名前は、他の言語のものであるため、配列には含まれません。</span><span class="sxs-lookup"><span data-stu-id="ea684-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="ea684-115">戻り値は、プロセスの終了コードとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea684-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="ea684-116">通常、ゼロは成功を示します。ゼロ以外の値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="ea684-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="ea684-117">ゼロ以外のリターン コードの特定の意味について規則はありません。リターン コードの意味は、アプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ea684-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="ea684-118">単純な `main` 関数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea684-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="ea684-119">このコードをコマンド ライン `EntryPoint.exe 1 2 3` を使用して実行すると、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea684-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="ea684-120">暗黙的なエントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="ea684-120">Implicit Entry Point</span></span>

<span data-ttu-id="ea684-121">エントリ ポイントを明示的に示す **EntryPoint** 属性がプログラムにない場合は、最後にコンパイルされるファイル内の最上位レベルのバインドがエントリ ポイントとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea684-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea684-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea684-122">See also</span></span>

- [<span data-ttu-id="ea684-123">関数</span><span class="sxs-lookup"><span data-stu-id="ea684-123">Functions</span></span>](index.md)
- [<span data-ttu-id="ea684-124">let 束縛</span><span class="sxs-lookup"><span data-stu-id="ea684-124">let Bindings</span></span>](let-bindings.md)
