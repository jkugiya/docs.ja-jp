---
description: '詳細情報: 方法:データ サービス参照を追加する (WCF Data Services)'
title: '方法: データ サービス参照を追加する (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 907ad9a7dc3710a6e565de55c74a0d279d20e159
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765752"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="67bce-103">方法: データ サービス参照を追加する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="67bce-103">How to: Add a data service reference (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="67bce-104">Visual Studio の **[サービス参照の追加]** ダイアログを使用して、WCF Data Services への参照を追加できます。</span><span class="sxs-lookup"><span data-stu-id="67bce-104">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="67bce-105">参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="67bce-105">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="67bce-106">この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="67bce-106">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="67bce-107">詳しくは、「[データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67bce-107">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="67bce-108">データ サービスの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="67bce-108">Add a data service reference</span></span>

1. <span data-ttu-id="67bce-109">(オプション) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。</span><span class="sxs-lookup"><span data-stu-id="67bce-109">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="67bce-110">Visual Studio の **ソリューション エクスプローラー** で、クライアント プロジェクトを右クリックして、 **[追加]**  >  **[サービス参照]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="67bce-110">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="67bce-111">データ サービスが現在のソリューションの一部である場合は、 **[探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67bce-111">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="67bce-112">\- または -</span><span class="sxs-lookup"><span data-stu-id="67bce-112">-or-</span></span>

     <span data-ttu-id="67bce-113">**[アドレス]** ボックスにデータ サービスのベース URL (`http://localhost:1234/Northwind.svc` など) を入力して **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67bce-113">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="67bce-114">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="67bce-114">Select **OK**.</span></span>

     <span data-ttu-id="67bce-115">データ サービス リソースにアクセスして操作できるデータ クラスが含まれる新しいコード ファイルが、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="67bce-115">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="67bce-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="67bce-116">See also</span></span>

- [<span data-ttu-id="67bce-117">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="67bce-117">Quickstart</span></span>](quickstart-wcf-data-services.md)
