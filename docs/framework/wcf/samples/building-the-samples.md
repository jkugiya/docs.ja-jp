---
description: 詳細については、「Windows Communication Foundation サンプルのビルド」を参照してください。
title: Windows Communication Foundation サンプルのビルド
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: a53073ac92369574b204dbce998bebb8844fce8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704187"
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="a0555-103">Windows Communication Foundation サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="a0555-103">Building the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="a0555-104">Windows Communication Foundation (WCF) のサンプルは、Visual Studio IDE を使用するか、コマンドラインから **msbuild** コマンドを使用してビルドできます。</span><span class="sxs-lookup"><span data-stu-id="a0555-104">The Windows Communication Foundation (WCF) samples can be built using the Visual Studio IDE or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="a0555-105">ここでは、両方の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0555-105">Both procedures are described in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="a0555-106">WCF サンプルをビルドまたは実行する前に、 [Windows Communication Foundation のサンプルに対して1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a0555-106">Before building or running any of the WCF samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

## <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="a0555-107">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="a0555-107">To build the sample using a command prompt</span></span>

1. <span data-ttu-id="a0555-108">Visual Studio の開発者コマンドプロンプトを開き、サンプルをインストールしたディレクトリの場所にある言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="a0555-108">Open Developer Command Prompt for Visual Studio and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="a0555-109">`msbuild`コマンドラインで「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a0555-109">Type `msbuild` at the command line.</span></span> <span data-ttu-id="a0555-110">クライアントプログラムファイルが *client\bin* に構築され、サービスプログラムファイルが *service\bin* に構築されます。</span><span class="sxs-lookup"><span data-stu-id="a0555-110">The client program files are built to *client\bin* and the service program files are built to *service\bin*.</span></span> <span data-ttu-id="a0555-111">サービスがインターネットインフォメーションサービス (IIS) によってホストされている場合、サービスプログラムファイルは *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリにもコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a0555-111">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="a0555-112">*%Systemdrive%\inetpub\wwwroot* の acl を設定して、実行しているアカウントに変更のアクセス許可を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-112">You must set the ACLs on *%systemdrive%\inetpub\wwwroot* to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="a0555-113">このように設定しない場合、ビルド後のイベントが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-113">Otherwise some post build events fail.</span></span> <span data-ttu-id="a0555-114">代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0555-114">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>

## <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a0555-115">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="a0555-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="a0555-116">Visual Studio の [**ファイル**] メニューの [   >  **プロジェクト/ソリューション** を開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0555-116">From the **File** menu in Visual Studio, select **Open** > **Project/Solution**.</span></span> <span data-ttu-id="a0555-117">サンプルをインストールしたディレクトリの下にある言語固有のサブディレクトリに移動し、.sln ファイルアイコンをダブルクリックして、Visual Studio でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="a0555-117">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>

