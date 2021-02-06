---
description: 詳細については、「WCF ライブラリプロジェクトの配置」を参照してください。
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1476f564e3e341c77ab9ba4e4281d6f242a735cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646102"
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="a1f58-103">WCF ライブラリ プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="a1f58-103">Deploying a WCF Library Project</span></span>

<span data-ttu-id="a1f58-104">このトピックでは、Windows Communication Foundation (WCF) サービスライブラリプロジェクトを配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1f58-104">This topic describes how you can deploy a Windows Communication Foundation (WCF) Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="a1f58-105">WCF サービス ライブラリの配置</span><span class="sxs-lookup"><span data-stu-id="a1f58-105">Deploying a WCF Service Library</span></span>  

 <span data-ttu-id="a1f58-106">WCF サービスライブラリは、ダイナミックリンクライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="a1f58-106">A WCF service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="a1f58-107">それ自体を単独で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a1f58-107">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="a1f58-108">ホスティング環境に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1f58-108">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="a1f58-109">このプロセスの詳細については、「 [WCF サービスのホストと](/previous-versions/dotnet/articles/bb332338(v=msdn.10))使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1f58-109">For more information about this process, see [Hosting and Consuming WCF Services](/previous-versions/dotnet/articles/bb332338(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="a1f58-110">WCF サービスライブラリは、他の WCF サービスと同様にデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="a1f58-110">A WCF service library can be deployed like any other WCF service.</span></span> <span data-ttu-id="a1f58-111">ただし、.NET Framework は Dll の構成をサポートしていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1f58-111">However, be aware that .NET Framework does not support configuration for DLLs.</span></span> <span data-ttu-id="a1f58-112"><xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a1f58-112"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="a1f58-113">WCF サービスライブラリプロジェクトでは、開発時にライブラリの App.config ファイルを提供することによって、この制限を軽減します。</span><span class="sxs-lookup"><span data-stu-id="a1f58-113">The WCF service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="a1f58-114">ただし、配置後、この App.config ファイルは認識されません。</span><span class="sxs-lookup"><span data-stu-id="a1f58-114">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="a1f58-115">構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1f58-115">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="a1f58-116">自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="a1f58-116">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="a1f58-117">サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1f58-117">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
