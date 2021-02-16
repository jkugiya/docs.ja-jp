---
description: '詳細情報: 式ツリーのデバッグ (Visual Studio) (Visual Basic)'
title: 式ツリーのデバッグ (Visual Studio)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 0221533a79dbc76be479380bd9b6e6df4156e288
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100459085"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="bcae2-103">式ツリーのデバッグ (Visual Studio) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcae2-103">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="bcae2-104">アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。</span><span class="sxs-lookup"><span data-stu-id="bcae2-104">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="bcae2-105">式ツリーの構造の概要を簡単に取得するには、`DebugView` プロパティ使用できます。このプロパティでは、[特殊な構文を使って](debugview-syntax.md)式ツリーが表されます。</span><span class="sxs-lookup"><span data-stu-id="bcae2-105">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="bcae2-106">(`DebugView` はデバッグ モードでのみ使用できることに注意してください。)</span><span class="sxs-lookup"><span data-stu-id="bcae2-106">(Note that `DebugView` is available only in debug mode.)</span></span>  

![式ツリーの DebugView のスクリーンショット。](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="bcae2-108">`DebugView` は文字列なので、[組み込まれているテキスト ビジュアライザー](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)を使って、複数行で表示できます。**テキスト ビジュアライザー** を使うには、`DebugView` ラベルの隣にある虫眼鏡アイコンから選択します。</span><span class="sxs-lookup"><span data-stu-id="bcae2-108">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![DebugView の結果に適用されるテキスト ビジュアライザーのスクリーンショット。](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="bcae2-110">または、式ツリー用の[カスタム ビジュアライザー](/visualstudio/debugger/create-custom-visualizers-of-data)をインストールして使うこともできます。例:</span><span class="sxs-lookup"><span data-stu-id="bcae2-110">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="bcae2-111">[ReadableExpressions](https://github.com/agileobjects/ReadableExpressions) ([MIT ライセンス](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)、[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) で使用可能): 式ツリーがテーマを設定できる C# コードとしてレンダリングされます。さまざまなレンダリング オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bcae2-111">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Readable Expressions Visualizer のスクリーンショット。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="bcae2-113">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT ライセンス](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) では、式ツリーとその個々のノードのツリー ビューが提供されます。また、Visual Basic の構文を使用して式ツリーをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="bcae2-113">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Expression Tree Visualizer のスクリーンショット。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="bcae2-115">式ツリーのビジュアライザーを開くには</span><span class="sxs-lookup"><span data-stu-id="bcae2-115">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="bcae2-116">**[データヒント]** 、 **[ウォッチ]** ウィンドウ、 **[自動変数]** ウィンドウ、または **[ローカル]** ウィンドウで、式ツリーの横に表示されている虫眼鏡のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcae2-116">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="bcae2-117">使用可能なビジュアライザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcae2-117">A list of available visualizers is displayed.:</span></span>

    ![Visual Studio からビジュアライザーを開くユーザーの操作を示すスクリーンショット。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="bcae2-119">使用するビジュアライザーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcae2-119">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="bcae2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcae2-120">See also</span></span>

- [<span data-ttu-id="bcae2-121">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcae2-121">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="bcae2-122">Visual Studio でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="bcae2-122">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="bcae2-123">カスタム ビジュアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="bcae2-123">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="bcae2-124">`DebugView` 構文</span><span class="sxs-lookup"><span data-stu-id="bcae2-124">`DebugView` syntax</span></span>](debugview-syntax.md)
