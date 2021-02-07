---
description: 詳細については、「拡張保護認証サンプルの ReadMe」を参照してください。
title: 拡張保護認証のサンプルの ReadMe
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: edab04c7762bf8964f634107debd3de35a7702ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733308"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="349bc-103">拡張保護認証のサンプルの ReadMe</span><span class="sxs-lookup"><span data-stu-id="349bc-103">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="349bc-104">拡張保護は、攻撃者 ("man-in-the-middle") がクライアントの資格情報を傍受し、クライアントの目的のサーバー上のセキュリティで保護されたリソースにアクセスするために使用する man-in-the-middle (MITM) 攻撃から保護するためのセキュリティ上の取り組みです。</span><span class="sxs-lookup"><span data-stu-id="349bc-104">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="349bc-105">詳細については、「 [認証の拡張保護の概要](extended-protection-for-authentication-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="349bc-105">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="349bc-106">このサンプルは、IIS でホストされた場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="349bc-106">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="349bc-107">このサンプルは HTTPS をサポートしないので、Visual Studio Development Server 上では機能しません。</span><span class="sxs-lookup"><span data-stu-id="349bc-107">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="349bc-108">サンプルをセットアップしてビルドし、実行するには</span><span class="sxs-lookup"><span data-stu-id="349bc-108">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="349bc-109">[プログラムの追加と削除]-> Windows の機能] から、コンピューターに IIS をインストールします。</span><span class="sxs-lookup"><span data-stu-id="349bc-109">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="349bc-110">Windows の機能で Windows 認証を有効にする: インターネットインフォメーションサービス-> World Wide Web サービス-> セキュリティ-> Windows 認証] をオンにします。</span><span class="sxs-lookup"><span data-stu-id="349bc-110">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="349bc-111">Windows の機能で HTTP アクティブ化を有効にする: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation HTTP アクティブ化。</span><span class="sxs-lookup"><span data-stu-id="349bc-111">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="349bc-112">このサンプルを実行するには、サーバーとの安全なチャネルを確立する必要のあるクライアントが必要なので、インターネット インフォメーション サービス (IIS) マネージャーからインストールすることのできるサーバー証明書が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349bc-112">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="349bc-113">[機能ビュー] タブから、IIS マネージャーの > サーバー証明書を開きます。</span><span class="sxs-lookup"><span data-stu-id="349bc-113">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="349bc-114">このサンプルをテストする目的で、自己署名証明書を作成できます </span><span class="sxs-lookup"><span data-stu-id="349bc-114">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="349bc-115">(インターネット エクスプローラーで証明書の安全性に関するプロンプトが表示されないようにする場合は、信頼されたルート証明機関ストアに証明書をインストールできます)。</span><span class="sxs-lookup"><span data-stu-id="349bc-115">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="349bc-116">既定の Web サイトの操作ウィンドウに移動します。</span><span class="sxs-lookup"><span data-stu-id="349bc-116">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="349bc-117">[サイト > バインドの編集] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="349bc-117">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="349bc-118">存在しない場合は、種類として HTTPS を追加します。ポート番号に 443 を指定し、前の手順で作成した SSL 証明書を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="349bc-118">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="349bc-119">サービスをビルドします。</span><span class="sxs-lookup"><span data-stu-id="349bc-119">Build the service.</span></span> <span data-ttu-id="349bc-120">(プロジェクト プロパティで指定されたビルド後のアクションから) IIS に仮想ディレクトリが作成され、サービスを Web ホスト サービスにするために必要な dll、.svc、および構成ファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="349bc-120">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="349bc-121">IIS マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="349bc-121">Open the IIS Manager.</span></span> <span data-ttu-id="349bc-122">前の手順で作成した仮想ディレクトリ (ExtendedProtection) を右クリックして、[アプリケーションへの変換] を選択します。</span><span class="sxs-lookup"><span data-stu-id="349bc-122">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="349bc-123">この仮想ディレクトリの認証モジュールを IIS マネージャーで開き、Windows 認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="349bc-123">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="349bc-124">このサンプルでは対応する ExtendedProtection 設定が [常に] に設定されているので、この仮想ディレクトリの Windows 認証の [詳細設定] を開き、[必須] に設定します。</span><span class="sxs-lookup"><span data-stu-id="349bc-124">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="349bc-125">ブラウザー ウィンドウから URL にアクセスして、サービスをテストできます。</span><span class="sxs-lookup"><span data-stu-id="349bc-125">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="349bc-126">コンピューター間でこの URL にアクセスする場合は、すべての受信 HTTP および HTTPS 通信に対してファイアウォールが開かれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="349bc-126">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="349bc-127">クライアント構成ファイルを開き、-address 属性の完全なコンピューター名を指定して \<client>  -  \<endpoint> 置き換え \<full_machine_name> ます。</span><span class="sxs-lookup"><span data-stu-id="349bc-127">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="349bc-128">クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="349bc-128">Run the client.</span></span> <span data-ttu-id="349bc-129">クライアントがセキュリティで保護されたチャネルを確立し、エンドポイント保護を使用してサービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="349bc-129">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
