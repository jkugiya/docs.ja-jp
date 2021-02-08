---
description: 詳細については、WS-Atomic トランザクションサポートの構成」を参照してください。
title: WS-AtomicTransaction サポートの構成
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: c9b732bd0d6b6aa8cb1cf04803ae302a00348987
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780545"
---
# <a name="configure-ws-atomic-transaction-support"></a><span data-ttu-id="e8e0e-103">WS-Atomic トランザクションサポートの構成</span><span class="sxs-lookup"><span data-stu-id="e8e0e-103">Configure WS-Atomic Transaction support</span></span>

<span data-ttu-id="e8e0e-104">ここでは、WS-AtomicTransaction (WS-AT) 構成ユーティリティを使用して WS-AT サポートを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-104">This topic describes how you can configure WS-AtomicTransaction (WS-AT) support by using the WS-AT Configuration Utility.</span></span>

## <a name="use-the-ws-at-configuration-utility"></a><span data-ttu-id="e8e0e-105">WS-AT 構成ユーティリティを使用する</span><span class="sxs-lookup"><span data-stu-id="e8e0e-105">Use the WS-AT configuration utility</span></span>

<span data-ttu-id="e8e0e-106">WS-AT 構成ユーティリティ (wsatConfig.exe) は、WS-AT 設定の構成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-106">The WS-AT Configuration Utility (wsatConfig.exe) is used to configure WS-AT settings.</span></span> <span data-ttu-id="e8e0e-107">WS-AT プロトコル サービスを有効にするには、この構成ユーティリティを使用して、WS-AT の HTTPS ポートを構成し、X.509 証明書をその HTTPS ポートにバインドし、証明書のサブジェクト名または拇印を指定して、承認されたパートナーの証明書を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-107">In order to enable the WS-AT protocol service, you must use the configuration utility to configure the HTTPS port for WS-AT, bind an X.509 certificate to the HTTPS port, and configure authorized partner certificates by specifying certificate subject names or thumbprints.</span></span> <span data-ttu-id="e8e0e-108">この構成ユーティリティでは、トレース モードを選択して、送信トランザクションの既定のタイムアウト値と受信トランザクションの最大タイムアウト値を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-108">The configuration utility also allows you to select the tracing mode and set default outgoing and maximum incoming transaction timeouts.</span></span>

<span data-ttu-id="e8e0e-109">このツールの機能は、コンポーネント サービス管理コンソールで Microsoft 管理コンソール (MMC) のプロパティ ページ スナップインを使用するか、またはコマンド ライン ウィンドウから操作できます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-109">You can access this tool's functionality by using a Microsoft Management Console (MMC) property page snap-in in the Component Services management console, or from a command-line window.</span></span> <span data-ttu-id="e8e0e-110">WS-AT サポートをローカル コンピューターで構成するには、コマンド ライン ウィンドウを使用し、ローカル コンピューターとリモート コンピューターの両方で設定を構成するには、MMC スナップインを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-110">Configure WS-AT support on the local machine through the command-line window; configure settings on both local and remote machines by using the MMC snap-in.</span></span>

<span data-ttu-id="e8e0e-111">コマンド ライン ウィンドウは、Windows SDK のインストール場所の "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation" で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-111">The command-line window can be accessed in the Windows SDK installation location "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".</span></span>

