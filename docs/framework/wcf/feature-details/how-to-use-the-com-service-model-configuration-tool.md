---
description: '詳細については、「方法: COM + サービスモデル構成ツールを使用する」を参照してください。'
title: '方法: COM+ サービス モデル構成ツールを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2047604f327cd871629bbdac403e9acd816bbdb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734088"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="22c4b-103">方法: COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="22c4b-103">How to: Use the COM+ Service Model Configuration Tool</span></span>

<span data-ttu-id="22c4b-104">適切なホスト モードを選択したら、COM+ サービス モデル構成コマンド ライン ツール (ComSvcConfig.exe) を使用して、Web サービスとして公開されるアプリケーション インターフェイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-104">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="22c4b-105">以下の各タスクを実行するには、コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="22c4b-105">You must be an administrator on the machine to perform any of the following tasks.</span></span>

 <span data-ttu-id="22c4b-106">Windows 7 コンピューターで ComSvcConfig.exe を使用して、最新のサービス モデル バージョン (現在 v4.5) を使用するように Web サービスを構成する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-106">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>

1. <span data-ttu-id="22c4b-107">レジストリキーを  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` DWORD 値0x00000001 に設定します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-107">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>

2. <span data-ttu-id="22c4b-108">comsvcconfig.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-108">Run comsvcconfig.exe</span></span>

3. <span data-ttu-id="22c4b-109">手順 1. で追加したレジストリ キーを元の値に戻すか、存在しない場合は削除します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-109">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22c4b-110">このレジストリ キーを元に戻すことは重要です。</span><span class="sxs-lookup"><span data-stu-id="22c4b-110">Reverting this registry key is important.</span></span> <span data-ttu-id="22c4b-111">これは互換性のキーです。</span><span class="sxs-lookup"><span data-stu-id="22c4b-111">This is a compatibility key.</span></span> <span data-ttu-id="22c4b-112">この変更を元に戻さないと、コンピューターで実行している他の .NET アプリケーションで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22c4b-112">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>

> [!WARNING]
> <span data-ttu-id="22c4b-113">Windows 8 コンピューターで ComSvcConfig.exe/install を使用すると、"PC 上のアプリには次の Windows 機能が必要です。 .NET Framework 3.5 がインストールされていない場合は、.NET Framework 3.5 (.NET 2.0 と .NET 3.0 を含む)" というダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22c4b-113">When using ComSvcConfig.exe  /install on a Windows 8 machine, a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="22c4b-114">このダイアログは無視してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="22c4b-114">This dialog may be ignored.</span></span> <span data-ttu-id="22c4b-115">また、OnlyUseLatestCLR レジストリ キーを DWORD 値 0x00000001 に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="22c4b-115">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>

## <a name="add-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="22c4b-116">COM + ホストモードを使用してインターフェイスを追加する</span><span class="sxs-lookup"><span data-stu-id="22c4b-116">Add an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="22c4b-117">次の例に示すように、`/install` オプションと `/hosting:complus` オプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-117">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     <span data-ttu-id="22c4b-118">このコマンドは、Web サービスとして公開されるインターフェイスのセットに (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.IFinancial` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-118">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="22c4b-119">サービスは COM+ ホスト モードを使用するため、アプリケーションを明示的にアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22c4b-119">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>

     <span data-ttu-id="22c4b-120">コンポーネントとインターフェイスにはワイルドカードアスタリスク ( \* ) 文字を使用できますが、選択した機能のみを Web サービスとして公開することが必要になる場合があるため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="22c4b-120">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="22c4b-121">ワイルドカードを使用すると、このコンポーネントの将来のバージョンを使用して実行したときに、構成構文の決定時には存在しなかったインターフェイスが誤って公開される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22c4b-121">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>

     <span data-ttu-id="22c4b-122">/verbose オプションを指定すると、ツールは、エラーだけでなく警告も表示します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-122">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>

     <span data-ttu-id="22c4b-123">公開されたサービスのコントラクトには、`IFinances` インターフェイスのすべてのメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="22c4b-123">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="22c4b-124">COM + ホストモードを使用してインターフェイスから特定のメソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="22c4b-124">Add specific methods from an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="22c4b-125">次の例に示すように、`/install` オプションと `/hosting:complus` オプション、および必要なメソッドの名前を明示的に指定して、ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-125">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     <span data-ttu-id="22c4b-126">このコマンドは、公開されたサービス コントラクトに `Credit` インターフェイスの `Debit` メソッドと `IFinances` メソッドだけを操作として追加します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-126">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="22c4b-127">インターフェイスのその他のメソッドはすべてコントラクトから除外されるため、Web サービス クライアントから呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="22c4b-127">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>

