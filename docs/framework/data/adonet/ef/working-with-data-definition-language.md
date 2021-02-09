---
description: '詳細情報: データ定義言語の操作'
title: データ定義言語の操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 2f924087d12b519e6086289a91dedce3a88199f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673025"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="4a039-103">データ定義言語の操作</span><span class="sxs-lookup"><span data-stu-id="4a039-103">Working with Data Definition Language</span></span>

<span data-ttu-id="4a039-104">.NET Framework バージョン 4 以降の Entity Framework では、データ定義言語 (DDL) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4a039-104">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="4a039-105">これにより、接続文字列、およびストレージ (SSDL) モデルのメターデータに基づいて、データベース インスタンスを作成または削除できます。</span><span class="sxs-lookup"><span data-stu-id="4a039-105">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="4a039-106"><xref:System.Data.Objects.ObjectContext> の次のメソッドでは、接続文字列と SSDL の内容を使用して、データベースの作成と削除、データベースが存在するかどうかの確認、生成された DDL スクリプトの表示を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a039-106">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="4a039-107">DDL コマンドを実行するには、十分なアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="4a039-107">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="4a039-108">上記に示したメソッドは、ほとんどの作業を基になる ADO.NET データ プロバイダーに委任します。</span><span class="sxs-lookup"><span data-stu-id="4a039-108">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="4a039-109">データベース オブジェクトの生成に使用される名前付け規則が、照会および更新に使用される規則と一致していることは、プロバイダーによって保証されています。</span><span class="sxs-lookup"><span data-stu-id="4a039-109">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="4a039-110">次の例は、既存のモデルを基にデータベースを生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4a039-110">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="4a039-111">また、新しいエンティティ オブジェクトはオブジェクト コンテキストに追加され、データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4a039-111">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4a039-112">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4a039-112">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="4a039-113">既存のモデルに基づいてデータベースを定義するには</span><span class="sxs-lookup"><span data-stu-id="4a039-113">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="4a039-114">コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a039-114">Create a console application.</span></span>  
  
2. <span data-ttu-id="4a039-115">既存のモデルをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="4a039-115">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="4a039-116">`SchoolModel` という名前の空のモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="4a039-116">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="4a039-117">空のモデルを作成する方法については、「[方法: 新しい .edmx ファイルを作成する](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))」トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4a039-117">To create an empty model, see the [How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="4a039-118">SchoolModel.edmx ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4a039-118">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="4a039-119">「[School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))」から、School モデルの概念、ストレージ、マッピングの内容をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4a039-119">Copy the conceptual, storage, and mapping content for the School model from the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="4a039-120">SchoolModel.edmx ファイルを開き、`edmx:Runtime` タグ内にその内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4a039-120">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="4a039-121">main 関数に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="4a039-121">Add the following code to your main function.</span></span> <span data-ttu-id="4a039-122">このコードでは、データベース サーバーへの接続文字列を初期化し、DDL スクリプトを表示して、データベースを作成します。さらに、コンテキストに新しいエンティティを追加して、データベースに変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="4a039-122">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
