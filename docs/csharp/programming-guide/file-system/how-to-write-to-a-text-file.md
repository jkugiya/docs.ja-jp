---
title: テキスト ファイルに書き込む方法 - C# プログラミング ガイド
description: C# でテキスト ファイルを記述する方法について説明します。 いくつかのコード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 02/11/2021
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.topic: how-to
ms.custom: contperf-fy21q3
ms.openlocfilehash: ecc3ba73161d4f4571bbc6ae0c9aaa3337586ef7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475618"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="6dbf4-104">テキスト ファイルに書き込む方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6dbf4-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="6dbf4-105">この記事では、ファイルにテキストを書き込むさまざまな方法の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-105">In this article, there are several examples showing various ways to write text to a file.</span></span> <span data-ttu-id="6dbf4-106">最初の 2 つの例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの便利な静的メソッドを使用し、すべての `IEnumerable<string>` の各要素と `string` をテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a `string` to a text file.</span></span> <span data-ttu-id="6dbf4-107">3 番目の例では、ファイルに書き込みながら各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-107">The third example shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="6dbf4-108">最初の 3 つの例では、ファイルの既存のコンテンツはすべて上書きします。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-108">In the first three examples, you overwrite all existing content in the file.</span></span> <span data-ttu-id="6dbf4-109">最後の例では、テキストを既存のファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-109">The final example shows how to append text to an existing file.</span></span>

 <span data-ttu-id="6dbf4-110">これらの例はいずれもリテラル文字列をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-110">These examples all write string literals to files.</span></span> <span data-ttu-id="6dbf4-111">ファイルに書き込まれるテキストの書式を設定する場合は、<xref:System.String.Format%2A> メソッドまたは C# の[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-111">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>

## <a name="write-a-collection-of-strings-to-a-file"></a><span data-ttu-id="6dbf4-112">ファイルに文字列のコレクションを書き込む</span><span class="sxs-lookup"><span data-stu-id="6dbf4-112">Write a collection of strings to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllLines.cs":::

<span data-ttu-id="6dbf4-113">上記のソース コードの例では、次を行います。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-113">The preceding source code example:</span></span>

- <span data-ttu-id="6dbf4-114">3 つの値で文字列の配列をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-114">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="6dbf4-115">次を行う、<xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> に対する呼び出しを待機します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-115">Awaits a call to <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="6dbf4-116">非同期的に *WriteLines.txt* という名前のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-116">Asynchronously creates a file name *WriteLines.txt*.</span></span> <span data-ttu-id="6dbf4-117">既にある場合は、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-117">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="6dbf4-118">ファイルに指定した行を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-118">Writes the given lines to the file.</span></span>
  - <span data-ttu-id="6dbf4-119">必要に応じて、自動的にフラッシュおよび破棄し、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-119">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-one-string-to-a-file"></a><span data-ttu-id="6dbf4-120">ファイルに文字列を 1 つ書き込む</span><span class="sxs-lookup"><span data-stu-id="6dbf4-120">Write one string to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllText.cs":::

<span data-ttu-id="6dbf4-121">上記のソース コードの例では、次を行います。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-121">The preceding source code example:</span></span>

- <span data-ttu-id="6dbf4-122">割り当てられた文字列リテラルを指定して、文字列をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-122">Instantiates a string given the assigned string literal.</span></span>
- <span data-ttu-id="6dbf4-123">次を行う、<xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> に対する呼び出しを待機します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-123">Awaits a call to <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="6dbf4-124">非同期的に *WriteText.txt* という名前のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-124">Asynchronously creates a file name *WriteText.txt*.</span></span> <span data-ttu-id="6dbf4-125">既にある場合は、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-125">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="6dbf4-126">指定したテキストをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-126">Writes the given text to the file.</span></span>
  - <span data-ttu-id="6dbf4-127">必要に応じて、自動的にフラッシュおよび破棄し、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-127">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-selected-strings-from-an-array-to-a-file"></a><span data-ttu-id="6dbf4-128">選択した文字列を配列からファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="6dbf4-128">Write selected strings from an array to a file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterOne.cs":::

<span data-ttu-id="6dbf4-129">上記のソース コードの例では、次を行います。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-129">The preceding source code example:</span></span>

- <span data-ttu-id="6dbf4-130">3 つの値で文字列の配列をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-130">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="6dbf4-131">[using 宣言](../../whats-new/csharp-8.md#using-declarations)として *WriteLines2.txt* のファイル パスを使用して <xref:System.IO.StreamWriter> をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-131">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations).</span></span>
- <span data-ttu-id="6dbf4-132">すべての行を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-132">Iterates through all the lines.</span></span>
- <span data-ttu-id="6dbf4-133">行に `"Second"` が含まれないときに、ファイルに行を書き込む <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> に対する呼び出しを条件付きで待機します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-133">Conditionally awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the line to the file when the line doesn't contain `"Second"`.</span></span>

## <a name="append-text-to-an-existing-file"></a><span data-ttu-id="6dbf4-134">既存のファイルにテキストを追加する</span><span class="sxs-lookup"><span data-stu-id="6dbf4-134">Append text to an existing file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterTwo.cs":::

<span data-ttu-id="6dbf4-135">上記のソース コードの例では、次を行います。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-135">The preceding source code example:</span></span>

- <span data-ttu-id="6dbf4-136">3 つの値で文字列の配列をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-136">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="6dbf4-137">[using 宣言](../../whats-new/csharp-8.md#using-declarations)として *WriteLines2.txt* のファイル パスを使用し、追加するために `true` を渡して <xref:System.IO.StreamWriter> をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-137">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations), passing in `true` to append.</span></span>
- <span data-ttu-id="6dbf4-138">文字列を追加された行としてファイルに書き込む、<xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> に対する呼び出しを待機します。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-138">Awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the string to the file as an appended line.</span></span>

## <a name="exceptions"></a><span data-ttu-id="6dbf4-139">例外</span><span class="sxs-lookup"><span data-stu-id="6dbf4-139">Exceptions</span></span>

<span data-ttu-id="6dbf4-140">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-140">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="6dbf4-141"><xref:System.InvalidOperationException>: ファイルは存在するが、読み取り専用である。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-141"><xref:System.InvalidOperationException>: The file exists and is read-only.</span></span>
- <span data-ttu-id="6dbf4-142"><xref:System.IO.PathTooLongException>: パス名が長すぎる。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-142"><xref:System.IO.PathTooLongException>: The path name may be too long.</span></span>
- <span data-ttu-id="6dbf4-143"><xref:System.IO.IOException>: ディスクがいっぱいになっている。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-143"><xref:System.IO.IOException>: The disk may be full.</span></span>

<span data-ttu-id="6dbf4-144">ファイル システムの操作時に例外が発生する可能性がある条件は他にもあるため、防御的なプログラムを書くことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6dbf4-144">There are additional conditions that may cause exceptions when working with the file system, it is best to program defensively.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dbf4-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dbf4-145">See also</span></span>

- [<span data-ttu-id="6dbf4-146">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6dbf4-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6dbf4-147">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6dbf4-147">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="6dbf4-148">サンプル: コレクションをアプリケーション ストレージに保存する</span><span class="sxs-lookup"><span data-stu-id="6dbf4-148">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
