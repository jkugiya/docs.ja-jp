---
description: '詳細情報: 分離ストレージでストアを列挙する方法'
title: 方法:分離ストレージでストアを列挙する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: f1acd6eaac5e81e9ea7a63b0eac4ef5a4a70efde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775618"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="3b4a8-103">方法:分離ストレージでストアを列挙する</span><span class="sxs-lookup"><span data-stu-id="3b4a8-103">How to: Enumerate Stores for Isolated Storage</span></span>

<span data-ttu-id="3b4a8-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 静的メソッドを使用すると、現在のユーザー用の分離ストアをすべて列挙できます。</span><span class="sxs-lookup"><span data-stu-id="3b4a8-104">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="3b4a8-105">このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageScope> 値を取り、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="3b4a8-105">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="3b4a8-106">ストアを列挙する場合、<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 値を指定する <xref:System.Security.Permissions.IsolatedStorageFilePermission> のアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="3b4a8-106">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="3b4a8-107"><xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 値を使用して <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを呼び出す場合、現在のユーザーに対して定義された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトの配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="3b4a8-107">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b4a8-108">例</span><span class="sxs-lookup"><span data-stu-id="3b4a8-108">Example</span></span>  

 <span data-ttu-id="3b4a8-109">次のコード例は、ユーザーおよびアセンブリ別に分離されたストアを取得し、いくつかファイルを作成し、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを使用してそれらのファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="3b4a8-109">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3b4a8-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b4a8-110">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="3b4a8-111">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="3b4a8-111">Isolated Storage</span></span>](isolated-storage.md)
