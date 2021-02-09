---
description: '詳細情報: 方法:モデル ファイルとマッピング ファイルを組み込みリソースにする'
title: '方法: モデル ファイルとマッピング ファイルを組み込みリソースにする'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 373dfc2c93adfc510341ec0ea0487ad8962aa3e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697518"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="5f898-103">方法: モデル ファイルとマッピング ファイルを組み込みリソースにする</span><span class="sxs-lookup"><span data-stu-id="5f898-103">How to: Make Model and Mapping Files Embedded Resources</span></span>

<span data-ttu-id="5f898-104">Entity Framework を使用すると、モデル ファイルとマッピング ファイルをアプリケーションの組み込みリソースとして配置できます。</span><span class="sxs-lookup"><span data-stu-id="5f898-104">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="5f898-105">モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f898-105">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="5f898-106">詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5f898-106">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="5f898-107">既定では、Entity Data Model ツールによって、モデル ファイルとマッピング ファイルが組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5f898-107">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="5f898-108">モデル ファイルとマッピング ファイルを手動で定義する場合は、Entity Framework アプリケーションと共にモデル ファイルとマッピング ファイルが組み込みリソースとして確実に配置されるように、この手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f898-108">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f898-109">組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f898-109">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="5f898-110">モデル ファイルとマッピング ファイルを組み込むには</span><span class="sxs-lookup"><span data-stu-id="5f898-110">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="5f898-111">**ソリューション エクスプローラー** で、概念 (.csdl) ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f898-111">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="5f898-112">**[プロパティ]** ペインで、 **[ビルド アクション]** を **[組み込まれたリソース]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5f898-112">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="5f898-113">ストレージ (.ssdl) ファイルとマッピング (.msl) ファイルに対して手順 1. と手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="5f898-113">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="5f898-114">**ソリューション エクスプローラー** で、App.config ファイルをダブルクリックし、次のいずれかの形式に基づいて `connectionString` 属性の `Metadata` パラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="5f898-114">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="5f898-115">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="5f898-115">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="5f898-116">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="5f898-116">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="5f898-117">詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5f898-117">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f898-118">例</span><span class="sxs-lookup"><span data-stu-id="5f898-118">Example</span></span>  

 <span data-ttu-id="5f898-119">次の接続文字列では、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) の組み込みモデル ファイルとマッピング ファイルが参照されます。</span><span class="sxs-lookup"><span data-stu-id="5f898-119">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="5f898-120">この接続文字列は、プロジェクトの App.config ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="5f898-120">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5f898-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f898-121">See also</span></span>

- [<span data-ttu-id="5f898-122">モデリングとマッピング</span><span class="sxs-lookup"><span data-stu-id="5f898-122">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="5f898-123">方法: 接続文字列を定義する</span><span class="sxs-lookup"><span data-stu-id="5f898-123">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="5f898-124">方法: EntityConnection の接続文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="5f898-124">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="5f898-125">[ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5f898-125">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
