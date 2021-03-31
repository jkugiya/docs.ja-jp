---
description: '詳細情報: PLINQ を使用してファイル ディレクトリを反復処理する方法'
title: '方法: PLINQ を使用してファイル ディレクトリを反復処理する'
ms.date: 03/30/2017
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 131350d34694b58ccd3a2e78eb2164495bd20708
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701912"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="00b7d-103">方法: PLINQ を使用してファイル ディレクトリを反復処理する</span><span class="sxs-lookup"><span data-stu-id="00b7d-103">How to: Iterate File Directories with PLINQ</span></span>

<span data-ttu-id="00b7d-104">この記事では、ファイル ディレクトリに対する操作を並列化する 2 とおりの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="00b7d-104">This article shows two ways to parallelize operations on file directories.</span></span> <span data-ttu-id="00b7d-105">最初のクエリでは、<xref:System.IO.Directory.GetFiles%2A> メソッドを使用して、ディレクトリとすべてのサブディレクトリ内のファイル名の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="00b7d-105">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="00b7d-106">このメソッドでは、配列全体が設定されるまで戻されないため、操作の開始時に待機時間が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00b7d-106">This method can introduce latency at the beginning of the operation, because it doesn't return until the entire array is populated.</span></span> <span data-ttu-id="00b7d-107">ただし、配列が作成されたら、PLINQ は配列を迅速に並列処理できます。</span><span class="sxs-lookup"><span data-stu-id="00b7d-107">However, after the array is populated, PLINQ can process it in parallel quickly.</span></span>  
  
<span data-ttu-id="00b7d-108">2 番目のクエリでは、即座に結果を返し始める静的な <xref:System.IO.Directory.EnumerateDirectories%2A> メソッドと <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="00b7d-108">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods, which begin returning results immediately.</span></span> <span data-ttu-id="00b7d-109">この方法での処理は、大規模なディレクトリ ツリーの反復処理では高速になる場合がありますが、処理時間は最初の例に比べると多くの要素に左右されます。</span><span class="sxs-lookup"><span data-stu-id="00b7d-109">This approach can be faster when you're iterating over large directory trees, but the processing time compared to the first example depends on many factors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00b7d-110">これらの例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。</span><span class="sxs-lookup"><span data-stu-id="00b7d-110">These examples are intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="00b7d-111">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00b7d-111">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="getfiles-example"></a><span data-ttu-id="00b7d-112">GetFiles の例</span><span class="sxs-lookup"><span data-stu-id="00b7d-112">GetFiles example</span></span>

 <span data-ttu-id="00b7d-113">この例では、ツリー内のすべてのディレクトリにアクセスできる場合、ファイル サイズが大きくない場合、アクセス時間が重要ではない場合の単純なシナリオで、ファイル ディレクトリを反復処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="00b7d-113">This example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes aren't large, and the access times are not significant.</span></span> <span data-ttu-id="00b7d-114">この方法では、ファイル名の配列が作成されている間、最初に待機時間が発生します。</span><span class="sxs-lookup"><span data-stu-id="00b7d-114">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a><span data-ttu-id="00b7d-115">EnumerateFiles の例</span><span class="sxs-lookup"><span data-stu-id="00b7d-115">EnumerateFiles example</span></span>

 <span data-ttu-id="00b7d-116">この例では、ツリー内のすべてのディレクトリにアクセスできる場合、ファイル サイズが大きくない場合、アクセス時間が重要ではない場合の単純なシナリオで、ファイル ディレクトリを反復処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="00b7d-116">This example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes aren't large, and the access times are not significant.</span></span> <span data-ttu-id="00b7d-117">この方法では、前の例よりも迅速に結果を生成し始めます。</span><span class="sxs-lookup"><span data-stu-id="00b7d-117">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="00b7d-118"><xref:System.IO.Directory.GetFiles%2A> を使用する場合は、ツリー内のすべてのディレクトリに対して必要なアクセス許可があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="00b7d-118">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="00b7d-119">アクセス許可がないと例外がスローされ、結果は返されません。</span><span class="sxs-lookup"><span data-stu-id="00b7d-119">Otherwise, an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="00b7d-120">PLINQ クエリで <xref:System.IO.Directory.EnumerateDirectories%2A> を使用する場合、反復処理を続行できるように I/O 例外を適切に処理することが問題となります。</span><span class="sxs-lookup"><span data-stu-id="00b7d-120">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="00b7d-121">コードで I/O 例外または承認されていないアクセスの例外を処理する必要がある場合は、「[方法: Parallel クラスを使用してファイル ディレクトリを反復処理する](how-to-iterate-file-directories-with-the-parallel-class.md)」で説明する方法を検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="00b7d-121">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="00b7d-122">ネットワーク経由のファイル I/O などで I/O の待機時間が問題となる場合は、「[TPL と従来の .NET 非同期プログラミング](tpl-and-traditional-async-programming.md)」およびこの[ブログの投稿](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)で説明する非同期 I/O の手法のいずれかを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="00b7d-122">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Asynchronous Programming](tpl-and-traditional-async-programming.md) and in this [blog post](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b7d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="00b7d-123">See also</span></span>

- [<span data-ttu-id="00b7d-124">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="00b7d-124">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