1. <span data-ttu-id="a0555-118">[ **ビルド** ] メニューの [ **ソリューションのリビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0555-118">From the **Build** menu, select **Rebuild Solution**.</span></span>

   <span data-ttu-id="a0555-119">クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="a0555-119">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="a0555-120">サービスが IIS でホストされている場合、サービスプログラムファイルは *servicemodelsamples* ディレクトリとその *\bin* サブディレクトリにもコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a0555-120">If the service is hosted in IIS, the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="a0555-121">%systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-121">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="a0555-122">このように設定しない場合、ビルド後のイベントが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-122">Otherwise some post build events fail.</span></span> <span data-ttu-id="a0555-123">代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0555-123">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="a0555-124">一部の Visual Studio アクション (ASP.NET ワーカープロセスへのデバッガーのアタッチなど) にも管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0555-124">Some Visual Studio actions (such as attaching a debugger to the ASP.NET worker process) also require administrative privileges.</span></span>

## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="a0555-125">セットアップ バッチ ファイルとスクリプト</span><span class="sxs-lookup"><span data-stu-id="a0555-125">Setup Batch Files and Scripts</span></span>

 <span data-ttu-id="a0555-126">Setup.exe および Cleanup.exe のバッチファイルとスクリプトは、Visual Studio の開発者コマンドプロンプトから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-126">Setup.exe and Cleanup.exe batch files and scripts should be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="a0555-127">いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-127">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>

## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="a0555-128">メタデータ エンドポイントに関する重要なセキュリティ情報</span><span class="sxs-lookup"><span data-stu-id="a0555-128">Important Security Information about Metadata Endpoints</span></span>

 <span data-ttu-id="a0555-129">機密性の高いサービスメタデータが誤って公開されるのを防ぐために、Windows Communication Foundation (WCF) サービスの既定の構成では、メタデータの公開が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a0555-129">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="a0555-130">この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。</span><span class="sxs-lookup"><span data-stu-id="a0555-130">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="a0555-131">サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。</span><span class="sxs-lookup"><span data-stu-id="a0555-131">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="a0555-132">このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-132">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="a0555-133">サービスメタデータの発行の詳細については、 [メタデータ公開動作](metadata-publishing-behavior.md) のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0555-133">For more information about publishing service metadata, see the [Metadata Publishing Behavior](metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="a0555-134">メタデータエンドポイントをセキュリティで保護するサンプルについては、 [カスタムセキュアメタデータエンドポイント](custom-secure-metadata-endpoint.md) のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0555-134">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>

## <a name="exception-handling"></a><span data-ttu-id="a0555-135">例外処理</span><span class="sxs-lookup"><span data-stu-id="a0555-135">Exception Handling</span></span>

 <span data-ttu-id="a0555-136">通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="a0555-136">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> <span data-ttu-id="a0555-137">例外処理の詳細については、「 [予期される例外](expected-exceptions.md) のサンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0555-137">For more information about exception handling, see the [Expected Exceptions](expected-exceptions.md) sample.</span></span>

## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="a0555-138">Svcutil を使用したクライアントと構成の再生成</span><span class="sxs-lookup"><span data-stu-id="a0555-138">Regenerating Clients and Configuration with Svcutil</span></span>

 <span data-ttu-id="a0555-139">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、ほとんどのサンプルのクライアントコードと構成を再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="a0555-139">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="a0555-140">一部のサンプルでは、構成を手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-140">Some samples require manually edited configuration.</span></span> <span data-ttu-id="a0555-141">たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0555-141">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="a0555-142">一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。</span><span class="sxs-lookup"><span data-stu-id="a0555-142">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>

### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="a0555-143">クライアントと構成ファイルを再生成するには</span><span class="sxs-lookup"><span data-stu-id="a0555-143">To regenerate the client and configuration files</span></span>

1. <span data-ttu-id="a0555-144">SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="a0555-144">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="a0555-145">サービスが Web ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0555-145">If the service is a Web-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="a0555-146">サービスが自己ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0555-146">If the service is a self-hosted type the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="a0555-147">`http://localhost:8000/ServiceModelSamples/service.svc/mex`自己ホスト型サービスの mex エンドポイントのアドレスで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a0555-147">Replace `http://localhost:8000/ServiceModelSamples/service.svc/mex` with the address of the self-hosted service's mex endpoint.</span></span>

     <span data-ttu-id="a0555-148">Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0555-148">To generate the client in a Visual Basic type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     <span data-ttu-id="a0555-149">サービスが自己ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0555-149">If the service is a self-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > <span data-ttu-id="a0555-150">クライアント構成の生成をスキップするには、 **/noConfig** オプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0555-150">To skip the generation of client configuration add the **/noConfig** option.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0555-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0555-151">See also</span></span>

- [<span data-ttu-id="a0555-152">Windows Communication Foundation サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="a0555-152">Running the Windows Communication Foundation Samples</span></span>](running-the-samples.md)
- [<span data-ttu-id="a0555-153">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a0555-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
