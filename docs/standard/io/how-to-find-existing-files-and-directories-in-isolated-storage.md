---
description: '詳細情報: 分離ストレージ内で既存のファイルおよびディレクトリを検索する方法'
title: 方法:分離ストレージ内で既存のファイルおよびディレクトリを検索する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: 8f8b48046bb65a2a5ba66df7212445bcd965682a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775605"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="17607-103">方法:分離ストレージ内で既存のファイルおよびディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="17607-103">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="17607-104">分離ストレージ内のディレクトリを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="17607-104">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17607-105">このメソッドは、検索パターンを表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="17607-105">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="17607-106">検索パターンでは、1 文字を表すワイルドカード文字 (?) と複数の文字を表すワイルドカード文字 (\*) の両方を使用できます。しかし、これらのワイルドカード文字は、名前の最後の部分で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17607-106">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="17607-107">たとえば、`directory1/*ect*` は有効な検索文字列ですが、`*ect*/directory2` は無効です。</span><span class="sxs-lookup"><span data-stu-id="17607-107">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="17607-108">ファイルを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="17607-108">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17607-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> に適用される、検索文字列内のワイルドカード文字の制約と同じ制約が <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="17607-109">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="17607-110">これらはいずれも再帰的メソッドではありません。つまり、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> には、ストア内のすべてのディレクトリまたはファイルを一覧表示するためのメソッドは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="17607-110">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="17607-111">ただし、次のコード例には、再帰的メソッドの例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="17607-111">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17607-112">例</span><span class="sxs-lookup"><span data-stu-id="17607-112">Example</span></span>  

 <span data-ttu-id="17607-113">分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="17607-113">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="17607-114">最初に、ユーザー、ドメイン、アセンブリ別に分離されたストアを取得し、`isoStore` 変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="17607-114">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="17607-115"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> メソッドは複数の異なるディレクトリをセットアップするために使用され、<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> コンストラクターではそれらのディレクトリ内にいくつかのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="17607-115">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="17607-116">次に、`GetAllDirectories` メソッドの結果内をループします。</span><span class="sxs-lookup"><span data-stu-id="17607-116">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="17607-117">このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> を使用して現在のディレクトリ内のすべてのディレクトリ名を検索します。</span><span class="sxs-lookup"><span data-stu-id="17607-117">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="17607-118">これらのディレクトリ名は配列で格納されているので、`GetAllDirectories` は自分自身を呼び出し、検出したそれぞれのディレクトリを渡します。</span><span class="sxs-lookup"><span data-stu-id="17607-118">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="17607-119">結果として、すべてのディレクトリ名が配列に返されます。</span><span class="sxs-lookup"><span data-stu-id="17607-119">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="17607-120">次に、`GetAllFiles` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="17607-120">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="17607-121">このメソッドは、`GetAllDirectories` を呼び出してすべてのディレクトリの名前を検索した後、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> メソッドを使用して、各ディレクトリにファイルが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="17607-121">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="17607-122">結果は、表示のために配列で返されます。</span><span class="sxs-lookup"><span data-stu-id="17607-122">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="17607-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="17607-123">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="17607-124">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="17607-124">Isolated Storage</span></span>](isolated-storage.md)
