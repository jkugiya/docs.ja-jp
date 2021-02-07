---
description: 詳細については、「ワークフローソリューションでのサービス参照の追加」を参照してください。
title: ワークフロー ソリューションでのサービス参照の追加
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: ff54235ce2925bd2596bae68333ce98dc7a2f009
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705318"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="88b44-103">ワークフローソリューションでのサービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="88b44-103">Add a Service Reference in a Workflow Solution</span></span>

<span data-ttu-id="88b44-104">ワークフロー アプリケーションでのサービス参照の追加は、通常の WCF アプリケーションとは動作が少し異なります。</span><span class="sxs-lookup"><span data-stu-id="88b44-104">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="88b44-105">[サービス参照の **追加**] を選択し、サービスの URL を指定すると、  >  メタデータがダウンロードされ、カスタムアクティビティが生成されます。これにより、wcf サービスまたは wcf ワークフローサービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="88b44-105">When you select **Add** > **Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call that WCF service or WCF workflow service.</span></span> <span data-ttu-id="88b44-106">サービス参照を追加した後、生成されたアクティビティがビルドされるように、ソリューションを再ビルドします。</span><span class="sxs-lookup"><span data-stu-id="88b44-106">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="88b44-107">これにより、アクティビティがワークフロー デザイナー ツールボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="88b44-107">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="88b44-108">これは、ワークフローソリューション内にサービス参照を追加する場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="88b44-108">This will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="88b44-109">次の web キャストは、他の種類のプロジェクトにサービス参照を追加する方法を示しています。 [Web プロジェクトのワークフローから WCF サービスを呼び出し](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)ます。</span><span class="sxs-lookup"><span data-stu-id="88b44-109">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).</span></span>

<span data-ttu-id="88b44-110">同じ操作名が含まれるサービスへのサービス参照を複数追加すると、問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="88b44-110">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="88b44-111">生成されたアクティビティは最初のサービス操作しか呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="88b44-111">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="88b44-112">この問題を回避するには、サービス操作の名前を変更するか、生成された各アクティビティ内のエンドポイント構成名を変更します。</span><span class="sxs-lookup"><span data-stu-id="88b44-112">To work around this issue, rename the service operations so they are different, or change the endpoint configuration name within each generated activity.</span></span>

## <a name="see-also"></a><span data-ttu-id="88b44-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="88b44-113">See also</span></span>

- [<span data-ttu-id="88b44-114">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="88b44-114">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="88b44-115">Web プロジェクトでのワークフローからの WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="88b44-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
