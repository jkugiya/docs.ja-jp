---
title: .NET アップグレード アシスタントの概要
description: .NET Framework からの移行と .NET 5 へのプロジェクトのアップグレードに役立つ .NET アップグレード アシスタント ツールについて紹介します。
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: bd1c904586d170d93b76ae058914adb334289f89
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108219"
---
# <a name="overview-of-the-net-upgrade-assistant"></a><span data-ttu-id="a224c-103">.NET アップグレード アシスタントの概要</span><span class="sxs-lookup"><span data-stu-id="a224c-103">Overview of the .NET Upgrade Assistant</span></span>

<span data-ttu-id="a224c-104">お客様は、現在 .NET Framework 上で実行されているアプリを .NET 5 に移植することに関心があるとします。</span><span class="sxs-lookup"><span data-stu-id="a224c-104">You might have apps that currently run on the .NET Framework that you're interested in porting to .NET 5.</span></span> <span data-ttu-id="a224c-105">.NET アップグレード アシスタント ツールを使用すれば、このプロセスを容易に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a224c-105">The .NET Upgrade Assistant tool can assist with this process.</span></span> <span data-ttu-id="a224c-106">この記事では、次について説明します。</span><span class="sxs-lookup"><span data-stu-id="a224c-106">This article provides:</span></span>

* <span data-ttu-id="a224c-107">.NET アップグレード アシスタントの概要。</span><span class="sxs-lookup"><span data-stu-id="a224c-107">An overview of the .NET Upgrade Assistant.</span></span>
* <span data-ttu-id="a224c-108">.NET アップグレード アシスタントをインストールする方法。</span><span class="sxs-lookup"><span data-stu-id="a224c-108">How to install the .NET Upgrade Assistant.</span></span>

## <a name="what-is-the-net-upgrade-assistant"></a><span data-ttu-id="a224c-109">.NET アップグレード アシスタントとは</span><span class="sxs-lookup"><span data-stu-id="a224c-109">What is the .NET Upgrade Assistant</span></span>

<span data-ttu-id="a224c-110">.NET アップグレード アシスタントは、さまざまな種類の .NET Framework アプリに対して実行できるコマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="a224c-110">The .NET Upgrade Assistant is a command-line tool that can be run on different kinds of .NET Framework apps.</span></span> <span data-ttu-id="a224c-111">これは、.NET Framework アプリの .NET 5 へのアップグレードを支援するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a224c-111">It's designed to assist with upgrading .NET Framework apps to .NET 5.</span></span> <span data-ttu-id="a224c-112">このツールを実行した後、**ほとんどの場合、アプリでは移行を完遂するためにより多くの作業が必要になります**。</span><span class="sxs-lookup"><span data-stu-id="a224c-112">After running the tool, **in most cases the app will require more effort to complete the migration**.</span></span> <span data-ttu-id="a224c-113">このツールには、移行を完遂するのを支援するアナライザーのインストールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a224c-113">The tool includes the installation of analyzers that can assist with completing the migration.</span></span>

<span data-ttu-id="a224c-114">現在、このツールでは次の種類の .NET Framework アプリがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a224c-114">Currently the tool supports the following .NET Framework app types:</span></span>

- <span data-ttu-id="a224c-115">.NET Framework Windows フォーム アプリ</span><span class="sxs-lookup"><span data-stu-id="a224c-115">.NET Framework Windows Forms apps</span></span>
- <span data-ttu-id="a224c-116">.NET Framework WPF アプリ</span><span class="sxs-lookup"><span data-stu-id="a224c-116">.NET Framework WPF apps</span></span>
- <span data-ttu-id="a224c-117">.NET Framework ASP.NET MVC アプリ</span><span class="sxs-lookup"><span data-stu-id="a224c-117">.NET Framework ASP.NET MVC apps</span></span>
- <span data-ttu-id="a224c-118">.NET Framework コンソール アプリ</span><span class="sxs-lookup"><span data-stu-id="a224c-118">.NET Framework console apps</span></span>
- <span data-ttu-id="a224c-119">.NET Framework クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a224c-119">.NET Framework class libraries</span></span>

