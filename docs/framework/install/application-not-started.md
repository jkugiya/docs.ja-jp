---
title: "\"このアプリケーションを開始できませんでした\" のトラブルシューティング"
description: "\"このアプリケーションを開始できませんでした\" のダイアログ ボックスが表示された場合の対処方法を説明します。"
ms.date: 09/05/2019
ms.openlocfilehash: 92055bf40500eba4f7c892d11af12d8e675ddd5d
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605244"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="d3aea-103">"このアプリケーションを開始できませんでした" のエラー メッセージのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d3aea-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="d3aea-104">.NET Framework 用に開発されたアプリケーションでは、通常、システムに特定のバージョンの .NET Framework がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3aea-104">Applications that are developed for .NET Framework typically require that a specific version of .NET Framework be installed on your system.</span></span> <span data-ttu-id="d3aea-105">場合によっては、インストールしたバージョンまたは必要なバージョンの .NET Framework が存在しない状態でアプリケーションを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="d3aea-105">In some cases, you may attempt to run an application without either an installed version or the expected version of .NET Framework present.</span></span> <span data-ttu-id="d3aea-106">その結果、次のようなエラー ダイアログ ボックスが生成されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="d3aea-106">This often produces an error dialog box like the following:</span></span>

![このアプリケーションを開始できませんでした。](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="d3aea-108">通常、このエラーは次のいずれかの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-108">This error typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="d3aea-109">システムにインストールされている .NET Framework が破損しています。</span><span class="sxs-lookup"><span data-stu-id="d3aea-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="d3aea-110">アプリケーションに必要な .NET Framework のバージョンを検出できません。</span><span class="sxs-lookup"><span data-stu-id="d3aea-110">The version of .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="d3aea-111">この問題を解決し、アプリケーションを実行できるようにするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="d3aea-112">[.NET Framework 修復ツール (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d3aea-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="d3aea-113">ダウンロードが完了すると、ツールが自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="d3aea-114">.NET Framework 修復ツールで、次の図に示すような追加のアクションが推奨される場合は、**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![修復ツールの推奨される変更](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="d3aea-116">次の図に示すように、変更が完了したことを示すダイアログ ボックスが .NET Framework 修復ツールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="d3aea-117">アプリケーションを再実行するときは、このダイアログ ボックスを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="d3aea-118">.NET Framework 修復ツールによって破損した .NET Framework インストールが特定され、修正された場合は成功です。</span><span class="sxs-lookup"><span data-stu-id="d3aea-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![修復ツールの変更の完了](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="d3aea-120">アプリケーションが正常に実行された場合は、**[完了]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="d3aea-121">それ以外の場合は、**[次へ]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="d3aea-122">**[次へ]** ボタンを選択した場合、.NET Framework 修復ツールでは次のようなダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="d3aea-123">**[完了]** ボタンを選択して、診断情報を Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![問題を解決できない](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="d3aea-125">それでもアプリケーションを実行できない場合は、次の表に示すように、使用しているバージョンの Windows でサポートされている .NET Framework の最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d3aea-125">If you still cannot run the application, install the latest version of .NET Framework that's supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="d3aea-126">Windows のバージョン</span><span class="sxs-lookup"><span data-stu-id="d3aea-126">Windows version</span></span>|<span data-ttu-id="d3aea-127">.NET framework のインストール</span><span class="sxs-lookup"><span data-stu-id="d3aea-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="d3aea-128">Windows 10 Anniversary Update 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d3aea-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="d3aea-129">.NET Framework 4.8 ランタイム</span><span class="sxs-lookup"><span data-stu-id="d3aea-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d3aea-130">Windows 10、Windows 10 November Update</span><span class="sxs-lookup"><span data-stu-id="d3aea-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="d3aea-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="d3aea-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="d3aea-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d3aea-132">Windows 8.1</span></span>|[<span data-ttu-id="d3aea-133">.NET Framework 4.8 ランタイム</span><span class="sxs-lookup"><span data-stu-id="d3aea-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d3aea-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d3aea-134">Windows 8</span></span>|[<span data-ttu-id="d3aea-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="d3aea-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="d3aea-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d3aea-136">Windows 7 SP1</span></span>|[<span data-ttu-id="d3aea-137">.NET Framework 4.8 ランタイム</span><span class="sxs-lookup"><span data-stu-id="d3aea-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="d3aea-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="d3aea-138">Windows Vista SP2</span></span>|[<span data-ttu-id="d3aea-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="d3aea-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="d3aea-140">.NET Framework 4.8 は、Windows 10 May 2019 Update にプレインストールされています。</span><span class="sxs-lookup"><span data-stu-id="d3aea-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="d3aea-141">アプリケーションを起動してみます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="d3aea-142">場合によっては、次のようなダイアログ ボックスが表示され、.NET Framework 3.5 をインストールするように求められます。</span><span class="sxs-lookup"><span data-stu-id="d3aea-142">In some cases, you may see a dialog box like the following, which asks you to install .NET Framework 3.5.</span></span> <span data-ttu-id="d3aea-143">**[この機能をダウンロードしてインストールする]** を選択して .NET Framework 3.5 をインストールし、アプリケーションをもう一度起動します。</span><span class="sxs-lookup"><span data-stu-id="d3aea-143">Select **Download and install this feature** to install .NET Framework 3.5, then launch the application again.</span></span>

   ![.NET Framework 3.5 をインストールすることを提案している [Windows の機能] ダイアログ ボックス](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="d3aea-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3aea-145">See also</span></span>

- [<span data-ttu-id="d3aea-146">.NET Framework のシステム要件</span><span class="sxs-lookup"><span data-stu-id="d3aea-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="d3aea-147">.NET framework のインストール ガイド</span><span class="sxs-lookup"><span data-stu-id="d3aea-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="d3aea-148">.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d3aea-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
