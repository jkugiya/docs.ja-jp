---
description: 詳細については、「ワークフローデザインエクスペリエンスのカスタマイズ」を参照してください。
title: ワークフロー デザイン操作のカスタマイズ
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 02049f8b42de3de6e4dfdfe8a4151be1500bcca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742655"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="1f67a-103">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="1f67a-103">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="1f67a-104">カスタムアクティビティを設計し、Windows ワークフローデザイナーを再ホストするシナリオは、.NET Framework 4 で大幅に簡素化されています。</span><span class="sxs-lookup"><span data-stu-id="1f67a-104">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="1f67a-105">開発も配置も簡単になり、柔軟性も向上しました。</span><span class="sxs-lookup"><span data-stu-id="1f67a-105">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="1f67a-106">主要なインフラストラクチャの変更は、新しいアクティビティデザイナーのプログラミングモデルが Windows Presentation Foundation (WPF) に基づいて構築されることです。</span><span class="sxs-lookup"><span data-stu-id="1f67a-106">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="1f67a-107">これにより、アクティビティデザイナーを宣言によって定義し、他のアプリケーションのワークフローデザイナーを比較しやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="1f67a-107">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="1f67a-108">再ホストするときに、カスタム式エディターを開発して、IntelliSense や簡略化された式ドメインをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="1f67a-108">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="1f67a-109">ワークフローサービスを使用すると、Windows Communication Foundation (WCF) との統合がシームレスになりました。</span><span class="sxs-lookup"><span data-stu-id="1f67a-109">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="1f67a-110">カスタム アクティビティ デザイナーおよびモデル アイテム ツリーを使用して、再ホストされたワークフロー デザイナーのデザイン時の操作を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="1f67a-110">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1f67a-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1f67a-111">In This Section</span></span>

 [<span data-ttu-id="1f67a-112">カスタム アクティビティ デザイナーおよびテンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="1f67a-112">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="1f67a-113">新しいカスタム アクティビティ デザイナーおよびテンプレートを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f67a-113">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="1f67a-114">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="1f67a-114">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="1f67a-115">Visual Studio の外部で Windows ワークフローデザイナーを再ホストする方法と、検証エラーを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f67a-115">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="1f67a-116">カスタム式エディターの使用</span><span class="sxs-lookup"><span data-stu-id="1f67a-116">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="1f67a-117">Visual Studio 2010 の外部で再ホストされたワークフローデザイナーで使用するカスタム式エディターを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f67a-117">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="1f67a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f67a-118">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="1f67a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f67a-119">See also</span></span>

- [<span data-ttu-id="1f67a-120">Windows Workflow Foundation の拡張</span><span class="sxs-lookup"><span data-stu-id="1f67a-120">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="1f67a-121">Designer</span><span class="sxs-lookup"><span data-stu-id="1f67a-121">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="1f67a-122">カスタム アクティビティ デザイナー</span><span class="sxs-lookup"><span data-stu-id="1f67a-122">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="1f67a-123">デザイナーのホスト</span><span class="sxs-lookup"><span data-stu-id="1f67a-123">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
