---
description: '詳細情報: 方法:DBML ファイルを変更してカスタマイズ コードを生成する'
title: '方法: DBML ファイルを変更してカスタマイズ コードを生成する'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 0dd4024b3f6a0ca0583de6bfbdb7463fab14d969
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786005"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="5dad8-103">方法: DBML ファイルを変更してカスタマイズ コードを生成する</span><span class="sxs-lookup"><span data-stu-id="5dad8-103">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="5dad8-104">データベース マークアップ言語 (.dbml) のメタデータ ファイルから、Visual Basic または C# のソース コードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="5dad8-104">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="5dad8-105">この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5dad8-105">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="5dad8-106">これは高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="5dad8-106">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="5dad8-107">実行手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5dad8-107">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="5dad8-108">.dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-108">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="5dad8-109">エディターを使用して .dbml ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-109">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="5dad8-110">.dbml ファイルは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の .dbml ファイルのスキーマ定義 (.xsd) ファイルに対して有効である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5dad8-110">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="5dad8-111">詳しくは、「[LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5dad8-111">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="5dad8-112">Visual Basic または C# のソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-112">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="5dad8-113">次の例では、SQLMetal コマンド ライン ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-113">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="5dad8-114">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5dad8-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dad8-115">例</span><span class="sxs-lookup"><span data-stu-id="5dad8-115">Example</span></span>  

 <span data-ttu-id="5dad8-116">次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-116">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="5dad8-117">データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="5dad8-117">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="5dad8-118">例</span><span class="sxs-lookup"><span data-stu-id="5dad8-118">Example</span></span>  

 <span data-ttu-id="5dad8-119">次のコードでは、.dbml ファイルから Visual Basic または C# のソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5dad8-119">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dad8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dad8-120">See also</span></span>

- [<span data-ttu-id="5dad8-121">LINQ to SQL でのコード生成</span><span class="sxs-lookup"><span data-stu-id="5dad8-121">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="5dad8-122">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="5dad8-122">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="5dad8-123">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="5dad8-123">Creating the Object Model</span></span>](creating-the-object-model.md)
