---
description: '詳細情報: 分離ストレージでストアを削除する方法'
title: 方法:分離ストレージでストアを削除する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 3e454492c6a6e24feb57acf20afe1073d7ffbb4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775644"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="8c6f2-103">方法:分離ストレージでストアを削除する</span><span class="sxs-lookup"><span data-stu-id="8c6f2-103">How to: Delete Stores in Isolated Storage</span></span>

<span data-ttu-id="8c6f2-104">分離ストレージ ファイルを削除するため、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスは 2 つのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="8c6f2-105">インスタンス メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> は引数を使わず、そのインスタンス メソッドを呼び出すストアを削除します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-105">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="8c6f2-106">この操作にアクセス許可は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-106">No permissions are required for this operation.</span></span> <span data-ttu-id="8c6f2-107">ストアにアクセスできるすべてのコードは、その内部の一部のデータやすべてのデータを削除できます。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-107">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="8c6f2-108">静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> は <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 列挙値を使い、コードを実行するユーザーのすべてのストアを削除します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-108">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="8c6f2-109">この操作を実行するには、 <xref:System.Security.Permissions.IsolatedStorageFilePermission> の値に対する <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-109">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c6f2-110">例</span><span class="sxs-lookup"><span data-stu-id="8c6f2-110">Example</span></span>  

 <span data-ttu-id="8c6f2-111">静的およびンスタンス <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> メソッドの使い方を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-111">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="8c6f2-112">クラスは、次の 2 つのストアを取得します。1 つは、ユーザーとアセンブリで使うように分離して、もう 1 つは、ユーザー、ドメイン、アセンブリで使うように分離します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-112">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="8c6f2-113">次に、分離ストレージ ファイル <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> の  `isoStore1`メソッドを呼び出すことにより、ユーザー、ドメイン、アセンブリのストアが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-113">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="8c6f2-114">その後、静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>を呼び出すことによって、ユーザーの残りのストアすべてを削除します。</span><span class="sxs-lookup"><span data-stu-id="8c6f2-114">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8c6f2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c6f2-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="8c6f2-116">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="8c6f2-116">Isolated Storage</span></span>](isolated-storage.md)
