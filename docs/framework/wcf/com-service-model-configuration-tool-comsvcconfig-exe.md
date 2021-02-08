---
description: 詳細については、「COM + サービスモデル構成ツール (ComSvcConfig.exe)」を参照してください。
title: COM+ サービス モデル構成ツール (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 81bfcbd468cb5401646a49967b6381b48e2f7cf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781065"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="bd603-103">COM+ サービス モデル構成ツール (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="bd603-103">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>

<span data-ttu-id="bd603-104">COM+ サービス モデル構成コマンド ライン ツール (ComSvcConfig.exe) を使用すると、COM+ インターフェイスを Web サービスとして公開するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd603-104">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd603-105">構文</span><span class="sxs-lookup"><span data-stu-id="bd603-105">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd603-106">解説</span><span class="sxs-lookup"><span data-stu-id="bd603-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd603-107">ComSvcConfig.exe を使用するには、ローカル コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd603-107">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="bd603-108">ツールは次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="bd603-108">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="bd603-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bd603-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="bd603-110">ComSvcConfig.exe の詳細については、「 [方法: COM + サービスモデル構成ツールを使用する](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd603-110">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="bd603-111">次の表は、ComSvcConfig.exe で使用できるモードを示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-111">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="bd603-112">オプション</span><span class="sxs-lookup"><span data-stu-id="bd603-112">Option</span></span>|<span data-ttu-id="bd603-113">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-113">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="bd603-114">サービス モデル統合に COM+ インターフェイスの構成をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bd603-114">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="bd603-115">短縮形 : `/i`。</span><span class="sxs-lookup"><span data-stu-id="bd603-115">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="bd603-116">サービス モデル統合から COM+ インターフェイスの構成をアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="bd603-116">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="bd603-117">短縮形 : `/u`。</span><span class="sxs-lookup"><span data-stu-id="bd603-117">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="bd603-118">サービス モデル統合に構成されるインターフェイスを持つ COM+ アプリケーションとコンポーネントの情報を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-118">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="bd603-119">短縮形 : `/l`。</span><span class="sxs-lookup"><span data-stu-id="bd603-119">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="bd603-120">次の表は、ComSvcConfig.exe で使用できるフラグを示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-120">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="bd603-121">オプション</span><span class="sxs-lookup"><span data-stu-id="bd603-121">Option</span></span>|<span data-ttu-id="bd603-122">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bd603-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="bd603-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="bd603-124">構成する COM+ アプリケーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd603-124">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="bd603-125">短縮形 : `/a`。</span><span class="sxs-lookup"><span data-stu-id="bd603-125">Short form `/a`.</span></span>|  
|<span data-ttu-id="bd603-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="bd603-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="bd603-127">サービスのコントラクトとして構成される COM+ コンポーネントとインターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd603-127">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="bd603-128">短縮形 : `/c`。</span><span class="sxs-lookup"><span data-stu-id="bd603-128">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="bd603-129">ワイルドカード文字 () は、 \* コンポーネントとインターフェイスの名前を指定するときに使用できますが、意図していないインターフェイスを公開する可能性があるため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bd603-129">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="bd603-130">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="bd603-130">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="bd603-131">COM+ ホスト モードと Web ホスト モードのどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd603-131">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="bd603-132">短縮形 : `/h`。</span><span class="sxs-lookup"><span data-stu-id="bd603-132">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="bd603-133">COM+ ホスト モードを使用するには、COM + アプリケーションの明示的なアクティブ化が必要です。</span><span class="sxs-lookup"><span data-stu-id="bd603-133">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="bd603-134">Web ホスト モードを使用すると、COM+ アプリケーションを必要なときに自動的にアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="bd603-134">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="bd603-135">COM+ アプリケーションがライブラリ アプリケーションの場合は、インターネット インフォメーション サービス (IIS) のプロセスで実行します。</span><span class="sxs-lookup"><span data-stu-id="bd603-135">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="bd603-136">COM+ アプリケーションがサーバー アプリケーションの場合は、Dllhost.exe のプロセスで実行します。</span><span class="sxs-lookup"><span data-stu-id="bd603-136">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="bd603-137">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="bd603-137">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="bd603-138">Web ホスト モードを使用する場合は、ホストする Web サイトを指定します (`/hosting` フラグを参照)。</span><span class="sxs-lookup"><span data-stu-id="bd603-138">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="bd603-139">短縮形 : `/w`。</span><span class="sxs-lookup"><span data-stu-id="bd603-139">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="bd603-140">Web サイトを指定しない場合は、既定の Web サイトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd603-140">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="bd603-141">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="bd603-141">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="bd603-142">Web ホストを使用する場合は、ホストする仮想ディレクトリを指定します (`/hosting` フラグを参照)。</span><span class="sxs-lookup"><span data-stu-id="bd603-142">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="bd603-143">短縮形 : `/d`。</span><span class="sxs-lookup"><span data-stu-id="bd603-143">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="bd603-144">サービスからコントラクト定義を取得するクライアントをサポートするには、既定のサービス構成に Metadata Exchange (MEX) サービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd603-144">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="bd603-145">短縮形 : `/x`。</span><span class="sxs-lookup"><span data-stu-id="bd603-145">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="bd603-146">アプリケーション、コンポーネント、およびインターフェイス情報を ID として表示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-146">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="bd603-147">短縮形 : `/k`。</span><span class="sxs-lookup"><span data-stu-id="bd603-147">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="bd603-148">ComSvcConfig.exe がロゴを表示しないようにします。</span><span class="sxs-lookup"><span data-stu-id="bd603-148">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="bd603-149">短縮形 : `/n`。</span><span class="sxs-lookup"><span data-stu-id="bd603-149">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="bd603-150">発生するエラーに加えて、すべての警告または情報テキストを出力します。</span><span class="sxs-lookup"><span data-stu-id="bd603-150">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="bd603-151">短縮形 : `/v`。</span><span class="sxs-lookup"><span data-stu-id="bd603-151">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="bd603-152">使用方法を示すメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-152">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="bd603-153">短縮形 : `/?`。</span><span class="sxs-lookup"><span data-stu-id="bd603-153">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="bd603-154">指定されたインターフェイスが、公開できる 1 つ以上のメソッド署名を含む場合にサービス構成を生成します。</span><span class="sxs-lookup"><span data-stu-id="bd603-154">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="bd603-155">サービスの初期化時に、互換性のあるメソッドはサービス コントラクトで操作として表示され、互換性のないメソッドはサービス コントラクトから除外されます。</span><span class="sxs-lookup"><span data-stu-id="bd603-155">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="bd603-156">このフラグが指定されていない場合は、指定されたインターフェイスが互換性のないメソッドを 1 つ以上含むとツールはサービス構成を生成しません。</span><span class="sxs-lookup"><span data-stu-id="bd603-156">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="bd603-157">例</span><span class="sxs-lookup"><span data-stu-id="bd603-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="bd603-158">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-158">Description</span></span>  

 <span data-ttu-id="bd603-159">次の例は、COM+ ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.IFinancial` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd603-159">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="bd603-160">発生するエラーに加えて、すべての警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="bd603-160">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bd603-161">コード</span><span class="sxs-lookup"><span data-stu-id="bd603-161">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="bd603-162">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-162">Description</span></span>  

 <span data-ttu-id="bd603-163">次の例は、Web ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineWarehouse COM+ アプリケーションの) `IStockLevels` コンポーネントの `ItemInventory.Warehouse` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd603-163">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="bd603-164">Web サービスは、IIS の OnlineWarehouse 仮想ディレクトリで Web ホストされます。</span><span class="sxs-lookup"><span data-stu-id="bd603-164">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bd603-165">コード</span><span class="sxs-lookup"><span data-stu-id="bd603-165">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="bd603-166">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-166">Description</span></span>  

 <span data-ttu-id="bd603-167">次の例は、Web サービスとして公開されるインターフェイスのセットから (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.Financial` インターフェイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="bd603-167">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bd603-168">コード</span><span class="sxs-lookup"><span data-stu-id="bd603-168">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="bd603-169">説明</span><span class="sxs-lookup"><span data-stu-id="bd603-169">Description</span></span>  

 <span data-ttu-id="bd603-170">次の例は、ローカル マシン上の OnlineStore COM+ アプリケーションの現在公開されている COM+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bd603-170">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bd603-171">コード</span><span class="sxs-lookup"><span data-stu-id="bd603-171">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd603-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd603-172">See also</span></span>

- [<span data-ttu-id="bd603-173">方法: COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="bd603-173">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