## <a name="add-an-interface-using-the-web-hosting-mode"></a><span data-ttu-id="22c4b-128">Web ホスティングモードを使用してインターフェイスを追加する</span><span class="sxs-lookup"><span data-stu-id="22c4b-128">Add an interface using the Web hosting mode</span></span>

- <span data-ttu-id="22c4b-129">次の例に示すように、`/install` オプションと `/hosting:was` オプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-129">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     <span data-ttu-id="22c4b-130">このコマンドは、Web サービスとして公開されるインターフェイスのセットに (OnlineWarehouse COM+ アプリケーションの) `IStockLevels` コンポーネントの `ItemInventory.Warehouse` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-130">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="22c4b-131">サービスは、COM+ 内ではなく、IIS の OnlineWarehouse 仮想ディレクトリ内で Web ホストされるため、アプリケーションは、必要に応じて自動的にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="22c4b-131">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>

     <span data-ttu-id="22c4b-132">Web ホスト (インプロセス) 構成を使用するには、コンポーネント サービス管理コンソールを使用して、サーバー アプリケーションではなくライブラリ アプリケーションとして実行されるように COM+ アプリケーションを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22c4b-132">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="22c4b-133">サーバー アプリケーションとして構成されたアプリケーションは、標準の Web ホスト モードを使用するため、各要求の処理でプロセス ホップが発生します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-133">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>

     <span data-ttu-id="22c4b-134">`/mex` オプションは、サービスからコントラクト定義を取得するクライアントをサポートするために、アプリケーションのサービス エンドポイントと同じトランスポートを使用する追加の Metadata Exchange (MEX) サービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-134">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>

## <a name="remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="22c4b-135">指定されたインターフェイスの Web サービスを削除します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-135">Remove a Web service for a specified interface</span></span>

- <span data-ttu-id="22c4b-136">次の例に示すように、`/uninstall` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-136">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     <span data-ttu-id="22c4b-137">このコマンドは、(OnlineStore COM+ アプリケーションから) `IFinances` コンポーネントの `ItemOrders.Financial` インターフェイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-137">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>

## <a name="list-currently-exposed-interfaces"></a><span data-ttu-id="22c4b-138">現在公開されているインターフェイスの一覧表示</span><span class="sxs-lookup"><span data-stu-id="22c4b-138">List currently exposed interfaces</span></span>

- <span data-ttu-id="22c4b-139">次の例に示すように、`/list` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-139">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list
    ```

     <span data-ttu-id="22c4b-140">このコマンドは、ローカル コンピューターに関して、現在公開されているインターフェイス、および対応するアドレスとバインディングの詳細を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-140">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>

## <a name="list-specific-currently-exposed-interfaces"></a><span data-ttu-id="22c4b-141">現在公開されている特定のインターフェイスを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="22c4b-141">List specific currently exposed interfaces</span></span>

- <span data-ttu-id="22c4b-142">次の例に示すように、`/list` のオプションを使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-142">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     <span data-ttu-id="22c4b-143">このコマンドは、ローカル コンピューター上の OnlineStore COM+ アプリケーションの現在公開されている COM+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-143">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>

## <a name="display-help-for-options"></a><span data-ttu-id="22c4b-144">オプションのヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="22c4b-144">Display help for options</span></span>

- <span data-ttu-id="22c4b-145">次の例に示すように、/? オプションを</span><span class="sxs-lookup"><span data-stu-id="22c4b-145">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="22c4b-146">使用して ComSvcConfig を実行します。</span><span class="sxs-lookup"><span data-stu-id="22c4b-146">option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a><span data-ttu-id="22c4b-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="22c4b-147">See also</span></span>

- [<span data-ttu-id="22c4b-148">COM + アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="22c4b-148">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
