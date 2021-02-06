---
description: 詳細については、「アプリケーションの構成」を参照してください。
title: アプリケーションの構成
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: d28876068f23a67ea1ff005d7d217e09b2854783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646063"
---
# <a name="configuring-your-application"></a><span data-ttu-id="d5c23-103">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="d5c23-103">Configuring Your Application</span></span>

<span data-ttu-id="d5c23-104">Windows Communication Foundation (WCF) では、.NET 構成システムを使用して、コンピューターとアプリケーションの両方のスコープでサービスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="d5c23-104">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="d5c23-105">WCF によって定義された構成設定は、 `<system.serviceModel>` セクショングループにあります。</span><span class="sxs-lookup"><span data-stu-id="d5c23-105">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="d5c23-106">WCF サービスを構成する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5c23-106">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="d5c23-107">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="d5c23-107">Configuring Services</span></span>](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="d5c23-108">アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。</span><span class="sxs-lookup"><span data-stu-id="d5c23-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="d5c23-109">.NET 構成ファイルのアプリケーション設定の詳細については、「」を参照してください [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) 。</span><span class="sxs-lookup"><span data-stu-id="d5c23-109">For more information about application settings in .NET configuration files, see [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="d5c23-110">構成エディターの使用</span><span class="sxs-lookup"><span data-stu-id="d5c23-110">Using the Configuration Editor</span></span>  

 <span data-ttu-id="d5c23-111">WCF [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) を使用すると、管理者および開発者は、グラフィカルユーザーインターフェイスを使用して wcf サービスの構成設定を作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="d5c23-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="d5c23-112">このツールを使用すると、XML 構成ファイルを直接編集することなく、WCF のバインディング、動作、サービス、および診断の設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="d5c23-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="d5c23-113">Visual Studio の構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="d5c23-113">Editing Configuration Files in Visual Studio</span></span>  

 <span data-ttu-id="d5c23-114">Visual Studio で WCF サービスプロジェクトの構成ファイルを編集するには、 **ソリューションエクスプローラー** で右クリックし、[ **Wcf 構成の編集** ] コンテキストメニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5c23-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="d5c23-115">これにより、 [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)が起動します。</span><span class="sxs-lookup"><span data-stu-id="d5c23-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5c23-116">**ソリューションエクスプローラー** で Wcf Web サービスプロジェクトの構成ファイルを右クリックして編集する場合は、[ **Wcf 構成の編集**] コンテキストメニュー項目が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5c23-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="d5c23-117">この問題を回避するには、[ **ツール** ] メニューをクリックし、[ **WCF サービス構成エディター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d5c23-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="d5c23-118">その後、構成ファイルを右クリックし、[ **WCF 構成の編集** ] コンテキストメニュー項目を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5c23-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c23-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5c23-119">See also</span></span>

- [<span data-ttu-id="d5c23-120">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="d5c23-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="d5c23-121">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="d5c23-121">Configuring Services</span></span>](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
