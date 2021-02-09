---
title: 単体テストの順序を設定する
description: .NET Core で単体テストの順序を設定する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: a7b6b66e4cc865d4ec6b7cfc31ac79767935df2f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506384"
---
# <a name="order-unit-tests"></a><span data-ttu-id="e24f7-103">単体テストの順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-103">Order unit tests</span></span>

<span data-ttu-id="e24f7-104">場合によっては、単体テストを特定の順序で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e24f7-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="e24f7-105">理想的には、単体テストの実行順序が問題になるようなことがあっては "_ならず_"、単体テストの順序を設定しなくて済むようにするのが [ベスト プラクティス](unit-testing-best-practices.md)です。</span><span class="sxs-lookup"><span data-stu-id="e24f7-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="e24f7-106">そうはいっても、それを行うことが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e24f7-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="e24f7-107">この記事では、そのような場合にテストの実行順序を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="e24f7-108">ソース コードを見た方がよい場合は、「[.NET Core の単体テストの順序を設定する](/samples/dotnet/samples/order-unit-tests-cs)」サンプル リポジトリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24f7-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="e24f7-109">この記事で説明する順序設定機能に加え、代わりの方法として、[Visual Studio でカスタム プレイリストを作成する](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists)ことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e24f7-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="e24f7-110">アルファベット順に設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-110">Order alphabetically</span></span>

<span data-ttu-id="e24f7-111">MSTest では、テストはテスト名の順序に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e24f7-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="e24f7-112">番号 `2` の方が `14` より小さくても、`Test14` という名前のテストが `Test2` より前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e24f7-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="e24f7-113">これは、テスト名の順序の設定ではテストのテキスト名が使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="e24f7-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="e24f7-114">xUnit テスト フレームワークでは、テストの実行順序をさらに細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="e24f7-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="e24f7-115">クラスのテスト ケースまたはテスト コレクションの順序を制御するには、`ITestCaseOrderer` インターフェイスと `ITestCollectionOrderer` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="e24f7-116">テスト ケースのアルファベット順に順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-116">Order by test case alphabetically</span></span>

<span data-ttu-id="e24f7-117">メソッド名でテスト ケースの順序を設定するには、`ITestCaseOrderer` を実装し、順序設定のメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="e24f7-118">その後、テスト クラスで、`TestCaseOrdererAttribute` を使用してテスト ケースの順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="e24f7-119">コレクションのアルファベット順に順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-119">Order by collection alphabetically</span></span>

<span data-ttu-id="e24f7-120">表示名でテスト コレクションの順序を設定するには、`ITestCollectionOrderer` を実装し、順序設定のメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="e24f7-121">テスト コレクションは並列に実行される可能性があるため、`CollectionBehaviorAttribute` を使用して、コレクションのテスト並列化を明示的に無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e24f7-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="e24f7-122">その後、`TestCollectionOrdererAttribute` の実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="e24f7-123">カスタム属性で順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-123">Order by custom attribute</span></span>

<span data-ttu-id="e24f7-124">カスタム属性で xUnit テストの順序を設定するには、その前に、利用する属性が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e24f7-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="e24f7-125">次のように `TestPriorityAttribute` を定義します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="e24f7-126">次に、`ITestCaseOrderer` インターフェイスの `PriorityOrderer` の実装を次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e24f7-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="e24f7-127">その後、テスト クラスで、`TestCaseOrdererAttribute` を `PriorityOrderer` にしてテスト ケースの順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="e24f7-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="e24f7-128">優先順位で順序を設定する</span><span class="sxs-lookup"><span data-stu-id="e24f7-128">Order by priority</span></span>

<span data-ttu-id="e24f7-129">テストの順序を明示的に設定できるように、NUnit には [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e24f7-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="e24f7-130">この属性が指定されているテストは、指定されていないテストより前に開始されます。</span><span class="sxs-lookup"><span data-stu-id="e24f7-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="e24f7-131">順序の値を使用して、単体テストを実行する順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="e24f7-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="e24f7-132">次の手順</span><span class="sxs-lookup"><span data-stu-id="e24f7-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e24f7-133">単体テストのコード カバレッジ</span><span class="sxs-lookup"><span data-stu-id="e24f7-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
