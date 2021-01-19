---
title: Azure VM に ASP.NET Web アプリを移行する
description: ASP.NET Web アプリケーションをオンプレミスから Azure 仮想マシンに移行する方法について説明します。
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 0bf591ce0bd02537414527c8f3ba22bd41cf51d6
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189214"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="f343d-103">Azure 仮想マシンへの ASP.NET Web アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="f343d-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="f343d-104">このドキュメントでは、ASP.NET Web アプリケーションをオンプレミスから Azure 仮想マシンに移行する方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f343d-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="f343d-105">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="f343d-105">Quickstart</span></span>

<span data-ttu-id="f343d-106">仮想マシンを作成し、この仮想マシンにアプリを発行する方法について説明します。[Azure VM への発行](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="f343d-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="f343d-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="f343d-107">Get Started</span></span>

<span data-ttu-id="f343d-108">次のチュートリアルでは、仮想マシンを作成 (または移行) する手順、Web アプリケーションを発行する手順、Azure でアプリケーションをサポートするために必要なその他のタスクについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="f343d-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="f343d-109">次の方法のいずれかを使用して、Azure に ASP.NET アプリケーション用の仮想マシンを作成します。</span><span class="sxs-lookup"><span data-stu-id="f343d-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="f343d-110">ASP.NET アプリケーション用の新しい仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="f343d-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="f343d-111">オンプレミスの既存の VMWare 仮想マシンを移行する</span><span class="sxs-lookup"><span data-stu-id="f343d-111">Migrate an existing on-premises VMWare virtual machine</span></span>](/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="f343d-112">オンプレミスの既存の Hyper-V 仮想マシンを移行する</span><span class="sxs-lookup"><span data-stu-id="f343d-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="f343d-113">Visual Studio を使用してアプリを発行する</span><span class="sxs-lookup"><span data-stu-id="f343d-113">Publish your app using Visual Studio</span></span>](/azure/virtual-machines/windows/publish-web-app-from-visual-studio)
- [<span data-ttu-id="f343d-114">VM 用のセキュリティで保護された仮想ネットワークを作成する</span><span class="sxs-lookup"><span data-stu-id="f343d-114">Create a secure virtual network for your VMs</span></span>](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="f343d-115">アプリケーションの CI/CD パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="f343d-115">Create a CI/CD pipeline for your application</span></span>](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="f343d-116">高可用性とスケーラビリティを確保するために VM スケール セットに移行する</span><span class="sxs-lookup"><span data-stu-id="f343d-116">Move to a VM scale set for high availability and scalability</span></span>](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="f343d-117">注意事項</span><span class="sxs-lookup"><span data-stu-id="f343d-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="f343d-118">利点</span><span class="sxs-lookup"><span data-stu-id="f343d-118">Benefits</span></span>

<span data-ttu-id="f343d-119">仮想マシンを使用すると、アプリケーションをオンプレミスからクラウドに最も簡単に移行できます。</span><span class="sxs-lookup"><span data-stu-id="f343d-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="f343d-120">仮想マシンを使用することで、アプリケーションがオンプレミスで使用している環境をレプリケートできると同時に、独自のデータ センターを管理する必要性が排除されます。</span><span class="sxs-lookup"><span data-stu-id="f343d-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="f343d-121">Virtual Machine Scale Sets は、Virtual Machines で実行されているアプリケーションの高可用性とスケーラビリティを実現します。</span><span class="sxs-lookup"><span data-stu-id="f343d-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="f343d-122">仮想マシンのサイズ</span><span class="sxs-lookup"><span data-stu-id="f343d-122">Virtual Machine Size</span></span>

<span data-ttu-id="f343d-123">ワークロードに最も最適化された仮想マシンのサイズと種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="f343d-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="f343d-124">詳細については、「[Azure の Windows 仮想マシンのサイズ](/azure/virtual-machines/windows/sizes)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f343d-124">For more information, see [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="f343d-125">メンテナンス </span><span class="sxs-lookup"><span data-stu-id="f343d-125">Maintenance</span></span>

<span data-ttu-id="f343d-126">オンプレミス コンピューターと同様に、仮想マシンの管理と更新はユーザーが行う必要があります<sup>&#42;</sup>。</span><span class="sxs-lookup"><span data-stu-id="f343d-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="f343d-127">[Azure App Service](/azure/app-service/) や[コンテナー](/azure/app-service/containers/)などのサービスとしてのプラットフォーム (PaaS) 環境でアプリケーションを実行できる場合、その必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="f343d-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](/azure/app-service/) or in a [container](/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="f343d-128">*<sup>&#42;</sup>[仮想マシン スケール セットの OS の自動アップグレード](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)は、現在、プレビュー サービスとして提供されています。*</span><span class="sxs-lookup"><span data-stu-id="f343d-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="f343d-129">仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f343d-129">Virtual Networks</span></span>

<span data-ttu-id="f343d-130">Azure Virtual Network を使用すると、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f343d-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="f343d-131">制御可能なハイブリッド インフラストラクチャを構築する</span><span class="sxs-lookup"><span data-stu-id="f343d-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="f343d-132">独自の IP アドレスと DNS サーバーを使用する</span><span class="sxs-lookup"><span data-stu-id="f343d-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="f343d-133">アプリケーション用に安全性の高い分離された環境を作成する</span><span class="sxs-lookup"><span data-stu-id="f343d-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="f343d-134">複数の[接続オプション](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)のいずれかを使用して、VM をオンプレミス ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="f343d-134">Connect your VM to your on-premises network using one of several [connectivity options](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="f343d-135">[ExpressRoute](https://azure.microsoft.com/services/expressroute/) を使用して、仮想マシンをオンプレミス ネットワークに統合する</span><span class="sxs-lookup"><span data-stu-id="f343d-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="f343d-136">作業を開始するには、「[Virtual Network のドキュメント](/azure/virtual-network/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f343d-136">To get started, see the [Virtual Network documentation](/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="f343d-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="f343d-137">Active Directory</span></span>

<span data-ttu-id="f343d-138">多くのアプリケーションでは、認証と ID 管理に Active Directory を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f343d-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="f343d-139">Azure AD Connect を使用すると、オンプレミスのディレクトリを Azure Active Directory と統合できます。</span><span class="sxs-lookup"><span data-stu-id="f343d-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="f343d-140">作業を開始するには、「[オンプレミスのディレクトリと Azure Active Directory の統合](/azure/active-directory/connect/active-directory-aadconnect)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f343d-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="f343d-141">[ExpressRoute](https://azure.microsoft.com/services/expressroute/) を使用すると、アプリケーションはオンプレミスの Active Directory にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f343d-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="f343d-142">SQL データベース</span><span class="sxs-lookup"><span data-stu-id="f343d-142">SQL Databases</span></span>

<span data-ttu-id="f343d-143">アプリケーションがオンプレミス データベースを使用している場合、既定ではアプリはデータベースと対話できません。</span><span class="sxs-lookup"><span data-stu-id="f343d-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="f343d-144">次のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f343d-144">You can either:</span></span>

- <span data-ttu-id="f343d-145">アプリケーションがオンプレミスで実行されているデータベースにアクセスできるようにするためのハイブリッド ネットワークを構成する。</span><span class="sxs-lookup"><span data-stu-id="f343d-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="f343d-146">データベースを Azure に移行する。</span><span class="sxs-lookup"><span data-stu-id="f343d-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="f343d-147">詳細については、[Azure への SQL Server データベースの移行](sql.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f343d-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="f343d-148">高可用性とスケーラビリティ</span><span class="sxs-lookup"><span data-stu-id="f343d-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="f343d-149">Virtual Machine Scale Sets</span><span class="sxs-lookup"><span data-stu-id="f343d-149">Virtual Machine Scale Sets</span></span>

<span data-ttu-id="f343d-150">アプリケーションの高可用性とスケーラビリティを確保する場合、VM イメージを Azure 仮想マシン スケール セットに移行すると、アプリケーションの可用性とスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="f343d-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="f343d-151">VM Scale Sets では、構成済みの既存の VM を使用したり、アプリケーションでイメージをビルドするためのビルド パイプラインを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="f343d-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="f343d-152">作業を開始するには、「[仮想マシン スケール セットへのアプリケーションのデプロイ](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f343d-152">To get started, see [Deploy your application on virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="f343d-153">ログの一元化</span><span class="sxs-lookup"><span data-stu-id="f343d-153">Centralized Logging</span></span>

<span data-ttu-id="f343d-154">複数のインスタンスでアプリケーションを実行する場合は、[Azure Storage](/azure/storage/) などの一元化された場所にログを保存することを検討します。</span><span class="sxs-lookup"><span data-stu-id="f343d-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f343d-155">次の手順</span><span class="sxs-lookup"><span data-stu-id="f343d-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f343d-156">Azure への SQL Server データベースの移行</span><span class="sxs-lookup"><span data-stu-id="f343d-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
