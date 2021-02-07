---
description: 詳細については、「アクティビティクラスを使用したワークフローアクティビティの作成」を参照してください。
title: アクティビティ クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 0d3ffc88bacfd941dfa0c853991bf72045468323
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754941"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="03253-103">アクティビティ クラスを使用したワークフロー アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="03253-103">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="03253-104">で Windows Workflow Foundation (WF) を使用してアクティビティを作成する最も基本的な方法 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] は、 <xref:System.Activities.Activity> 組み込みの [アクティビティライブラリ](net-framework-4-5-built-in-activity-library.md)からカスタムアクティビティまたはアクティビティをアセンブルして機能を作成するから継承するクラスを作成することです。</span><span class="sxs-lookup"><span data-stu-id="03253-104">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="03253-105">ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03253-105">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="03253-106">アクティビティ デザイナーを使ってカスタム アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="03253-106">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="03253-107">Visual Studio 2012 を開きます。</span><span class="sxs-lookup"><span data-stu-id="03253-107">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="03253-108">[ファイル]、[新規作成]、[プロジェクト] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="03253-108">Select File, New, Project.</span></span> <span data-ttu-id="03253-109">[**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="03253-109">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="03253-110">[**テンプレート**] ウィンドウで [**アクティビティライブラリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="03253-110">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="03253-111">新しいプロジェクトに HelloActivity という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="03253-111">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="03253-112">新しいアクティビティを開きます。</span><span class="sxs-lookup"><span data-stu-id="03253-112">Open the new activity.</span></span>  <span data-ttu-id="03253-113"><xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="03253-113">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="03253-114"><xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="03253-114">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="03253-115">`"Hello World"`**テキスト** フィールドに「」 (引用符を含む) と入力します。</span><span class="sxs-lookup"><span data-stu-id="03253-115">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="03253-116">2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="03253-116">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="03253-117">`"Goodbye"`**テキスト** フィールドに「」 (引用符を含む) と入力します。</span><span class="sxs-lookup"><span data-stu-id="03253-117">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
