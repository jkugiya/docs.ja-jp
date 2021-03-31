---
description: '詳細情報: 分離ストレージでストアを取得する方法'
title: 方法:分離ストレージでストアを取得する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
ms.openlocfilehash: 4d65eb23d4e6935b72dd32926c097f7cf0ab6b85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775592"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="5de96-103">方法:分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="5de96-103">How to: Obtain Stores for Isolated Storage</span></span>

<span data-ttu-id="5de96-104">分離ストアでは、データ コンパートメント内の仮想ファイル システムを公開します。</span><span class="sxs-lookup"><span data-stu-id="5de96-104">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="5de96-105"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスでは、分離ストアと対話するためのいくつかのメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5de96-105">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="5de96-106">ストアを作成して取得するために、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> では次の 3 つの静的メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5de96-106">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="5de96-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> は、ユーザーおよびアセンブリ別に分離されるストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="5de96-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="5de96-108"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> は、ドメインおよびアセンブリ別に分離されるストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="5de96-108"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="5de96-109">両方のメソッドで、呼び出し元のコードに属するストアが取得されます。</span><span class="sxs-lookup"><span data-stu-id="5de96-109">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="5de96-110">静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> は、スコープ パラメーターの組み合わせを渡すことで指定される分離ストアを返します。</span><span class="sxs-lookup"><span data-stu-id="5de96-110">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="5de96-111">次のコードでは、ユーザー、アセンブリ、およびドメイン別に分離されるストアを返します。</span><span class="sxs-lookup"><span data-stu-id="5de96-111">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="5de96-112"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドを使用して、ストアが移動ユーザー プロファイルと共にローミングするように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5de96-112">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="5de96-113">この設定方法の詳細については、「[分離のタイプ](types-of-isolation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5de96-113">For details on how to set this up, see [Types of Isolation](types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="5de96-114">異なるアセンブリ内から取得される分離ストアは、既定では異なるストアとなります。</span><span class="sxs-lookup"><span data-stu-id="5de96-114">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="5de96-115"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドのパラメーターでアセンブリまたはドメインの証拠を渡すことで、異なるアセンブリまたはドメインのストアにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5de96-115">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="5de96-116">この場合、アプリケーション ドメイン ID で分離ストレージにアクセスするアクセス許可が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5de96-116">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="5de96-117">詳細については、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドのオーバーロードに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5de96-117">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="5de96-118"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、および <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドは <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="5de96-118">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="5de96-119">状況に最適な分離タイプの判別に役立つ「[分離のタイプ](types-of-isolation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5de96-119">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](types-of-isolation.md).</span></span> <span data-ttu-id="5de96-120">分離ストレージ ファイル オブジェクトがある場合は、分離ストレージ メソッドを使用して、ファイルとディレクトリの読み取り、書き込み、作成、削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5de96-120">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="5de96-121">ストア自体を取得するのに十分なアクセス権がないコードに <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを渡さないようにするためのメカニズムはありません。</span><span class="sxs-lookup"><span data-stu-id="5de96-121">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="5de96-122">ドメインとアセンブリの ID と分離ストレージのアクセス許可が確認されるのは、通常、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドで <xref:System.IO.IsolatedStorage.IsolatedStorage> オブジェクトへの参照が取得される場合のみです。</span><span class="sxs-lookup"><span data-stu-id="5de96-122">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="5de96-123">したがって、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> への参照を保護するのは、これらの参照を使用するコードの役目です。</span><span class="sxs-lookup"><span data-stu-id="5de96-123">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5de96-124">例</span><span class="sxs-lookup"><span data-stu-id="5de96-124">Example</span></span>  

 <span data-ttu-id="5de96-125">次のコードでは、ユーザーとアセンブリ別に分離されるストアを取得するクラスの単純な例を示します。</span><span class="sxs-lookup"><span data-stu-id="5de96-125">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="5de96-126"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドが渡す引数に <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> を追加することで、ユーザー、ドメイン、およびアセンブリ別に分離されるストアを取得するようにコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5de96-126">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="5de96-127">コードを実行したら、コマンド ラインで「**StoreAdm /LIST**」と入力して、ストアが作成されたことを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="5de96-127">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="5de96-128">これにより、[分離ストレージ ツール (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) が実行され、ユーザーの現在の分離ストアがすべてリストされます。</span><span class="sxs-lookup"><span data-stu-id="5de96-128">This runs the [Isolated Storage tool (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5de96-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5de96-129">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="5de96-130">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="5de96-130">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="5de96-131">分離のタイプ</span><span class="sxs-lookup"><span data-stu-id="5de96-131">Types of Isolation</span></span>](types-of-isolation.md)
- [<span data-ttu-id="5de96-132">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="5de96-132">Assemblies in .NET</span></span>](../assembly/index.md)
