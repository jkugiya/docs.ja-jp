---
title: '方法: Net.TCP ポート共有サービスを有効にする'
description: 既定では無効になっている Net.TCP を有効にするために、MMC を使用して Net TCP ポート共有サービスを構成する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 7200d82e4a45ce9e36b2a4cec3d0c08e1a5f00ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265467"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="a96e8-103">方法: Net.TCP ポート共有サービスを有効にする</span><span class="sxs-lookup"><span data-stu-id="a96e8-103">How to: Enable the Net.TCP Port Sharing Service</span></span>

<span data-ttu-id="a96e8-104">Windows Communication Foundation (WCF) では Net.TCP ポート共有サービスと呼ばれる Windows サービスを使用し、複数のプロセス間での TCP ポート共有を実現します。</span><span class="sxs-lookup"><span data-stu-id="a96e8-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="a96e8-105">このサービスは WCF の一部としてインストールされますが、セキュリティ予防措置として既定では有効になっていません。したがって、初めて使用する前に手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a96e8-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="a96e8-106">このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a96e8-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="a96e8-107">Net.TCP ポート共有サービスを有効にして手動で開始したら、「[方法: ポート共有を使用するように WCF サービスを構成する](how-to-configure-a-wcf-service-to-use-port-sharing.md)」を参照して、このサービスを使用できるようにユーザーのサービスを構成する方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="a96e8-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="a96e8-108">net.tcp://ポート共有を使用するサンプルについては、「[Net.TCP ポート共有のサンプル](../samples/net-tcp-port-sharing-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a96e8-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="a96e8-109">MMC を使用して Net.TCP ポート共有サービスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="a96e8-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="a96e8-110">[スタート] メニューから、コマンド プロンプト ウィンドウを開いて「`services.msc`」と入力するか、[ファイル名を指定して実行] を開いて [名前] ボックスに「`services.msc`」と入力し、サービス管理コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="a96e8-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="a96e8-111">サービス リストの **[名前]** 列の **[Net.Tcp ポート共有サービス]** を右クリックして、メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a96e8-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="a96e8-112">サービスの手動起動を有効にするには、 **[プロパティ]** ウィンドウの **[全般]** タブをクリックし、 **[スタートアップの種類]** ボックスの [手動] を選択して、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a96e8-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="a96e8-113">サービスを開始するには、サービス状態領域の **[開始]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a96e8-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="a96e8-114">これで、サービスの状態には "開始" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a96e8-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="a96e8-115">**[OK]** をクリックしてサービス リストに戻り、MMC コンソールを終了します。</span><span class="sxs-lookup"><span data-stu-id="a96e8-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a96e8-116">例</span><span class="sxs-lookup"><span data-stu-id="a96e8-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96e8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a96e8-117">See also</span></span>

- [<span data-ttu-id="a96e8-118">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="a96e8-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="a96e8-119">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="a96e8-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
