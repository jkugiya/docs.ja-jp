---
description: 詳細については、「WCF サービスホストの自動起動の制御」を参照してください。
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f0e9a4e79a403920c0bc6a512b30fb038b2aa1f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677393"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="1cf3b-103">WCF サービス ホストの自動起動の制御</span><span class="sxs-lookup"><span data-stu-id="1cf3b-103">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="1cf3b-104">複数のプロジェクトを含む同じ Visual Studio ソリューションで別のプロジェクトをデバッグするときに、WCF サービスライブラリプロジェクトの Windows Communication Foundation (WCF) サービスホスト (WcfSvcHost.exe) の自動起動機能を制御できます。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-104">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="1cf3b-105">これを行うには、 **ソリューションエクスプローラー** で Wcf サービスプロジェクトを右クリックし、[ **プロパティ**] をクリックして、[ **wcf オプション** ] タブをクリックします。既定では、[ **同じソリューションで別のプロジェクトをデバッグするときに WCF サービスホストを開始する** ] チェックボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-105">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="1cf3b-106">このチェックボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの WCF サービスホストが起動されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-106">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="1cf3b-107">この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-107">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="1cf3b-108">このオプションは、次のプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-108">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="1cf3b-109">WCF サービスライブラリプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="1cf3b-109">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="1cf3b-110">シーケンシャル ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="1cf3b-110">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="1cf3b-111">ステート マシン ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="1cf3b-111">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="1cf3b-112">配信サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="1cf3b-112">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf3b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cf3b-113">See also</span></span>

- [<span data-ttu-id="1cf3b-114">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="1cf3b-114">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
