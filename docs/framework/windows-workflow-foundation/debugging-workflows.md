---
description: 詳細については、「ワークフローのデバッグ」をご覧ください。
title: デバッグのワークフロー
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 9de65e580d47395a9528f4672014ceb491b09230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742564"
---
# <a name="debugging-workflows"></a><span data-ttu-id="a80a1-103">デバッグのワークフロー</span><span class="sxs-lookup"><span data-stu-id="a80a1-103">Debugging Workflows</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a80a1-104">には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a80a1-104">offers several options for debugging running workflows from the development environment.</span></span> <span data-ttu-id="a80a1-105">ワークフローは、デザイナー、XAML、およびコードでデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="a80a1-105">Workflows can be debugged in the designer, in XAML, and in code.</span></span>

## <a name="debugging-in-the-workflow-designer"></a><span data-ttu-id="a80a1-106">ワークフロー デザイナーでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a80a1-106">Debugging in the Workflow Designer</span></span>

<span data-ttu-id="a80a1-107">ワークフローデザイナーのアクティビティにブレークポイントを設定するには、アクティビティを強調表示し、 <kbd>F9</kbd> キーを押すか、アクティビティのコンテキストメニューを使用します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-107">Breakpoints can be set on activities in the workflow designer by either highlighting the activity and pressing <kbd>F9</kbd> or by using the activity’s context menu.</span></span> <span data-ttu-id="a80a1-108">ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-108">Execution of the workflow then breaks when the workflow host is run in debug mode.</span></span> <span data-ttu-id="a80a1-109">次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-109">In the following screenshot, workflow execution is paused at a breakpoint.</span></span> <span data-ttu-id="a80a1-110">詳細については、「 [ワークフローデザイナーを使用したワークフローのデバッグ](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a80a1-110">For more information, see [Debugging Workflows with the Workflow Designer](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).</span></span>

## <a name="debugging-in-xaml"></a><span data-ttu-id="a80a1-111">XAML でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a80a1-111">Debugging in XAML</span></span>

<span data-ttu-id="a80a1-112">デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="a80a1-112">If a workflow has paused at a breakpoint in the designer, the workflow can also be debugged in XAML.</span></span> <span data-ttu-id="a80a1-113">XAML での実行ポイントを表示するには、ワークフローの実行が一時停止されているときに、ワークフローデザイナーで [ **Xaml ビュー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-113">To view the point of execution in XAML, select **XAML View** in the workflow designer when workflow execution is paused.</span></span> <span data-ttu-id="a80a1-114">デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-114">Debugging can be switched back to the designer by re-opening the workflow in the designer from the solution explorer.</span></span> <span data-ttu-id="a80a1-115">詳細については、「 [方法: ワークフローデザイナーを使用](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)して XAML をデバッグする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a80a1-115">For more information, see [How to: Debug XAML with the Workflow Designer](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).</span></span>

## <a name="debugging-in-code"></a><span data-ttu-id="a80a1-116">コードでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a80a1-116">Debugging in Code</span></span>

<span data-ttu-id="a80a1-117">ブレークポイントを設定するには、コードペインの左余白をクリックするか、カーソルを設定する行にカーソルを合わせて <kbd>F9</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-117">To set a breakpoint, click the left margin of the code pane, or press <kbd>F9</kbd> with the cursor at the line where you want to set it.</span></span>

## <a name="attaching-to-a-workflow-process"></a><span data-ttu-id="a80a1-118">ワークフロー プロセスへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="a80a1-118">Attaching to a Workflow Process</span></span>

<span data-ttu-id="a80a1-119">ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a80a1-119">Workflow debugging also supports using Visual Studio’s infrastructure to attach to a process.</span></span> <span data-ttu-id="a80a1-120">そのため、ワークフロー作成者は、Internet Information Services (IIS) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="a80a1-120">This enables the workflow author to debug a workflow running in a different host environment such as Internet Information Services (IIS) 7.0.</span></span>

## <a name="remote-debugging"></a><span data-ttu-id="a80a1-121">Remote Debugging</span><span class="sxs-lookup"><span data-stu-id="a80a1-121">Remote Debugging</span></span>

<span data-ttu-id="a80a1-122">Windows Workflow Foundation (WF) リモートデバッグは、他の Visual Studio コンポーネントのリモートデバッグと同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="a80a1-122">Windows Workflow Foundation (WF) remote debugging functions the same as remote debugging for other Visual Studio components.</span></span> <span data-ttu-id="a80a1-123">リモートデバッグの使用方法の詳細については、「 [方法: リモートデバッグを有効](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a80a1-123">For information on using remote debugging, see [How to: Enable Remote Debugging](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="a80a1-124">ワークフローアプリケーションが x86 アーキテクチャを対象としていて、64ビットオペレーティングシステムを実行しているコンピューターでホストされている場合、リモートデバッグは、Visual Studio がリモートコンピューターにインストールされていない場合、またはワークフローアプリケーションのターゲットが **ANY CPU** に変更されている場合を除き、機能しません。</span><span class="sxs-lookup"><span data-stu-id="a80a1-124">If the workflow application targets the x86 architecture and is hosted on a computer running a 64 bit operating system, then remote debugging will not work unless Visual Studio is installed on the remote computer or the target for the workflow application is changed to **Any CPU**.</span></span>

## <a name="extending-the-workflow-debugging-service"></a><span data-ttu-id="a80a1-125">ワークフロー デバッグ サービスの拡張</span><span class="sxs-lookup"><span data-stu-id="a80a1-125">Extending the Workflow Debugging Service</span></span>

<span data-ttu-id="a80a1-126">ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="a80a1-126">The workflow debugger service is now public and can be used to create custom applications such as monitoring, simulation, and debugging in a re-hosted designer.</span></span> <span data-ttu-id="a80a1-127">詳細については、「<xref:System.Activities.Presentation.Debug.DebuggerService>」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a80a1-127">For more information, see the <xref:System.Activities.Presentation.Debug.DebuggerService> article.</span></span>
