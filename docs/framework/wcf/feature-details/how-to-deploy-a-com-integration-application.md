---
description: '詳細については、「方法: COM + 統合アプリケーションを展開する」を参照してください。'
title: '方法: COM+ 統合アプリケーションを展開する'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 4bf9e72a631c97f3b791ecd01abb5cb74365772d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734387"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="47d80-103">方法: COM+ 統合アプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="47d80-103">How to: Deploy a COM+ Integration Application</span></span>

<span data-ttu-id="47d80-104">COM+ 統合アプリケーションを作成した後、これを別のコンピューターに展開する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="47d80-104">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="47d80-105">ここでは、COM+ 統合アプリケーションをコンピューター間で移動する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="47d80-105">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="47d80-106">COM+ ホスト統合アプリケーションの移動</span><span class="sxs-lookup"><span data-stu-id="47d80-106">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="47d80-107">両方のコンピューターに WCF がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47d80-107">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="47d80-108">コンピューター A からアプリケーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="47d80-108">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="47d80-109">コンピューター B にアプリケーションをインポートします。</span><span class="sxs-lookup"><span data-stu-id="47d80-109">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="47d80-110">アプリケーション ルート ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="47d80-110">Set the Application Root Directory.</span></span> <span data-ttu-id="47d80-111">通常これは %PROGRAMFILES%/ComPlus Applications/{AppGUID} になります。</span><span class="sxs-lookup"><span data-stu-id="47d80-111">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="47d80-112">コンピューター A のアプリケーション ルート ディレクトリにある Application.config ファイルおよび Application.manifest ファイルを、コンピューター B のアプリケーション ルート ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="47d80-112">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="47d80-113">コンピューター B の Application.config ファイルのサービス エンドポイント アドレスを編集して、コンピューター B が識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="47d80-113">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="47d80-114">たとえば、`http://machineA/MyService` を `http://machineB/MyService` に変更します。</span><span class="sxs-lookup"><span data-stu-id="47d80-114">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="47d80-115">Web ホスト統合アプリケーションの移動</span><span class="sxs-lookup"><span data-stu-id="47d80-115">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="47d80-116">両方のコンピューターに WCF がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47d80-116">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="47d80-117">コンピューター A からアプリケーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="47d80-117">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="47d80-118">コンピューター B にアプリケーションをインポートします。</span><span class="sxs-lookup"><span data-stu-id="47d80-118">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="47d80-119">コンピューター B で IIS vroot を作成します。</span><span class="sxs-lookup"><span data-stu-id="47d80-119">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="47d80-120">コンピューター A の vroot にある .svc ファイル (componentName.svc) と Web.config ファイルを、コンピューター B で新しく作成した vroot にコピーします。</span><span class="sxs-lookup"><span data-stu-id="47d80-120">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d80-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="47d80-121">See also</span></span>

- [<span data-ttu-id="47d80-122">COM + アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="47d80-122">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="47d80-123">方法: COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="47d80-123">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="47d80-124">方法: COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="47d80-124">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
