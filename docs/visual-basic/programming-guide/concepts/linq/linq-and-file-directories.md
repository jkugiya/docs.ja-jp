---
description: '詳細情報: LINQ とファイル ディレクトリ (Visual Basic)'
title: LINQ とファイル ディレクトリ
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: ed7f4151acde51794269e5028820397f9a3bb3f9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426765"
---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="b9280-103">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-103">LINQ and File Directories (Visual Basic)</span></span>

<span data-ttu-id="b9280-104">多くのファイル システム操作は基本的にクエリであるため、LINQ での使用に最適です。</span><span class="sxs-lookup"><span data-stu-id="b9280-104">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="b9280-105">ここで示すクエリは破壊的ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9280-105">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="b9280-106">元のファイルやフォルダーの内容が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="b9280-106">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="b9280-107">これは、クエリは副作用を引き起こすべきではないという規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="b9280-107">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="b9280-108">一般に、参照元データを変更するコード (create、update、または delete の各演算子を実行するクエリなど) は、単にデータを照会するだけのコードとは分離する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9280-108">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="b9280-109">このセクションでは、以下のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9280-109">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="b9280-110">方法: 指定された属性または名前のファイルを照会する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-110">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="b9280-111"><xref:System.IO.FileInfo> オブジェクトで 1 つ以上のプロパティを調べ、ファイルを検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-111">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="b9280-112">方法: 拡張機能でファイルをグループ化する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-112">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="b9280-113">ファイル名拡張子に基づいて、<xref:System.IO.FileInfo> オブジェクトのグループを返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-113">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="b9280-114">方法: 一連のフォルダーの合計バイト数を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-114">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="b9280-115">指定したディレクトリ ツリー内のすべてのファイルの合計バイト数を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-115">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="b9280-116">[方法: 2 つのフォルダーの内容を比較する (LINQ) (Visual Basic)](how-to-compare-the-contents-of-two-folders-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9280-116">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="b9280-117">指定した 2 つのフォルダーに存在するファイルをすべて返す方法と、一方のフォルダーにのみ存在し、もう一方には存在しないファイルをすべて返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-117">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="b9280-118">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-118">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="b9280-119">ディレクトリ ツリーで、最もサイズの大きいファイルまたは最もサイズの小さいファイル、あるいは指定した数のファイルを返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-119">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="b9280-120">方法: ディレクトリツリーで重複するファイルを照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-120">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="b9280-121">指定したディレクトリ ツリーの複数の場所に出現するすべてのファイル名をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-121">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="b9280-122">また、カスタム比較演算子に基づいて、より複雑な比較を実行する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-122">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="b9280-123">フォルダー内のファイルの内容を照会する方法 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-123">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="b9280-124">ツリー内のフォルダーを反復処理し、各ファイルを開き、ファイルの内容を照会する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9280-124">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="b9280-125">コメント</span><span class="sxs-lookup"><span data-stu-id="b9280-125">Comments</span></span>  

 <span data-ttu-id="b9280-126">ファイル システムの内容を正確に表し、例外を適切に処理するデータ ソースを作成する手順は複雑になります。</span><span class="sxs-lookup"><span data-stu-id="b9280-126">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="b9280-127">ここに示す例では、指定したルート フォルダーおよびすべてのサブフォルダーの下にある、すべてのファイルを表す <xref:System.IO.FileInfo> オブジェクトのスナップショット コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9280-127">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="b9280-128">各 <xref:System.IO.FileInfo> の実際の状態は、クエリの実行の開始時点から終了時点までの間に変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9280-128">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="b9280-129">たとえば、データ ソースとして使用する <xref:System.IO.FileInfo> オブジェクトの一覧を作成したとします。</span><span class="sxs-lookup"><span data-stu-id="b9280-129">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="b9280-130">クエリで `Length` プロパティにアクセスしようとすると、<xref:System.IO.FileInfo> オブジェクトがファイル システムにアクセスして `Length` の値を更新しようとします。</span><span class="sxs-lookup"><span data-stu-id="b9280-130">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="b9280-131">ファイルがもう存在しない場合は、ファイル システムを直接照会していなくても、クエリから <xref:System.IO.FileNotFoundException> が返されます。</span><span class="sxs-lookup"><span data-stu-id="b9280-131">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="b9280-132">ここで示すクエリの中には、状況により、このような特定の例外を処理する個別のメソッドを使用しているものがあります。</span><span class="sxs-lookup"><span data-stu-id="b9280-132">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="b9280-133">別の方法として、<xref:System.IO.FileSystemWatcher> を使用して、データ ソースを動的に更新して常に最新の状態に保つこともできます。</span><span class="sxs-lookup"><span data-stu-id="b9280-133">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9280-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9280-134">See also</span></span>

- [<span data-ttu-id="b9280-135">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9280-135">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
