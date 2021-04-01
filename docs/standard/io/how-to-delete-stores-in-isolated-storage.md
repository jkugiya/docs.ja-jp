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
# <a name="how-to-delete-stores-in-isolated-storage"></a>方法:分離ストレージでストアを削除する

分離ストレージ ファイルを削除するため、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスは 2 つのメソッドを提供します。  
  
- インスタンス メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> は引数を使わず、そのインスタンス メソッドを呼び出すストアを削除します。 この操作にアクセス許可は必要ありません。 ストアにアクセスできるすべてのコードは、その内部の一部のデータやすべてのデータを削除できます。  
  
- 静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> は <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 列挙値を使い、コードを実行するユーザーのすべてのストアを削除します。 この操作を実行するには、 <xref:System.Security.Permissions.IsolatedStorageFilePermission> の値に対する <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> アクセス許可が必要です。  
  
## <a name="example"></a>例  

 静的およびンスタンス <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> メソッドの使い方を次のコード例に示します。 クラスは、次の 2 つのストアを取得します。1 つは、ユーザーとアセンブリで使うように分離して、もう 1 つは、ユーザー、ドメイン、アセンブリで使うように分離します。 次に、分離ストレージ ファイル <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> の  `isoStore1`メソッドを呼び出すことにより、ユーザー、ドメイン、アセンブリのストアが削除されます。 その後、静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>を呼び出すことによって、ユーザーの残りのストアすべてを削除します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [分離ストレージ](isolated-storage.md)
