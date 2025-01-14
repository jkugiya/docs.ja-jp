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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>方法:分離ストレージでストアを列挙する

<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 静的メソッドを使用すると、現在のユーザー用の分離ストアをすべて列挙できます。 このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageScope> 値を取り、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列挙子を返します。 ストアを列挙する場合、<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 値を指定する <xref:System.Security.Permissions.IsolatedStorageFilePermission> のアクセス許可が必要です。 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 値を使用して <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを呼び出す場合、現在のユーザーに対して定義された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトの配列が返されます。  
  
## <a name="example"></a>例  

 次のコード例は、ユーザーおよびアセンブリ別に分離されたストアを取得し、いくつかファイルを作成し、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを使用してそれらのファイルを取得します。  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [分離ストレージ](isolated-storage.md)
