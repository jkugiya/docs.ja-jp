---
title: Windows 7 SP1 への .NET Framework のインストール
description: Windows 7 SP1 に .NET Framework をインストールする方法について説明します。
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899088"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a><span data-ttu-id="0cbbf-103">Windows 7 SP1 と Windows Server 2008 R2 に .NET Framework をインストールする</span><span class="sxs-lookup"><span data-stu-id="0cbbf-103">Install the .NET Framework on Windows 7 SP1 and Windows Server 2008 R2</span></span>

<span data-ttu-id="0cbbf-104">.NET Framework は、Windows でさまざまなアプリケーションを実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="0cbbf-105">次の手順を使用してインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-105">You can use the following instructions to install it.</span></span> <span data-ttu-id="0cbbf-106">このページをご覧になっている理由は、アプリケーションを実行しようとして次のようなダイアログがコンピューターに表示されたからではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-106">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![このアプリケーションを開始できませんでした。](./media/this-application-could-not-be-started.png)

<span data-ttu-id="0cbbf-108">これらの手順は、必要な .NET Framework バージョンをインストールする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-108">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="0cbbf-109">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) が最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-109">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest version.</span></span> <span data-ttu-id="0cbbf-110">これは Windows 7 SP1 と Windows Server 2008 R2 でサポートされており、[Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update) に付属します。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-110">It is supported on Windows 7 SP1 and Windows Server 2008 R2 and is included with [Windows 10 May 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update).</span></span>

## <a name="net-framework-48"></a><span data-ttu-id="0cbbf-111">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="0cbbf-111">.NET Framework 4.8</span></span>

> [!div class="button"]
> [<span data-ttu-id="0cbbf-112">.NET Framework 4.8 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="0cbbf-112">Download .NET Framework 4.8</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="0cbbf-113">[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) は、.NET Framework 4.0 以降用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-113">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) can be used to run applications built for .NET Framework 4.0 or later.</span></span>

### <a name="offline-installer"></a><span data-ttu-id="0cbbf-114">オフライン インストーラー</span><span class="sxs-lookup"><span data-stu-id="0cbbf-114">Offline installer</span></span>

<span data-ttu-id="0cbbf-115">Windows 7 で .NET Framework 用のオフライン インストールを実行する場合は、まず最新の [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) がターゲット コンピューターにインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-115">When doing an offline install for .NET Framework on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="0cbbf-116">_certmgr.exe_ ツールを使用すると、証明書のインストールを自動化できます。これは、Visual Studio または Windows SDK から取得されます。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-116">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="0cbbf-117">.NET Framework インストーラーを実行する前に、次のコマンドを使用して証明書をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-117">The following command is used to install the certificate before running the .NET Framework installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a><span data-ttu-id="0cbbf-118">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="0cbbf-118">.NET Framework 3.5</span></span>

<span data-ttu-id="0cbbf-119">[.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) は、Windows 7 に含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-119">The [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) is included with Windows 7.</span></span>

<span data-ttu-id="0cbbf-120">.NET Framework 3.5 は、.NET Framework 1.0 から 3.5 用に構築されたアプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-120">The .NET Framework 3.5 supports apps built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="help"></a><span data-ttu-id="0cbbf-121">Help</span><span class="sxs-lookup"><span data-stu-id="0cbbf-121">Help</span></span>

<span data-ttu-id="0cbbf-122">インストールされている .NET Framework の正しいバージョンがわからない場合は、[Microsoft にお問い合わせください](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。</span><span class="sxs-lookup"><span data-stu-id="0cbbf-122">You can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) if you cannot get the correct version of the .NET Framework installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cbbf-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cbbf-123">See also</span></span>

- [<span data-ttu-id="0cbbf-124">.NET Framework のダウンロード</span><span class="sxs-lookup"><span data-stu-id="0cbbf-124">Download the .NET Framework</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="0cbbf-125">.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0cbbf-125">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="0cbbf-126">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="0cbbf-126">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
