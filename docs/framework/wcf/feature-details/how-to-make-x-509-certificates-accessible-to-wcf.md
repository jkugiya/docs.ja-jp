---
title: '方法: X.509 証明書を WCF からアクセス可能にする'
description: X.509 証明書を WCF からアクセス可能にする方法について説明します。 アプリケーション コードでは、証明書ストアの名前と場所を指定する必要があります。 他の要件がある可能性もあります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 06a6167f0ad352955eb6b764ef8bfdb1394f4ed9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279741"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="7c68e-105">方法: X.509 証明書を WCF からアクセス可能にする</span><span class="sxs-lookup"><span data-stu-id="7c68e-105">How to: Make X.509 Certificates Accessible to WCF</span></span>

<span data-ttu-id="7c68e-106">Windows Communication Foundation (WCF) から X.509 証明書にアクセスできるようにするには、アプリケーション コードで証明書ストアの名前と場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c68e-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="7c68e-107">特定の状況では、X.509 証明書に関連付けられた秘密キーを格納しているファイルにプロセス ID がアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c68e-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="7c68e-108">証明書ストア内の X.509 証明書に関連付けられている秘密キーを取得するには、それを行うためのアクセス許可が WCF に必要になります。</span><span class="sxs-lookup"><span data-stu-id="7c68e-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="7c68e-109">既定では、所有者と System アカウントだけが証明書の秘密キーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="7c68e-110">X.509 証明書を WCF からアクセス可能にするには</span><span class="sxs-lookup"><span data-stu-id="7c68e-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="7c68e-111">WCF が実行されているアカウントに対して、X.509 証明書に関連付けられている秘密キーを格納しているファイルへの読み取りアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="7c68e-112">WCF に X.509 証明書の秘密キーへの読み取りアクセス権が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="7c68e-113">次の表は、X.509 証明書を使用する際に秘密キーを使用できる必要があるかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="7c68e-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="7c68e-114">X.509 証明書の使用法</span><span class="sxs-lookup"><span data-stu-id="7c68e-114">X.509 certificate use</span></span>|<span data-ttu-id="7c68e-115">秘密キー</span><span class="sxs-lookup"><span data-stu-id="7c68e-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="7c68e-116">送信 SOAP メッセージにデジタル署名する。</span><span class="sxs-lookup"><span data-stu-id="7c68e-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="7c68e-117">はい</span><span class="sxs-lookup"><span data-stu-id="7c68e-117">Yes</span></span>|  
        |<span data-ttu-id="7c68e-118">受信 SOAP メッセージの署名を検証する。</span><span class="sxs-lookup"><span data-stu-id="7c68e-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="7c68e-119">いいえ</span><span class="sxs-lookup"><span data-stu-id="7c68e-119">No</span></span>|  
        |<span data-ttu-id="7c68e-120">送信 SOAP メッセージを暗号化する。</span><span class="sxs-lookup"><span data-stu-id="7c68e-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="7c68e-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="7c68e-121">No</span></span>|  
        |<span data-ttu-id="7c68e-122">受信 SOAP メッセージを復号化する。</span><span class="sxs-lookup"><span data-stu-id="7c68e-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="7c68e-123">はい</span><span class="sxs-lookup"><span data-stu-id="7c68e-123">Yes</span></span>|  
  
    2. <span data-ttu-id="7c68e-124">証明書が格納されている証明書ストアの場所と名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="7c68e-125">証明書が格納されている証明書ストアは、アプリケーション コードまたは構成で指定します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="7c68e-126">たとえば、次の例では、証明書が `CurrentUser` という名前の `My` 証明書ストア内に存在することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="7c68e-127">[FindPrivateKey](../samples/findprivatekey.md) ツールを使用して、証明書の秘密キーがコンピューター上のどこに存在するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="7c68e-128">[FindPrivateKey](../samples/findprivatekey.md) ツールには、証明書ストアの名前、証明書ストアの場所、および証明書を一意に識別する情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c68e-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="7c68e-129">このツールは、証明書のサブジェクト名または拇印を一意の識別子として受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="7c68e-130">証明書の拇印を確認する方法の詳細については、「[方法: 証明書のサムプリントを取得する](how-to-retrieve-the-thumbprint-of-a-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c68e-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="7c68e-131">次のコード例では、[FindPrivateKey](../samples/findprivatekey.md) ツールを使用して、`CurrentUser` の `My` ストア内に存在する、拇印 `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` を持つ証明書の秘密キーの場所を特定します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="7c68e-132">WCF が実行されているアカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c68e-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="7c68e-133">次の表は、特定のシナリオで WCF が実行されているアカウントの詳細を示しています。</span><span class="sxs-lookup"><span data-stu-id="7c68e-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="7c68e-134">シナリオ</span><span class="sxs-lookup"><span data-stu-id="7c68e-134">Scenario</span></span>|<span data-ttu-id="7c68e-135">プロセス ID</span><span class="sxs-lookup"><span data-stu-id="7c68e-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="7c68e-136">クライアント (コンソールまたは WinForms アプリケーション)</span><span class="sxs-lookup"><span data-stu-id="7c68e-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="7c68e-137">現在ログインしているユーザー</span><span class="sxs-lookup"><span data-stu-id="7c68e-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="7c68e-138">自己ホスト型のサービス</span><span class="sxs-lookup"><span data-stu-id="7c68e-138">Service that is self-hosted.</span></span>|<span data-ttu-id="7c68e-139">現在ログインしているユーザー</span><span class="sxs-lookup"><span data-stu-id="7c68e-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="7c68e-140">IIS 6.0 (Windows Server 2003) または IIS 7.0 (Windows Vista) でホストされているサービス。</span><span class="sxs-lookup"><span data-stu-id="7c68e-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="7c68e-141">NETWORK SERVICE</span><span class="sxs-lookup"><span data-stu-id="7c68e-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="7c68e-142">IIS 5.X (Windows XP) でホストされているサービス。</span><span class="sxs-lookup"><span data-stu-id="7c68e-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="7c68e-143">Machine.config ファイル内の `<processModel>` 要素によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="7c68e-144">既定のアカウントは ASPNET です。</span><span class="sxs-lookup"><span data-stu-id="7c68e-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="7c68e-145">icacls.exe などのツールを使用して、WCF が実行されているアカウントに、秘密キーを格納しているファイルへの読み取りアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="7c68e-146">次のコード例では、指定したファイルの随意アクセス制御リスト (DACL) を編集して、NETWORK SERVICE アカウントにそのファイルへの読み取り (:R) アクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="7c68e-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="7c68e-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c68e-147">See also</span></span>

- [<span data-ttu-id="7c68e-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="7c68e-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="7c68e-149">方法: 証明書のサムプリントを取得する</span><span class="sxs-lookup"><span data-stu-id="7c68e-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="7c68e-150">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="7c68e-150">Working with Certificates</span></span>](working-with-certificates.md)
