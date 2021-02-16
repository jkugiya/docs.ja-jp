---
description: '詳細情報: LINQ と文字列 (Visual Basic)'
title: LINQ と文字列
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 16e1a2c3d8cee30643743400ad21dfc4ff15c14d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469787"
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="21bbc-103">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-103">LINQ and Strings (Visual Basic)</span></span>

<span data-ttu-id="21bbc-104">文字列やそのコレクションは、LINQ を使って照会したり変換したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-104">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="21bbc-105">特に、テキスト ファイル内の半構造化されたデータでその利便性が発揮されます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-105">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="21bbc-106">LINQ クエリは、従来の文字列関数や正規表現と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-106">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="21bbc-107">たとえば、<xref:System.String.Split%2A> または <xref:System.Text.RegularExpressions.Regex.Split%2A> メソッドを使用して、文字列の配列を作成し、その後で LINQ を使用してクエリを実行したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-107">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="21bbc-108">LINQ クエリの `where` 句で <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-108">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="21bbc-109">LINQ を使用して、正規表現によって返される <xref:System.Text.RegularExpressions.MatchCollection> の結果に対してクエリを実行したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-109">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="21bbc-110">このセクションで説明する手法を使えば、半構造化されたテキスト データを XML に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-110">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="21bbc-111">詳細については、[CSV ファイルから XML を生成する (C#)](../../../../standard/linq/generate-xml-csv-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21bbc-111">For more information, see [How to: Generate XML from CSV Files](../../../../standard/linq/generate-xml-csv-files.md).</span></span>  
  
 <span data-ttu-id="21bbc-112">このセクションの例は、次の 2 つのカテゴリに分かれています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-112">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="21bbc-113">テキスト ブロックの照会</span><span class="sxs-lookup"><span data-stu-id="21bbc-113">Querying a Block of Text</span></span>  

 <span data-ttu-id="21bbc-114"><xref:System.String.Split%2A> メソッドまたは <xref:System.Text.RegularExpressions.Regex.Split%2A> メソッドを使用して、テキスト ブロックをクエリ可能な小さな文字列の配列に分割することによって、テキスト ブロックのクエリ、分析、および変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-114">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="21bbc-115">単語や文、段落、ページなどの単位にソース テキストを分割できるほか、クエリ内で必要であれば、さらに細かく分割することもできます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-115">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="21bbc-116">方法: 文字列での単語の出現回数をカウントする (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-116">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="21bbc-117">テキストに対する単純なクエリを LINQ で行う方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-117">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="21bbc-118">方法: 指定された単語のセットを含む文章を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-118">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="21bbc-119">区切りを指定してテキスト ファイルを分割する方法やその各構成要素に対してクエリを実行する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-119">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="21bbc-120">方法: 文字列内の文字を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-120">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="21bbc-121">文字列がクエリ可能型であることを実証します。</span><span class="sxs-lookup"><span data-stu-id="21bbc-121">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="21bbc-122">LINQ クエリと正規表現を組み合わせる方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-122">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="21bbc-123">LINQ クエリで正規表現を使い、フィルター処理されたクエリ結果に対して複雑なパターン マッチを行う方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-123">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="21bbc-124">半構造化されたテキスト形式データのクエリ</span><span class="sxs-lookup"><span data-stu-id="21bbc-124">Querying Semi-Structured Data in Text Format</span></span>  

 <span data-ttu-id="21bbc-125">テキスト ファイルにはさまざまな種類がありますが、タブ区切りファイルやコンマ区切りファイル、固定長行など同様の形式を持った一連の行で構成されていることは少なくありません。</span><span class="sxs-lookup"><span data-stu-id="21bbc-125">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="21bbc-126">そのようなテキスト ファイルをメモリに読み込んだ後、LINQ を使って、必要な行を照会したり編集したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-126">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="21bbc-127">複数ソースからのデータを組み合わせる作業も LINQ クエリなら簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="21bbc-127">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="21bbc-128">方法: 2 つのリストの差集合を見つける (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-128">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="21bbc-129">ある特定のリストには存在しているものの、それ以外には存在しない文字列をすべて探す方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-129">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="21bbc-130">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-130">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="21bbc-131">単語やフィールドに基づいてテキスト行を並べ替える方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-131">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="21bbc-132">方法: 区切りファイルのフィールドの順序を変更する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-132">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="21bbc-133">.csv ファイルの行に含まれるフィールドを並べ替える方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-133">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="21bbc-134">方法: 文字列コレクションを結合および比較する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-134">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="21bbc-135">文字列リストをさまざまな方法で結合する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-135">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="21bbc-136">方法: 複数のソースからオブジェクトコレクションにデータを設定する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-136">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="21bbc-137">複数のテキスト ファイルをデータ ソースとしてオブジェクトのコレクションを作成する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-137">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="21bbc-138">方法: 異種ファイルのコンテンツを結合する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-138">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="21bbc-139">2 つのリストに含まれる文字列を、一致するキーを使って 1 つの文字列に結合する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-139">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="21bbc-140">方法: グループを使用してファイルを複数のファイルに分割する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-140">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="21bbc-141">1 つのファイルをデータ ソースとして新しいファイルを作成する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-141">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="21bbc-142">方法: CSV テキスト ファイルの列値を計算する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-142">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="21bbc-143">.csv ファイルでテキスト データに対して数学的計算を実行する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="21bbc-143">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bbc-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="21bbc-144">See also</span></span>

- [<span data-ttu-id="21bbc-145">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21bbc-145">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="21bbc-146">方法: CSV ファイルから XML を生成する</span><span class="sxs-lookup"><span data-stu-id="21bbc-146">How to: Generate XML from CSV Files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
