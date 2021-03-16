---
title: Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)
description: "Cert2spc.exe (ソフトウェア発行元証明書テスト ツール) を使用します。 このツールによって、1 つまたは複数の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) が作成されます。"
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 96b4c05f6c9af6fc78aa55b248a88de84e2d4ac8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258282"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="30e8b-104">Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)</span><span class="sxs-lookup"><span data-stu-id="30e8b-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>

<span data-ttu-id="30e8b-105">ソフトウェア発行元証明書テスト ツールは、1 つ以上の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) を作成します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="30e8b-106">Cert2spc.exe はテスト専用のツールです。</span><span class="sxs-lookup"><span data-stu-id="30e8b-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="30e8b-107">有効な SPC は、VeriSign や Thawte などの証明書発行機関から入手できます。</span><span class="sxs-lookup"><span data-stu-id="30e8b-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="30e8b-108">X.509 証明書の作成の詳細については、「[Makecert.exe (証明書作成ツール)](/windows/desktop/SecCrypto/makecert)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30e8b-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="30e8b-109">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="30e8b-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="30e8b-110">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-110">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="30e8b-111">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e8b-112">構文</span><span class="sxs-lookup"><span data-stu-id="30e8b-112">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="30e8b-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30e8b-113">Parameters</span></span>  
  
|<span data-ttu-id="30e8b-114">引数</span><span class="sxs-lookup"><span data-stu-id="30e8b-114">Argument</span></span>|<span data-ttu-id="30e8b-115">説明</span><span class="sxs-lookup"><span data-stu-id="30e8b-115">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="30e8b-116">SPC ファイルに組み込む X.509 証明書の名前。</span><span class="sxs-lookup"><span data-stu-id="30e8b-116">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="30e8b-117">スペースで区切ることによって、複数の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30e8b-117">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="30e8b-118">SPC ファイルに組み込む証明書失効リストの名前。</span><span class="sxs-lookup"><span data-stu-id="30e8b-118">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="30e8b-119">スペースで区切ることによって、複数の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30e8b-119">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="30e8b-120">X.509 証明書が格納される PKCS #7 オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="30e8b-120">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="30e8b-121">オプション</span><span class="sxs-lookup"><span data-stu-id="30e8b-121">Option</span></span>|<span data-ttu-id="30e8b-122">説明</span><span class="sxs-lookup"><span data-stu-id="30e8b-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="30e8b-123">**/?**</span><span class="sxs-lookup"><span data-stu-id="30e8b-123">**/?**</span></span>|<span data-ttu-id="30e8b-124">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-124">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="30e8b-125">使用例</span><span class="sxs-lookup"><span data-stu-id="30e8b-125">Examples</span></span>  

 <span data-ttu-id="30e8b-126">`myCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-126">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="30e8b-127">`oneCertificate.cer` と `twoCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30e8b-127">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="30e8b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="30e8b-128">See also</span></span>

- [<span data-ttu-id="30e8b-129">ツール</span><span class="sxs-lookup"><span data-stu-id="30e8b-129">Tools</span></span>](index.md)
- [<span data-ttu-id="30e8b-130">Makecert.exe (証明書作成ツール)</span><span class="sxs-lookup"><span data-stu-id="30e8b-130">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="30e8b-131">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="30e8b-131">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
