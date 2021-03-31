---
description: '詳細情報: 分離ストレージの領域不足状態に備える方法'
title: 方法:分離ストレージの領域不足状態に備える
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
ms.openlocfilehash: 782fcf66a8cf3f609153c897fb9248f53a764150
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775800"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="c66ab-103">方法:分離ストレージの領域不足状態に備える</span><span class="sxs-lookup"><span data-stu-id="c66ab-103">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="c66ab-104">分離ストレージを使用するコードは、分離ストレージ ファイルとディレクトリが存在するデータ コンパートメントの最大サイズを規定する[クォータ](isolated-storage.md#quotas)の制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-104">Code that uses isolated storage is constrained by a [quota](isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="c66ab-105">クォータはセキュリティ ポリシーによって定義され、管理者が構成できます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-105">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="c66ab-106">データの書き込み時に許容される最大サイズを超えると、<xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外がスローされ、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="c66ab-106">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="c66ab-107">データ ストレージを容量不足にしてアプリケーションの要求拒否を引き起こす可能性がある悪意のあるサービス拒否攻撃を、この方法で防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-107">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="c66ab-108">この理由で特定の書き込み試行が失敗する可能性があるかどうかを判断できるように、<xref:System.IO.IsolatedStorage.IsolatedStorage> クラスには 3 つの読み取り専用のプロパティ <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c66ab-108">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="c66ab-109">これらのプロパティを使用して、ストアへの書き込みによってストアの最大許容サイズを超えるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-109">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="c66ab-110">分離ストレージには同時にアクセスできます。そのため、残りのストレージ容量を計算しても、ストアに書き込もうとするまでにストレージ領域が使用される可能性がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c66ab-110">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="c66ab-111">ただし、ストアの最大サイズを使用すると、使用できるストレージの上限に近づいているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-111">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="c66ab-112"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> プロパティはアセンブリからの証拠に応じて適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="c66ab-112">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="c66ab-113">この理由から、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドを使用して作成された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトでのみ、このプロパティを取得するようにします。</span><span class="sxs-lookup"><span data-stu-id="c66ab-113">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="c66ab-114">その他の方法で作成された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクト (<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドから返されたオブジェクトなど) は正確な最大サイズを返しません。</span><span class="sxs-lookup"><span data-stu-id="c66ab-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="c66ab-115">例</span><span class="sxs-lookup"><span data-stu-id="c66ab-115">Example</span></span>

<span data-ttu-id="c66ab-116">次のコード例は、分離ストアを取得し、いくつかのファイルを作成し、<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="c66ab-116">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="c66ab-117">残りの容量はバイト単位で報告されます。</span><span class="sxs-lookup"><span data-stu-id="c66ab-117">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="c66ab-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c66ab-118">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="c66ab-119">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="c66ab-119">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="c66ab-120">方法: 分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="c66ab-120">How to: Obtain Stores for Isolated Storage</span></span>](how-to-obtain-stores-for-isolated-storage.md)