<span data-ttu-id="a224c-120">.NET アップグレード アシスタントは現在プレリリースされていて、頻繁に更新されています。</span><span class="sxs-lookup"><span data-stu-id="a224c-120">The .NET Upgrade Assistant is currently prerelease and is receiving frequent updates.</span></span> <span data-ttu-id="a224c-121">このツールの使用時に問題が見つかった場合は、このツールの [GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant)でそれらをご報告ください。</span><span class="sxs-lookup"><span data-stu-id="a224c-121">If you discover problems using the tool, please report them in the tool's [GitHub repository](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="how-to-install-the-net-upgrade-assistant"></a><span data-ttu-id="a224c-122">.NET アップグレード アシスタントをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="a224c-122">How to install the .NET Upgrade Assistant</span></span>

<span data-ttu-id="a224c-123">.NET アップグレード アシスタントをインストールして使用する方法については、[入門チュートリアル](https://aka.ms/dotnet-upgrade-assistant-install)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a224c-123">The [Get Started tutorial](https://aka.ms/dotnet-upgrade-assistant-install) walks through how to install and use the .NET Upgrade Assistant.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a224c-124">前提条件</span><span class="sxs-lookup"><span data-stu-id="a224c-124">Prerequisites</span></span>

1. <span data-ttu-id="a224c-125">このツールでは、プロジェクト ファイルの操作に MSBuild が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a224c-125">This tool uses MSBuild to work with project files.</span></span> <span data-ttu-id="a224c-126">最新バージョンの MSBuild がインストールされていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a224c-126">Make sure that a recent version of MSBuild is installed.</span></span> <span data-ttu-id="a224c-127">[Visual Studio 2019 をインストール](https://visualstudio.microsoft.com/downloads/)すれば、それを簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a224c-127">An easy way to do this is to [install Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span></span>
1. <span data-ttu-id="a224c-128">このツールは [try-convert](https://github.com/dotnet/try-convert) に依存しています。</span><span class="sxs-lookup"><span data-stu-id="a224c-128">This tool depends on [try-convert](https://github.com/dotnet/try-convert).</span></span> <span data-ttu-id="a224c-129">このツールを正しく動作させるには、プロジェクト ファイルを新しい SDK スタイルに変換するための try-convert ツールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a224c-129">In order for the tool to run correctly, you must install the try-convert tool for converting project files to the new SDK style.</span></span> <span data-ttu-id="a224c-130">**try-convert** が既にインストールされている場合は、代わりにそれを更新することが必要になることがあります (**upgrade-assistant** がバージョン _0.7.212201_ 以降に依存しているためです)</span><span class="sxs-lookup"><span data-stu-id="a224c-130">If you already have **try-convert** installed, you may need to update it instead (since **upgrade-assistant** depends on version _0.7.212201_ or later)</span></span>
    1. <span data-ttu-id="a224c-131">try-convert をインストールするには: `dotnet tool install -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="a224c-131">To install try-convert: `dotnet tool install -g try-convert`</span></span>
    1. <span data-ttu-id="a224c-132">try-convert を更新するには: `dotnet tool update -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="a224c-132">To update try-convert: `dotnet tool update -g try-convert`</span></span>

### <a name="installation-steps"></a><span data-ttu-id="a224c-133">インストール手順</span><span class="sxs-lookup"><span data-stu-id="a224c-133">Installation steps</span></span>

<span data-ttu-id="a224c-134">このツールは、次を実行することで .NET CLI ツールとしてインストールできます: `dotnet tool install -g upgrade-assistant --add-source https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span><span class="sxs-lookup"><span data-stu-id="a224c-134">The tool can be installed as a .NET CLI tool by running: `dotnet tool install -g upgrade-assistant --add-source https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span></span>

<span data-ttu-id="a224c-135">同様に、.NET アップグレード アシスタントは .NET CLI ツールとしてインストールされるため、次を実行することで簡単に更新できます: `https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span><span class="sxs-lookup"><span data-stu-id="a224c-135">Similarly, because the .NET Upgrade Assistant is installed as a .NET CLI tool, it can be easily updated by running: `https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span></span>

<span data-ttu-id="a224c-136">インストールの手順の詳細については、プロジェクトの [README](https://github.com/dotnet/upgrade-assistant) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a224c-136">For detailed installation instructions, please refer to the project's [README](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="see-also"></a><span data-ttu-id="a224c-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a224c-137">See also</span></span>

- [<span data-ttu-id="a224c-138">.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="a224c-138">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="a224c-139">.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="a224c-139">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="a224c-140">.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="a224c-140">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="a224c-141">.NET アップグレード アシスタントの GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="a224c-141">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
