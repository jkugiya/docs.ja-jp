---
description: '詳細情報: 分離ストレージ内でファイルの読み取りと書き込みを行う方法'
title: 方法:分離ストレージ内でファイルの読み取りと書き込みを行う
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: 6e88cc4c590c44394768472ce8bd5fd89ac99d38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775540"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="4fc21-103">方法:分離ストレージ内でファイルの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="4fc21-103">How to: Read and Write to Files in Isolated Storage</span></span>

<span data-ttu-id="4fc21-104">分離ストアのファイルを読み取ったり、それに書き込んだりするには、ストリーム リーダー (<xref:System.IO.StreamReader> オブジェクト) またはストリーム ライター (<xref:System.IO.StreamWriter> オブジェクト) で <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fc21-104">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fc21-105">例</span><span class="sxs-lookup"><span data-stu-id="4fc21-105">Example</span></span>  

 <span data-ttu-id="4fc21-106">次のコード例では、分離ストアを取得し、ストア内に TestStore.txt をという名前のファイルが存在するかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="4fc21-106">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="4fc21-107">存在しない場合、ファイルが作成され、"Hello Isolated Storage" とファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="4fc21-107">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="4fc21-108">TestStore.txt が既に存在する場合、コード例は、ファイルから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="4fc21-108">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4fc21-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fc21-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="4fc21-110">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="4fc21-110">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="4fc21-111">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="4fc21-111">Isolated Storage</span></span>](isolated-storage.md)
