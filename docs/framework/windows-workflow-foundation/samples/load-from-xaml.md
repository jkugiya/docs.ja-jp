---
description: 詳細については、「XAML からの読み込み」を参照してください。
title: XAML からの読み込み
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: fd0eca487c0245c7bfa46ca80c06f2adfa577353
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742031"
---
# <a name="load-from-xaml"></a><span data-ttu-id="63c44-103">XAML からの読み込み</span><span class="sxs-lookup"><span data-stu-id="63c44-103">Load From XAML</span></span>

<span data-ttu-id="63c44-104">このサンプルでは、XamlBuildTask ツールを実行することなく、XAML ワークフローを動的に読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="63c44-104">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="63c44-105">代わりに、このサンプルでは <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63c44-105">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="63c44-106">このサンプルは、クラスを使用して XAML ワークフローを読み込み、それを実行する Windows Presentation Foundation (WPF) クライアントアプリケーションです <xref:System.Activities.XamlIntegration.ActivityXamlServices> 。</span><span class="sxs-lookup"><span data-stu-id="63c44-106">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="63c44-107"><xref:System.Activities.XamlIntegration.ActivityXamlServices> クラスを使用して XAML ワークフローが読み込まれると、実行可能な <xref:System.Activities.DynamicActivity%601> が返されます。</span><span class="sxs-lookup"><span data-stu-id="63c44-107">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="63c44-108">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="63c44-108">To use this sample</span></span>

1. <span data-ttu-id="63c44-109">Visual Studio 2010 を使用して、LoadFromXAML ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="63c44-109">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="63c44-110">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="63c44-110">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="63c44-111">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="63c44-111">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63c44-112">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="63c44-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="63c44-113">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="63c44-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="63c44-114">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="63c44-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63c44-115">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="63c44-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
