---
description: 詳細については、「メッセージキュー経由のメッセージセキュリティ」を参照してください。
title: メッセージ キューを介したメッセージ セキュリティ
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: bfbec02dec11d4f4eb153db942eb12ce4cb595e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752328"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="3e58c-103">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3e58c-103">Message Security over Message Queuing</span></span>

<span data-ttu-id="3e58c-104">このサンプルでは、クライアントの認証で X.509v3 証明書による WS-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509v3 証明書を MSMQ 経由で使用するサーバー認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="3e58c-104">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="3e58c-105">MSMQ ストア内のメッセージの暗号化を保持したり、アプリケーションで独自のメッセージ認証を実行できるようにするには、メッセージ セキュリティの使用が望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-105">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="3e58c-106">このサンプルは、トランザクション処理された [MSMQ バインディング](transacted-msmq-binding.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="3e58c-106">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="3e58c-107">メッセージは暗号化されて署名されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-107">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e58c-108">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3e58c-108">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3e58c-109">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-109">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3e58c-110">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-110">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3e58c-111">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-111">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3e58c-112">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-112">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3e58c-113">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3e58c-113">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="3e58c-114">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-114">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="3e58c-115">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-115">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="3e58c-116">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-116">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="3e58c-117">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-117">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="3e58c-118">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-118">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="3e58c-119">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3e58c-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="3e58c-120">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="3e58c-120">To run the sample on the same computer</span></span>

1. <span data-ttu-id="3e58c-121">Makecert.exe と FindPrivateKey.exe を格納するフォルダーがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-121">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="3e58c-122">Setup.bat をサンプルのインストール フォルダーで実行します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-122">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="3e58c-123">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-123">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3e58c-124">サンプルの実行後は、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-124">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="3e58c-125">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-125">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="3e58c-126">Service.exe を \service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-126">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="3e58c-127">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-127">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="3e58c-128">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-128">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="3e58c-129">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-129">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3e58c-130">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="3e58c-130">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="3e58c-131">Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルをサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-131">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="3e58c-132">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-132">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="3e58c-133">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-133">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="3e58c-134">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-134">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="3e58c-135">サーバーで `setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-135">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="3e58c-136">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-136">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="3e58c-137">サービスの service.exe.config を編集して、新しい証明書名 ( `findValue` の属性) を反映し [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ます。これは、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="3e58c-137">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="3e58c-138">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-138">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="3e58c-139">クライアントで `setup.bat client` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-139">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="3e58c-140">`setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-140">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="3e58c-141">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-141">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="3e58c-142">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-142">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="3e58c-143">さらに、サービス証明書の名前を、サービス コンピューターの完全修飾ドメイン名 (`findValue` の下にある `defaultCertificate` の `serviceCertificate` 要素の `clientCredentials` 属性) と同じ名前に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-143">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="3e58c-144">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-144">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="3e58c-145">クライアントで `ImportServiceCert.bat` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-145">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="3e58c-146">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-146">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="3e58c-147">サーバーで `ImportClientCert.bat` を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-147">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="3e58c-148">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-148">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="3e58c-149">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-149">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="3e58c-150">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-150">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3e58c-151">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="3e58c-151">To clean up after the sample</span></span>  
  
