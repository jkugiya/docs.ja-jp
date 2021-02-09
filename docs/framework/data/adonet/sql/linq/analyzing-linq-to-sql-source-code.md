---
description: '詳細情報: LINQ to SQL のソース コードの分析'
title: LINQ to SQL のソース コードの分析
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: acf80b10c3bb817cf3fd87876da75a47e2fe271c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712793"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="1b394-103">LINQ to SQL のソース コードの分析</span><span class="sxs-lookup"><span data-stu-id="1b394-103">Analyzing LINQ to SQL Source Code</span></span>

<span data-ttu-id="1b394-104">以下の手順を実行すると、Northwind サンプル データベースから [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のソース コードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b394-104">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="1b394-105">オブジェクト モデルの要素とデータベースの要素を比較対照することで、個別の項目がどのように対応付けられているかがわかります。</span><span class="sxs-lookup"><span data-stu-id="1b394-105">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b394-106">Visual Studio を使用している開発者は、O/R デザイナーを使用してこのコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="1b394-106">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="1b394-107">開発用コンピューターに Northwind サンプル データベースがない場合は、無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1b394-107">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="1b394-108">詳細については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b394-108">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="1b394-109">SqlMetal コマンド ライン ツールを使用して、Visual Basic または C# のソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="1b394-109">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="1b394-110">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b394-110">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="1b394-111">コマンド プロンプトで次のコマンドを入力すると、ストアド プロシージャおよび関数を含めて Visual Basic または C# のソース ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="1b394-111">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="1b394-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b394-112">See also</span></span>

- [<span data-ttu-id="1b394-113">参照</span><span class="sxs-lookup"><span data-stu-id="1b394-113">Reference</span></span>](reference.md)
- [<span data-ttu-id="1b394-114">背景情報</span><span class="sxs-lookup"><span data-stu-id="1b394-114">Background Information</span></span>](background-information.md)
