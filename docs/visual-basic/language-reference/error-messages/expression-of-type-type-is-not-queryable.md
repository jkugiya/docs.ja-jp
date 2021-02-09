---
description: '詳細情報: BC36593:型 <type> の式はクエリ不可能です'
title: 型 <type> の式はクエリ不可能です
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: b2fc6c81ee34c1f8e251ac65ba582fde1c6a7b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796354"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a><span data-ttu-id="5db79-103">BC36593:型 \<type> の式はクエリ不可能です</span><span class="sxs-lookup"><span data-stu-id="5db79-103">BC36593: Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="5db79-104">型 \<type> の式はクエリ不可能です。</span><span class="sxs-lookup"><span data-stu-id="5db79-104">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="5db79-105">LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5db79-105">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>

 <span data-ttu-id="5db79-106">クエリ可能型は、<xref:System.Linq>、<xref:System.Data.Linq>、および <xref:System.Xml.Linq> 名前空間で定義します。</span><span class="sxs-lookup"><span data-stu-id="5db79-106">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="5db79-107">LINQ クエリを実行するには、これらの名前空間の 1 つ以上をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db79-107">You must import one or more of these namespaces to perform LINQ queries.</span></span>

 <span data-ttu-id="5db79-108"><xref:System.Linq> 名前空間により、LINQ を使用してコレクションや配列などのオブジェクトに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5db79-108">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>

 <span data-ttu-id="5db79-109"><xref:System.Data.Linq> 名前空間により、LINQ を使用して ADO.NET データセットと SQL Server データベースに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5db79-109">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>

 <span data-ttu-id="5db79-110"><xref:System.Xml.Linq> 名前空間により、LINQ を使用して XML に対してクエリを実行し、Visual Basic の XML 機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5db79-110">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>

 <span data-ttu-id="5db79-111">**エラー ID:** BC36593</span><span class="sxs-lookup"><span data-stu-id="5db79-111">**Error ID:** BC36593</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5db79-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5db79-112">To correct this error</span></span>

1. <span data-ttu-id="5db79-113"><xref:System.Linq>、<xref:System.Data.Linq>、または <xref:System.Xml.Linq> 名前空間の `Import` ステートメントをコード ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="5db79-113">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="5db79-114">プロジェクト デザイナー (**マイ プロジェクト**) の **[参照]** ページを使用して、プロジェクトの名前空間をインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5db79-114">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>

2. <span data-ttu-id="5db79-115">クエリのソースとして指定した型がクエリ可能型であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5db79-115">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="5db79-116">つまり、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="5db79-116">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5db79-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5db79-117">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="5db79-118">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="5db79-118">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5db79-119">LINQ</span><span class="sxs-lookup"><span data-stu-id="5db79-119">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="5db79-120">XML</span><span class="sxs-lookup"><span data-stu-id="5db79-120">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="5db79-121">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="5db79-121">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="5db79-122">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="5db79-122">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- <span data-ttu-id="5db79-123">[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="5db79-123">[References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
