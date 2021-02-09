---
description: '詳細情報: 方法:Visual Studio で LINQ to DataSet プロジェクトを作成する'
title: Visual Studio で LINQ to DataSet プロジェクトを作成する
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 4ab626ddaa27780759df95462faac366be8beeff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723830"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="ff7e6-103">方法: Visual Studio で LINQ to DataSet プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="ff7e6-103">How to: Create a LINQ to DataSet project in Visual Studio</span></span>

<span data-ttu-id="ff7e6-104">さまざまな種類の LINQ プロジェクトでは、特定のアセンブリ参照と、インポートされる名前空間 (Visual Basic) または [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブ (C#) が必要です。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-104">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="ff7e6-105">LINQ の場合の最小要件は、*System.Core.dll* への参照と、<xref:System.Linq> に対する `using` ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-105">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="ff7e6-106">Visual Studio 2017 以降のバージョンで新しい C# コンソール アプリ プロジェクトを作成した場合、これらの要件は既定で提供されます。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-106">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017 or a later version.</span></span> <span data-ttu-id="ff7e6-107">以前のバージョンの Visual Studio のプロジェクトをアップグレードする場合、これらの LINQ 関連の参照を手動で追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-107">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="ff7e6-108">LINQ to DataSet では、さらに *System.Data.dll* と *System.Data.DataSetExtensions.dll* に対する 2 つの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-108">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="ff7e6-109">コマンド プロンプトからビルドする場合、 *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5* 内の LINQ 関連 DLL を、手動で参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-109">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="ff7e6-110">LINQ to DataSet 機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ff7e6-110">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="ff7e6-111">既存のプロジェクトで LINQ to DataSet 機能を有効にするには、次の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-111">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="ff7e6-112">**System.Core**、**System.Data**、**System.Data.DataSetExtensions** に対する参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-112">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="ff7e6-113">**ソリューション エクスプローラー** で、 **[参照]** ノードを右クリックし、 **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-113">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="ff7e6-114">**[参照マネージャー]** ダイアログ ボックスで、**System.Core**、**System.Data**、**System.Data.DataSetExtensions** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-114">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="ff7e6-115">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-115">Select **OK**.</span></span>

1. <span data-ttu-id="ff7e6-116">**System.Data** と **System.Linq** に対する [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブ (Visual Basic では [Imports ステートメント](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)) を追加します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-116">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="ff7e6-117">データベースへの接続方法に基づき、必要に応じて、**System.Data.Common** または **System.Data.SqlClient** に対する `using` ディレクティブ (または `Imports` ステートメント) を追加します。</span><span class="sxs-lookup"><span data-stu-id="ff7e6-117">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff7e6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff7e6-118">See also</span></span>

- [<span data-ttu-id="ff7e6-119">LINQ to DataSet の概要</span><span class="sxs-lookup"><span data-stu-id="ff7e6-119">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