<span data-ttu-id="e8e0e-112">コマンドラインツールの詳細については、「ws-atomictransaction [構成ユーティリティ (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-112">For more information about the command-line tool, see [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md).</span></span>

<span data-ttu-id="e8e0e-113">Windows XP または Windows Server 2003 を実行している場合、MMC スナップインにアクセスするには、[コントロールパネル]、[管理ツール]、[ **コンポーネントサービス**] の順に移動し、 **マイコンピューター** を右クリックして、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-113">If you are running Windows XP or Windows Server 2003, you can access the MMC snap-in by navigating to **Control Panel/Administrative Tools/Component Services**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="e8e0e-114">この場所では、Microsoft 分散トランザクション コーディネーター (MSDTC) を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-114">This is the same location where you can configure the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="e8e0e-115">構成に使用できるオプションは、[ **ws-at** ] タブの下にグループ化されています。Windows Vista または Windows Server 2008 を実行している場合は、[ **スタート** ] ボタンをクリックし、 `dcomcnfg.exe` **検索** ボックスに「」と入力すると、MMC スナップインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-115">Options available for configuration are grouped under the **WS-AT** tab. If you are running Windows Vista or Windows Server 2008, the MMC snap-in can be found by clicking the **Start** button, and entering `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="e8e0e-116">MMC が開いたら、 **My Computer\Distributed Transaction COORDINATOR\LOCAL DTC** ノードに移動し、右クリックして、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-116">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="e8e0e-117">構成に使用できるオプションは、[ **ws-at** ] タブの下にグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-117">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

<span data-ttu-id="e8e0e-118">スナップインの詳細については、「ws-atomictransaction [構成 MMC スナップ](../ws-atomictransaction-configuration-mmc-snap-in.md)イン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-118">For more information about the snap-in, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md).</span></span>

<span data-ttu-id="e8e0e-119">ツールのユーザー インターフェイスを有効にするには、WsatUI.dll ファイルを登録しておく必要があります。このファイルは、次のパスにあります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-119">To enable the tool's user interface, you must first register the WsatUI.dll file, located at the following path</span></span>

<span data-ttu-id="e8e0e-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span><span class="sxs-lookup"><span data-stu-id="e8e0e-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span></span>

<span data-ttu-id="e8e0e-121">製品を登録するには、[コマンド プロンプト] ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-121">To register the product, execute the following command from a Command Prompt window:</span></span>

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a><span data-ttu-id="e8e0e-122">WS-AT を有効にする</span><span class="sxs-lookup"><span data-stu-id="e8e0e-122">Enable WS-AT</span></span>

<span data-ttu-id="e8e0e-123">ポート 443 と、ローカル コンピューター ストアにインストールされている秘密キーを持つ X.509 証明書を使用して、MSDTC 内部で WS-AT プロトコル サービスを有効にするには、wsatConfig.exe ツールを使用して次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-123">To enable the WS-AT protocol service inside MSDTC using port 443 and an X.509 certificate with a private key that has been installed in the local machine store, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

<span data-ttu-id="e8e0e-124">個々のパラメーターを、ユーザーの環境に適した値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-124">Substitute the respective parameters with values relevant to your environment.</span></span>

<span data-ttu-id="e8e0e-125">MSDTC 内部で WS-AT プロトコル サービスを無効にするには、wsatConfig.exe ツールを使用して次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-125">To disable the WS-AT protocol service inside MSDTC, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a><span data-ttu-id="e8e0e-126">2台のコンピューター間の信頼を構成する</span><span class="sxs-lookup"><span data-stu-id="e8e0e-126">Configure trust between two machines</span></span>

<span data-ttu-id="e8e0e-127">WS-AT プロトコル サービスでは、管理者が、分散トランザクションに参加する個々のアカウントを明示的に承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-127">The WS-AT protocol service requires the administrator to explicitly authorize individual accounts to participate in distributed transactions.</span></span> <span data-ttu-id="e8e0e-128">2 台のコンピューターの管理者である場合は、両方のコンピューターを構成して、相互の信頼関係を確立することができます。それには、コンピューター間で適切な証明書を交換し、その証明書を適切な証明書ストアにインストールし、wsatConfig.exe ツールを使用して各コンピューターの証明書をお互いの承認済み参加者の証明書リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-128">If you are an administrator for two machines, you can configure both machines to establish a mutual trust relationship by exchanging the right set of certificates between the machines, installing them into the appropriate certificate stores, and using the wsatConfig.exe tool to add each machine's certificate to the other's list of authorized participant certificates.</span></span> <span data-ttu-id="e8e0e-129">この手順は、WS-AT を使用する 2 台のコンピューター間で分散トランザクションを実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-129">This step is necessary to perform distributed transactions between two machines using WS-AT.</span></span>

<span data-ttu-id="e8e0e-130">次の例では、A と B という 2 台のコンピューター間で信頼を確立する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-130">In the following example outlines the steps to establish trust between two machines, A and B.</span></span>

### <a name="create-and-export-certificates"></a><span data-ttu-id="e8e0e-131">証明書の作成とエクスポート</span><span class="sxs-lookup"><span data-stu-id="e8e0e-131">Create and export certificates</span></span>

<span data-ttu-id="e8e0e-132">この手順では、MMC 証明書スナップインを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-132">This procedure requires the MMC Certificates snap-in.</span></span> <span data-ttu-id="e8e0e-133">このスナップインにアクセスするには、[スタート] ボタンをクリックして [ファイル名を指定して実行] をクリックし、入力ボックスに「mmc」と入力して [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-133">The snap-in can be accessed by opening the Start/Run menu, typing "mmc" in the input box and pressing OK.</span></span> <span data-ttu-id="e8e0e-134">次に、[**コンソール** 1] ウィンドウで、[**ファイル]、[追加**]、[削除] スナップインの順に移動し、[追加] をクリックして、[**使用可能なスタンドアロンスナップイン**] ボックスの一覧から [**証明書**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-134">Then, in the **Console1** window, navigate to **the File/Add-Remove** Snap-in, click Add, and choose **Certificates** from the **Available Standalone Snapins** list.</span></span> <span data-ttu-id="e8e0e-135">最後に、[管理する **コンピューターアカウント** ] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-135">Finally, select **Computer Account** to manage and click **OK**.</span></span> <span data-ttu-id="e8e0e-136">スナップインコンソールに [ **証明書** ] ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-136">The **Certificates** node appears in the snap-in console.</span></span>

<span data-ttu-id="e8e0e-137">信頼を確立するために必要な証明書は、あらかじめ用意されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-137">You must already possess the required certificates to establish trust.</span></span> <span data-ttu-id="e8e0e-138">次の手順の前に新しい証明書を作成してインストールする方法については、「 [方法: 開発時に WCF に一時的なクライアント証明書を作成してインストール](/previous-versions/msp-n-p/ff650751(v=pandp.10))する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-138">To learn how to create and install new certificates prior to the following steps, see [How to: Create and Install Temporary Client Certificates in WCF During Development](/previous-versions/msp-n-p/ff650751(v=pandp.10)).</span></span>

1. <span data-ttu-id="e8e0e-139">コンピューター A で、MMC 証明書スナップインを使用して、既存の証明書 (certA) を LocalMachine\MY (Personal Node) ストアと LocalMachine\ROOT (信頼されたルート証明機関のノード) ストアにインポートします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-139">On machine A, using the MMC Certificates snap-in, import the existing certificate (certA) into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span> <span data-ttu-id="e8e0e-140">証明書を特定のノードにインポートするには、ノードを右クリックし、[ **すべてのタスク**]、[インポート] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-140">To import a certificate to a specific node, right-click the node and choose **All Tasks/Import**.</span></span>

2. <span data-ttu-id="e8e0e-141">コンピューター B で、MMC 証明書スナップインを使用して、秘密キーを持つ証明書 certB を作成するか取得し、LocalMachine\MY (Personal Node) ストアと LocalMachine\ROOT (信頼されたルート証明機関のノード) ストアにインポートします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-141">On machine B, using the MMC Certificates snap-in, create or obtain a certificate certB with a private key and import it into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span>

3. <span data-ttu-id="e8e0e-142">certA の秘密キーをファイルにエクスポートします (エクスポートしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-142">Export certA's public key to a file if this has not been done already.</span></span>

4. <span data-ttu-id="e8e0e-143">certB の秘密キーをファイルにエクスポートします (エクスポートしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-143">Export certB's public key to a file if this has not been done already.</span></span>

### <a name="establish-mutual-trust-between-machines"></a><span data-ttu-id="e8e0e-144">マシン間の相互の信頼を確立する</span><span class="sxs-lookup"><span data-stu-id="e8e0e-144">Establish mutual trust between machines</span></span>

1. <span data-ttu-id="e8e0e-145">コンピューター A で、certB のファイルを LocalMachine\MY ストアと LocalMachine\ROOT ストアにインポートします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-145">On machine A, import the file representation of certB into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="e8e0e-146">これによって、コンピューター A が certB を信頼して通信することを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-146">This declares that machine A trusts certB to communicate with it.</span></span>

2. <span data-ttu-id="e8e0e-147">コンピューター B で、certA のファイルを LocalMachine\MY ストアと LocalMachine\ROOT ストアにインポートします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-147">On machine B, import certA’s file into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="e8e0e-148">これによって、コンピューター B が certA を信頼して通信することを示します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-148">This implies that machine B trusts certA to communicate with it.</span></span>

<span data-ttu-id="e8e0e-149">この手順が完了すると、2 台のコンピューター間に信頼が確立されるので、WS-AT を使用して相互に通信するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-149">After completing these steps, trust is established between the two machines, and they can be configured to communicate with each other using WS-AT.</span></span>

### <a name="configure-msdtc-to-use-certificates"></a><span data-ttu-id="e8e0e-150">MSDTC で証明書を使用するように構成する</span><span class="sxs-lookup"><span data-stu-id="e8e0e-150">Configure MSDTC to use certificates</span></span>

<span data-ttu-id="e8e0e-151">WS-AT プロトコル サービスは、クライアントとサーバーの両方として機能するので、このサービスは、受信接続のリッスンと送信接続の開始を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-151">Since the WS-AT protocol service acts as both a client and a server, it must both listen for incoming connections and initiate outgoing connections.</span></span> <span data-ttu-id="e8e0e-152">このため、外部の通信相手と通信するときに使用する証明書と、受信接続を受け入れるときに承認する証明書を MSDTC に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-152">Therefore, you need to configure MSDTC so that it knows which certificate to use when communicating with external parties, and which certificates to authorize when accepting incoming communication.</span></span>

<span data-ttu-id="e8e0e-153">これを構成するには、MMC WS-AT スナップインを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-153">You can configure this by using the MMC WS-AT snap-in.</span></span> <span data-ttu-id="e8e0e-154">このツールの詳細については、「ws-atomictransaction [構成 MMC スナップ](../ws-atomictransaction-configuration-mmc-snap-in.md) イン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-154">For more information about this tool, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="e8e0e-155">次の手順では、MSDTC を実行している 2 台のコンピューター間に信頼を確立する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-155">The following steps describe how to establish trust between two computers running MSDTC.</span></span>

1. <span data-ttu-id="e8e0e-156">コンピューター A の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-156">Configure machine A's settings.</span></span> <span data-ttu-id="e8e0e-157">[エンドポイント証明書] で、[certA] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-157">For "Endpoint Certificate", select certA.</span></span> <span data-ttu-id="e8e0e-158">"承認された証明書" の場合は、certB を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-158">For "Authorized Certificates", select the certB.</span></span>

2. <span data-ttu-id="e8e0e-159">コンピューター B の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-159">Configure machine B's settings.</span></span> <span data-ttu-id="e8e0e-160">[エンドポイント証明書] で、[certB] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-160">For "Endpoint Certificate", select certB.</span></span> <span data-ttu-id="e8e0e-161">"承認された証明書" の場合は、certA を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-161">For "Authorized Certificates", select the certA.</span></span>

> [!NOTE]
> <span data-ttu-id="e8e0e-162">一方のコンピューターからもう一方のコンピューターにメッセージを送信する場合、送信側は、受信側の証明書のサブジェクト名と受信側のコンピューターの名前が一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-162">When one machine sends a message to the other machine, the sender attempts to verify that the subject name of the recipient’s certificate and the name of the recipient’s machine match.</span></span> <span data-ttu-id="e8e0e-163">これらが一致しないと、証明書の確認が失敗し、2 台のコンピューターは通信できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-163">If they do not match, certificate verification fails and the two machines cannot communicate.</span></span>
>
> <span data-ttu-id="e8e0e-164">ドメインに参加しているコンピューターの名前は完全修飾ドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-164">For a machine joined to a domain, the name is the fully qualified domain name.</span></span> <span data-ttu-id="e8e0e-165">既定では、ワークグループ上のコンピューターの名前は、コンピューターの NetBIOS 名です。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-165">By default, the name of a machine on a workgroup is the machine’s NetBIOS name.</span></span> <span data-ttu-id="e8e0e-166">ただし、2 台のコンピューター間で使用されている接続用のドメイン ネーム システム (DNS) サフィックスが存在する場合は、名前に DNS サフィックス含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-166">However, the name can also include a Domain Name System (DNS) suffix if one is present for the connection being used between the two machines.</span></span>
>
> <span data-ttu-id="e8e0e-167">ワークグループ コンピューターがドメインに参加するときなどにコンピューターの名前を変更した場合は、証明書を再発行するか、DNS サフィックスを手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-167">If the name of the machine changes, for example, when a workgroup machine joins a domain, you must reissue certificates or manually configure DNS suffixes.</span></span>

## <a name="security"></a><span data-ttu-id="e8e0e-168">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e8e0e-168">Security</span></span>

<span data-ttu-id="e8e0e-169">一部の MSDTC と WS-AT 関連の設定はそれぞれ、レジストリ HKLM\Software\Microsoft\MSDTC と HKLM\Software\Microsoft\WSAT に格納されるので、必ずこのレジストリ キーをセキュリティで保護し、管理者だけがそのキーに書き込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-169">Since some of the settings related to MSDTC and WS-AT are stored in the registry at HKLM\Software\Microsoft\MSDTC and at HKLM\Software\Microsoft\WSAT, respectively, ensure that these registry keys are secured so that only administrators can write to them.</span></span> <span data-ttu-id="e8e0e-170">レジストリエディターツールで、セキュリティで保護するキーを右クリックし、[ **アクセス許可** ] を選択して適切なアクセス制御を設定します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-170">In the Registry Editor tool, right-click the key you want to secure and select **Permission** to set the appropriate access control.</span></span> <span data-ttu-id="e8e0e-171">重要なキーを特権の低いユーザーに対して読み取り専用にしておくことが、システムのセキュリティと整合性を確保するために重要です。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-171">It is crucial to the security and integrity of the system that important keys are read-only for low-privileged users.</span></span>

<span data-ttu-id="e8e0e-172">MSDTC を展開する場合、管理者は、すべての MSDTC データの交換がセキュリティで保護されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-172">When deploying MSDTC, the administrator must ensure that any MSDTC data interchange is secure.</span></span> <span data-ttu-id="e8e0e-173">ワークグループの展開では、トランザクションのインフラストラクチャを悪質なユーザーから隔離してください。クラスターの展開では、クラスター レジストリをセキュリティで保護してください。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-173">In a workgroup deployment, isolate the transactional infrastructure from malicious users; in a cluster deployment, secure the cluster registry.</span></span>

## <a name="tracing"></a><span data-ttu-id="e8e0e-174">トレース</span><span class="sxs-lookup"><span data-stu-id="e8e0e-174">Tracing</span></span>

<span data-ttu-id="e8e0e-175">WS-AT プロトコルサービスは、ws-atomictransaction [構成 MMC スナップ](../ws-atomictransaction-configuration-mmc-snap-in.md) インツールを使用して有効化および管理できる、トランザクション固有の統合トレースをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-175">The WS-AT protocol service supports integrated, transaction-specific tracing that can be enabled and managed through the use of the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) tool.</span></span> <span data-ttu-id="e8e0e-176">トレースには、特定のトランザクションに参加した時刻、トランザクションが終了状態に到達した時刻、各トランザクション参加で受け取った結果などを示すデータを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-176">Traces can include data indicating the time an enlistment is made for a specific transaction, the time a transaction reaches its terminal state, the outcome each transaction enlistment has received.</span></span> <span data-ttu-id="e8e0e-177">すべてのトレースは、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) ツールを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-177">All traces can be viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tool.</span></span>

<span data-ttu-id="e8e0e-178">WS-AT プロトコル サービスは、ETW トレース セッションを通じて統合 ServiceModel トレースもサポートします。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-178">The WS-AT protocol service also supports integrated ServiceModel tracing through the ETW trace session.</span></span> <span data-ttu-id="e8e0e-179">これにより、既存のトランザクション トレースに加えて、より詳細な通信固有のトレースが得られます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-179">This provides more detailed, communication-specific traces in addition to the existing transaction traces.</span></span>  <span data-ttu-id="e8e0e-180">これらの追加トレースを有効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-180">To enable these additional traces, follow these steps</span></span>

1. <span data-ttu-id="e8e0e-181">[ **開始/実行** ] メニューを開き、入力ボックスに「regedit」と入力して、[ **OK**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-181">Open the **Start/Run** menu, type "regedit" in the input box and select **OK**.</span></span>

2. <span data-ttu-id="e8e0e-182">**レジストリエディター** で、左側のウィンドウにある次のフォルダーに移動し、Hkey_Local_Machine \software\microsoft\wsat\3.0\ を開きます。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-182">In the **Registry Editor**, navigate to the following folder on the left pane, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\</span></span>

3. <span data-ttu-id="e8e0e-183">`ServiceModelDiagnosticTracing`右ペインで値を右クリックし、[**変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-183">Right-click the `ServiceModelDiagnosticTracing` value in the right pane and select **Modify**.</span></span>

4. <span data-ttu-id="e8e0e-184">[ **値のデータ** 入力] ボックスに、次の有効な値のいずれかを入力して、有効にするトレースレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-184">In the **Value data** input box, enter one of the following valid values to specify the trace level you want to enable.</span></span>

- <span data-ttu-id="e8e0e-185">0 : オフ</span><span class="sxs-lookup"><span data-stu-id="e8e0e-185">0: off</span></span>

- <span data-ttu-id="e8e0e-186">1 : クリティカル</span><span class="sxs-lookup"><span data-stu-id="e8e0e-186">1: critical</span></span>

- <span data-ttu-id="e8e0e-187">3 : エラー (</span><span class="sxs-lookup"><span data-stu-id="e8e0e-187">3: error.</span></span> <span data-ttu-id="e8e0e-188">これは、既定値です。</span><span class="sxs-lookup"><span data-stu-id="e8e0e-188">This is the default value</span></span>

- <span data-ttu-id="e8e0e-189">7 : 警告</span><span class="sxs-lookup"><span data-stu-id="e8e0e-189">7: warning</span></span>

- <span data-ttu-id="e8e0e-190">15 : 情報</span><span class="sxs-lookup"><span data-stu-id="e8e0e-190">15: information</span></span>

- <span data-ttu-id="e8e0e-191">31 : 詳細</span><span class="sxs-lookup"><span data-stu-id="e8e0e-191">31: verbose</span></span>

## <a name="see-also"></a><span data-ttu-id="e8e0e-192">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8e0e-192">See also</span></span>

- [<span data-ttu-id="e8e0e-193">WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="e8e0e-193">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="e8e0e-194">WS-AtomicTransaction 構成 MMC スナップイン</span><span class="sxs-lookup"><span data-stu-id="e8e0e-194">WS-AtomicTransaction Configuration MMC Snap-in</span></span>](../ws-atomictransaction-configuration-mmc-snap-in.md)