- <span data-ttu-id="3e58c-152">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-152">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3e58c-153">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="3e58c-153">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="3e58c-154">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-154">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3e58c-155">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-155">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e58c-156">要件</span><span class="sxs-lookup"><span data-stu-id="3e58c-156">Requirements</span></span>

 <span data-ttu-id="3e58c-157">このサンプルでは、MSMQ がインストールされて実行中であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3e58c-157">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3e58c-158">対象</span><span class="sxs-lookup"><span data-stu-id="3e58c-158">Demonstrates</span></span>

 <span data-ttu-id="3e58c-159">クライアントは、サービスの公開キーを使用してメッセージを暗号化し、独自の証明書を使用してメッセージ署名を行います。</span><span class="sxs-lookup"><span data-stu-id="3e58c-159">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="3e58c-160">キューからのメッセージを読み込むサービスは、信頼されたユーザーのストア内の証明書を使用して、クライアント証明書を認証します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-160">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="3e58c-161">次にメッセージを復号化し、サービス操作にディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-161">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="3e58c-162">Windows Communication Foundation (WCF) メッセージは MSMQ メッセージの本文のペイロードとして転送されるため、本文は MSMQ ストアで暗号化されたままになります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-162">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="3e58c-163">これによりメッセージは、望ましくない公開から保護されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-163">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="3e58c-164">MSMQ 自体では、送信されるメッセージが暗号化されているかどうかは認識されません。</span><span class="sxs-lookup"><span data-stu-id="3e58c-164">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="3e58c-165">このサンプルは、MSMQ でメッセージ レベルの相互認証を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-165">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="3e58c-166">証明書は、帯域外で交換されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-166">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="3e58c-167">サービスとクライアントは同時に実行される必要がないため、キューに置かれたアプリケーションでは常にその状態です。</span><span class="sxs-lookup"><span data-stu-id="3e58c-167">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="3e58c-168">説明</span><span class="sxs-lookup"><span data-stu-id="3e58c-168">Description</span></span>

 <span data-ttu-id="3e58c-169">サンプルクライアントとサービスコードは、 [トランザクション MSMQ バインディング](transacted-msmq-binding.md) サンプルと同じであり、1つの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-169">The sample client and service code are the same as the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="3e58c-170">操作コントラクトには、メッセージの署名および暗号化が必要であることを示す注釈が保護レベルで付けられます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-170">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="3e58c-171">メッセージが、サービスとクライアントの識別に必要なトークンを使用してセキュリティ保護されるには、App.config に資格情報を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-171">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="3e58c-172">クライアント構成では、サービスを認証するサービス証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-172">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="3e58c-173">また、LocalMachine のストアを信頼されるストアとして使用し、サービスの有効性を信頼します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-173">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="3e58c-174">さらに、クライアントのサービス認証用として、メッセージに関連付けられたクライアント証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-174">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="3e58c-175">セキュリティ モードが Message に設定されている場合は、ClientCredentialType は Certificate に設定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-175">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="3e58c-176">サービス構成には、サービスの資格情報を指定するサービス動作が含まれます。この資格情報は、クライアントがサービスを認証する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-176">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="3e58c-177">サーバー証明書のサブジェクト名は、の属性で指定され `findValue` [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) ます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-177">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="3e58c-178">このサンプルは、構成を使用した認証の制御、およびセキュリティ コンテキストから呼び出し側の ID を取得する方法を示しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-178">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="3e58c-179">実行時、サービス コードにはクライアント ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-179">When run, the service code displays the client identification.</span></span> <span data-ttu-id="3e58c-180">サービス コードからの出力サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-180">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="3e58c-181">コメント</span><span class="sxs-lookup"><span data-stu-id="3e58c-181">Comments</span></span>

- <span data-ttu-id="3e58c-182">クライアント証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="3e58c-182">Creating the client certificate.</span></span>

     <span data-ttu-id="3e58c-183">バッチ ファイルの次の行では、クライアント証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-183">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="3e58c-184">指定されたクライアント名が、作成される証明書のサブジェクト名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-184">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="3e58c-185">証明書は、`My` ストアの場所の `CurrentUser` ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-185">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="3e58c-186">クライアント証明書のサーバーの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="3e58c-186">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="3e58c-187">バッチ ファイルの次の行では、クライアント証明書をサーバーの TrustedPeople ストアにコピーし、サーバーが信頼/非信頼を判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-187">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="3e58c-188">TrustedPeople ストアにインストールされている証明書が Windows Communication Foundation (WCF) サービスによって信頼されるようにするには、クライアント証明書検証モードをまたは値に設定する必要があり `PeerOrChainTrust` `PeerTrust` ます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-188">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="3e58c-189">前のサービス構成サンプルを参照して、構成ファイルを使用してこれを行う手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-189">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="3e58c-190">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="3e58c-190">Creating the server certificate.</span></span>

     <span data-ttu-id="3e58c-191">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-191">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="3e58c-192">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="3e58c-192">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="3e58c-193">証明書は LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-193">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="3e58c-194">セットアップバッチファイルの実行にサービスの引数 (など) が指定されている場合、 `setup.bat service` % SERVER_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。それ以外の場合、既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="3e58c-194">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="3e58c-195">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="3e58c-195">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="3e58c-196">次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e58c-196">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="3e58c-197">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="3e58c-197">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="3e58c-198">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="3e58c-198">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="3e58c-199">英語 (米国) 以外の言語で Microsoft Windows を使用している場合は、Setup.bat ファイルを編集し、"NT AUTHORITY\NETWORK SERVICE" アカウント名を現在の地域に適した名前に変更してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-199">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e58c-200">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e58c-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3e58c-201">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3e58c-202">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3e58c-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e58c-203">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e58c-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`
