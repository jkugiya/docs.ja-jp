---
description: '詳細情報: 方法: コンピューターについての情報の取得 (Visual Basic)'
title: コンピューターについての情報の取得
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Info object [Visual Basic], tasks
ms.assetid: 13c145bc-5c85-4fea-a5dd-2ca8681a0252
ms.openlocfilehash: 11198082950fcfd648b5ba8fa859b8765e3f628c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797771"
---
# <a name="getting-information-about-the-computer-visual-basic"></a><span data-ttu-id="2d3a0-103">方法: コンピューターについての情報の取得 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d3a0-103">Getting Information about the Computer (Visual Basic)</span></span>

<span data-ttu-id="2d3a0-104">`My.Computer.Info` オブジェクトは、コンピューターのメモリ、読み込まれたアセンブリ名、オペレーティング システムに関する情報を取得するためのプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-104">The `My.Computer.Info` object provides properties for getting information about the computer's memory, loaded assemblies, name, and operating system.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d3a0-105">解説</span><span class="sxs-lookup"><span data-stu-id="2d3a0-105">Remarks</span></span>

<span data-ttu-id="2d3a0-106">この表は `My.Computer.Info` オブジェクトでよく処理されるタスクを一覧にしたものであり、各タスクの実行方法を実演するトピックにここからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-106">This table lists tasks commonly accomplished through the `My.Computer.Info` object and points to topics demonstrating how to perform each.</span></span>

|<span data-ttu-id="2d3a0-107">終了</span><span class="sxs-lookup"><span data-stu-id="2d3a0-107">To</span></span>|<span data-ttu-id="2d3a0-108">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="2d3a0-108">See</span></span>|
|---|---|
|<span data-ttu-id="2d3a0-109">アプリケーションがインストールされているコンピューターで使用できる仮想アドレス領域の量を確認する</span><span class="sxs-lookup"><span data-stu-id="2d3a0-109">Determine how much virtual address space is available for the computer on which the application is installed</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.TotalVirtualMemory%2A>|
|<span data-ttu-id="2d3a0-110">アプリケーションを実行しているコンピューターのプラットフォームの種類を確認する</span><span class="sxs-lookup"><span data-stu-id="2d3a0-110">Determine the platform type of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSPlatform%2A>|
|<span data-ttu-id="2d3a0-111">アプリケーションを実行しているコンピューターのオペレーティング システムの種類を確認する</span><span class="sxs-lookup"><span data-stu-id="2d3a0-111">Determine the operating system of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName%2A>|
|<span data-ttu-id="2d3a0-112">アプリケーションを実行しているコンピューターにインストールされているサービス パックを確認する</span><span class="sxs-lookup"><span data-stu-id="2d3a0-112">Determine what service packs have been installed on the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSVersion%2A>|
|<span data-ttu-id="2d3a0-113">アプリケーションを実行しているコンピューターにインストールされている `UICulture` を確認する</span><span class="sxs-lookup"><span data-stu-id="2d3a0-113">Determine the installed `UICulture` on the computer on which the application is running.</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.InstalledUICulture%2A>|

## <a name="see-also"></a><span data-ttu-id="2d3a0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d3a0-114">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
