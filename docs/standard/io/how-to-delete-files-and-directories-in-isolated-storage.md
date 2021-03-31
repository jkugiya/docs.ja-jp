---
description: '詳細情報: 分離ストレージでファイルおよびディレクトリを削除する方法'
title: 方法:分離ストレージでファイルおよびディレクトリを削除する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: 9ea8ea16b4329989f8c2453153ef3d803a4cc598
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775683"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="0f263-103">方法:分離ストレージでファイルおよびディレクトリを削除する</span><span class="sxs-lookup"><span data-stu-id="0f263-103">How to: Delete Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="0f263-104">分離ストレージ ファイル内のディレクトリとファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="0f263-104">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="0f263-105">ストア内では、ファイル名とディレクトリ名はオペレーティング システムに依存し、仮想ファイル システムのルートに対して相対的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="0f263-105">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="0f263-106">Windows オペレーティング システムでは大文字小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="0f263-106">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="0f263-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> クラスには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> のディレクトリおよびファイルを削除するメソッドが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="0f263-107">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="0f263-108">存在しないファイルまたはディレクトリを削除しようとする場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException> の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0f263-108">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="0f263-109">名前にワイルドカード文字を含める場合、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> は <xref:System.IO.IsolatedStorage.IsolatedStorageException> の例外をスローし、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> は <xref:System.ArgumentException> の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="0f263-109">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="0f263-110">ディレクトリにファイルまたはサブディレクトリが含まれている場合、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="0f263-110">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="0f263-111"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> のメソッドを使用すると、既存のファイルとディレクトリを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="0f263-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="0f263-112">ストアの仮想ファイル システムを検索する方法の詳細については、「[方法 : 分離ストレージ内でファイルおよびディレクトリを検索する](how-to-find-existing-files-and-directories-in-isolated-storage.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f263-112">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f263-113">例</span><span class="sxs-lookup"><span data-stu-id="0f263-113">Example</span></span>  

 <span data-ttu-id="0f263-114">次のコード例は、いくつかのディレクトリとファイルを作成して削除します。</span><span class="sxs-lookup"><span data-stu-id="0f263-114">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0f263-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f263-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="0f263-116">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="0f263-116">Isolated Storage</span></span>](isolated-storage.md)
