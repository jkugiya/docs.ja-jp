---
description: 詳細については、インターネットインフォメーションサービス (IIS) サーバー証明書のインストール手順に関するページを参照してください。
title: インターネット インフォメーション サービス (IIS) サーバー証明書インストール手順
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1ac5209e9ff82911b0631c190e16ff457fea0db6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631854"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="b0096-103">インターネット インフォメーション サービス (IIS) サーバー証明書インストール手順</span><span class="sxs-lookup"><span data-stu-id="b0096-103">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>

<span data-ttu-id="b0096-104">インターネット インフォメーション サービス (IIS) と安全に通信するこのサンプルを実行するには、サーバー証明書を作成してインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0096-104">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="b0096-105">手順 1.</span><span class="sxs-lookup"><span data-stu-id="b0096-105">Step 1.</span></span> <span data-ttu-id="b0096-106">証明書の作成</span><span class="sxs-lookup"><span data-stu-id="b0096-106">Creating Certificates</span></span>  

 <span data-ttu-id="b0096-107">コンピューターの証明書を作成するには、管理者特権で Visual Studio の開発者コマンドプロンプトを開き、IIS とのセキュリティで保護された通信を使用する各サンプルに含まれる Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="b0096-107">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="b0096-108">このバッチ ファイルを実行する前に、Makecert.exe を含むフォルダがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0096-108">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="b0096-109">Setup.bat で証明書の作成に使用されるコマンドは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0096-109">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="b0096-110">手順 2.</span><span class="sxs-lookup"><span data-stu-id="b0096-110">Step 2.</span></span> <span data-ttu-id="b0096-111">証明書のインストール</span><span class="sxs-lookup"><span data-stu-id="b0096-111">Installing Certificates</span></span>  

 <span data-ttu-id="b0096-112">先ほど作成した証明書をインストールするために必要な手順は、使用している IIS のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b0096-112">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="b0096-113">IIS 5.1 (Windows XP) および IIS 6.0 (Windows Server 2003) に証明書をインストールするには</span><span class="sxs-lookup"><span data-stu-id="b0096-113">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="b0096-114">インターネット インフォメーション サービス マネージャー MMC スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="b0096-114">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="b0096-115">[既定の Web サイト] を右クリックし、[ **プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0096-115">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="b0096-116">[ **ディレクトリセキュリティ** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0096-116">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="b0096-117">[ **サーバー証明書** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0096-117">Click the **Server Certificate** button.</span></span> <span data-ttu-id="b0096-118">Web サーバー証明書ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="b0096-118">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="b0096-119">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="b0096-119">Complete the wizard.</span></span> <span data-ttu-id="b0096-120">証明書を割り当てるオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="b0096-120">Select the option to assign a certificate.</span></span> <span data-ttu-id="b0096-121">表示される証明書の一覧から ServiceModelSamples-HTTPS-Server 証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0096-121">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="b0096-122">![IIS 証明書ウィザード](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="b0096-122">![IIS Certificate Wizard](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="b0096-123">HTTPS アドレスを使用して、ブラウザーでサービスへのアクセスをテストし `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="b0096-123">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="b0096-124">Httpcfg.exe であらかじめ SSL が構成されている場合</span><span class="sxs-lookup"><span data-stu-id="b0096-124">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="b0096-125">Makecert.exe を使用 (または Setup.bat を実行) して、サーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0096-125">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="b0096-126">IIS マネージャを実行し、前の手順に従って証明書をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b0096-126">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="b0096-127">クライアント プログラムに次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="b0096-127">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b0096-128">このコードが必要になるのは、Makecert.exe によって作成された証明書などをテストする場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b0096-128">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="b0096-129">製品版のコードには、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="b0096-129">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="b0096-130">IIS 7.0 (Windows Vista および Windows Server 2008) に証明書をインストールするには</span><span class="sxs-lookup"><span data-stu-id="b0096-130">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="b0096-131">[ **スタート** ] メニューの [ファイルの **実行**] をクリックし、「 **inetmgr.exe** 」と入力して、インターネットインフォメーションサービス (IIS) MMC スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="b0096-131">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="b0096-132">[**既定の Web サイト**] を右クリックし、[**バインドの編集...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0096-132">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="b0096-133">[**サイトバインド**] ダイアログボックスの [**追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0096-133">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="b0096-134">[**種類**] ドロップダウンリストから [ **HTTPS** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0096-134">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="b0096-135">[ **SSL 証明書**] ボックスの一覧から **ServiceModelSamples** を選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0096-135">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="b0096-136">HTTPS アドレスを使用して、ブラウザーでサービスへのアクセスをテストし `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="b0096-136">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0096-137">先ほどインストールしたテスト証明書は信頼された証明書ではないので、この証明書でセキュリティ保護されたローカル Web アドレスを参照した場合、Internet Explorer のセキュリティ警告がさらに発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0096-137">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="b0096-138">証明書の削除</span><span class="sxs-lookup"><span data-stu-id="b0096-138">Removing Certificates</span></span>  
  
- <span data-ttu-id="b0096-139">前に説明したようにインターネット インフォメーション サービス マネージャーを使用しますが、証明書またはバインディングを追加するのではなく削除します。</span><span class="sxs-lookup"><span data-stu-id="b0096-139">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="b0096-140">次のコマンドを使用して、コンピューターの証明書を削除します。</span><span class="sxs-lookup"><span data-stu-id="b0096-140">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
