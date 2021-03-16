---
title: Certmgr.exe (証明書マネージャー ツール)
description: 証明書マネージャー ツール Certmgr.exe について確認します。 このツールによって、証明書、証明書信頼リスト (CTL)、および証明書失効リスト (CRL) が管理されています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: a5666645c674bbbe77b988fc7a1ff0db935920aa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258235"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="4c224-104">Certmgr.exe (証明書マネージャー ツール)</span><span class="sxs-lookup"><span data-stu-id="4c224-104">Certmgr.exe (Certificate Manager Tool)</span></span>

<span data-ttu-id="4c224-105">証明書マネージャー ツール (Certmgr.exe) は、証明書、証明書信頼リスト (CTL: Certificate Trust List)、および証明書失効リスト (CRL: Certificate Revocation List) を管理します。</span><span class="sxs-lookup"><span data-stu-id="4c224-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="4c224-106">証明書マネージャーは Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4c224-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4c224-107">ツールを起動するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c224-107">To start the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c224-108">証明書マネージャー ツール (Certmgr.exe) はコマンド ライン ユーティリティですが、証明書 (Certmgr.msc) は Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインです。</span><span class="sxs-lookup"><span data-stu-id="4c224-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="4c224-109">通常、Certmgr.msc は Windows のシステム ディレクトリにあるので、コマンド ラインで「`certmgr`」と入力すると、Visual Studio 用開発者コマンド プロンプトを開いていた場合でも証明書 MMC スナップインが読み込まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c224-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="4c224-110">これは、PATH 環境変数で、スナップインのパスが証明書マネージャー ツールのパスよりも前に指定されているためです。</span><span class="sxs-lookup"><span data-stu-id="4c224-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="4c224-111">この問題が発生した場合は、実行可能ファイルのパスを指定して Certmgr.exe コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4c224-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="4c224-112">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4c224-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4c224-113">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c224-113">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="4c224-114">X.509 証明書の概要については、「[証明書の使用](../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c224-114">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="4c224-115">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="4c224-115">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c224-116">構文</span><span class="sxs-lookup"><span data-stu-id="4c224-116">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c224-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c224-117">Parameters</span></span>  
  
|<span data-ttu-id="4c224-118">引数</span><span class="sxs-lookup"><span data-stu-id="4c224-118">Argument</span></span>|<span data-ttu-id="4c224-119">説明</span><span class="sxs-lookup"><span data-stu-id="4c224-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4c224-120">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="4c224-120">*sourceStorename*</span></span>|<span data-ttu-id="4c224-121">追加、削除、保存、または表示する既存の証明書、CTL、または CRL を含む証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="4c224-121">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="4c224-122">ストア ファイルまたはシステム ストアを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4c224-122">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="4c224-123">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="4c224-123">*destinationStorename*</span></span>|<span data-ttu-id="4c224-124">出力証明書ストアまたはファイル。</span><span class="sxs-lookup"><span data-stu-id="4c224-124">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="4c224-125">オプション</span><span class="sxs-lookup"><span data-stu-id="4c224-125">Option</span></span>|<span data-ttu-id="4c224-126">説明</span><span class="sxs-lookup"><span data-stu-id="4c224-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4c224-127">**/add**</span><span class="sxs-lookup"><span data-stu-id="4c224-127">**/add**</span></span>|<span data-ttu-id="4c224-128">証明書、CTL、および CRL を証明書ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-128">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="4c224-129">**/all**</span><span class="sxs-lookup"><span data-stu-id="4c224-129">**/all**</span></span>|<span data-ttu-id="4c224-130">**/add** を指定して使用した場合は、すべてのエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-130">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="4c224-131">**/del** を指定して使用した場合は、すべてのエントリを削除します。 **/add**、 **/del** のいずれのオプションも指定せずに使用した場合は、すべてのエントリを表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-131">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="4c224-132">**/all** オプションは、 **/put** オプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="4c224-132">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="4c224-133">**/c**</span><span class="sxs-lookup"><span data-stu-id="4c224-133">**/c**</span></span>|<span data-ttu-id="4c224-134">**/add** を指定して使用した場合は、証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-134">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="4c224-135">**/del** を指定して使用した場合は、証明書を削除します。 **/put** を指定して使用した場合は、証明書を保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-135">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="4c224-136">**/add**、 **/del**、 **/put** のいずれのオプションも指定せずに使用した場合は、証明書を表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-136">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="4c224-137">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="4c224-137">**/CRL**</span></span>|<span data-ttu-id="4c224-138">**/add** を指定して使用した場合は、CRL を追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-138">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="4c224-139">**/del** を指定して使用した場合は、CRL を削除します。 **/put** を指定して使用した場合は、CRL を保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-139">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="4c224-140">**/add**、 **/del**、 **/put** のいずれのオプションも指定せずに使用した場合は、CRL を表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-140">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="4c224-141">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="4c224-141">**/CTL**</span></span>|<span data-ttu-id="4c224-142">**/add** を指定して使用した場合は、CTL を追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-142">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="4c224-143">**/del** を指定して使用した場合は、CTL を削除します。 **/put** を指定して使用した場合は、CTL を保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-143">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="4c224-144">**/add**、 **/del**、 **/put** のいずれのオプションも指定せずに使用した場合は、CTL を表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-144">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="4c224-145">**/del**</span><span class="sxs-lookup"><span data-stu-id="4c224-145">**/del**</span></span>|<span data-ttu-id="4c224-146">証明書、CTL、および CRL を証明書ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="4c224-146">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="4c224-147">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="4c224-147">**/e** *encodingType*</span></span>|<span data-ttu-id="4c224-148">証明書のエンコード タイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-148">Specifies the certificate encoding type.</span></span> <span data-ttu-id="4c224-149">既定値は、`X509_ASN_ENCODING` です。</span><span class="sxs-lookup"><span data-stu-id="4c224-149">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="4c224-150">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="4c224-150">**/f** *dwFlags*</span></span>|<span data-ttu-id="4c224-151">ストア オープン フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-151">Specifies the store open flag.</span></span> <span data-ttu-id="4c224-152">これは **CertOpenStore** に渡される *dwFlags* パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4c224-152">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="4c224-153">既定値は CERT_SYSTEM_STORE_CURRENT_USER です。</span><span class="sxs-lookup"><span data-stu-id="4c224-153">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="4c224-154">このオプションは **/y** オプションを使用した場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="4c224-154">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="4c224-155">**/h** **[elp]**</span><span class="sxs-lookup"><span data-stu-id="4c224-155">**/h**[**elp**]</span></span>|<span data-ttu-id="4c224-156">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-156">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="4c224-157">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="4c224-157">**/n** *nam*</span></span>|<span data-ttu-id="4c224-158">追加、削除、または保存する証明書の共通名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-158">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="4c224-159">このオプションは証明書についてだけ使用できます。CTL または CRL については使用できません。</span><span class="sxs-lookup"><span data-stu-id="4c224-159">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="4c224-160">**/put**</span><span class="sxs-lookup"><span data-stu-id="4c224-160">**/put**</span></span>|<span data-ttu-id="4c224-161">証明書ストアに含まれている X.509 証明書、CTL、または CRL をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-161">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="4c224-162">ファイルは X.509 形式で保存されます。</span><span class="sxs-lookup"><span data-stu-id="4c224-162">The file is saved in X.509 format.</span></span> <span data-ttu-id="4c224-163">**/7** オプションを **/put** オプションと一緒に使用すると、ファイルを PKCS #7 形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="4c224-163">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="4c224-164">**/put** オプションの後ろには、 **/c**、 **/CTL**、 **/CRL** のいずれかのオプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c224-164">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="4c224-165">**/all** オプションは、 **/put** オプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="4c224-165">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="4c224-166">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="4c224-166">**/r** *location*</span></span>|<span data-ttu-id="4c224-167">システム ストアのレジストリの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-167">Identifies the registry location of the system store.</span></span> <span data-ttu-id="4c224-168">このオプションは、 **/s** オプションを指定した場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="4c224-168">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="4c224-169">*location* には、次のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c224-169">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="4c224-170">-   証明書ストアが HKEY_CURRENT_USER キーに含まれる場合は `currentUser` を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-170">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="4c224-171">既定値です。</span><span class="sxs-lookup"><span data-stu-id="4c224-171">This is the default.</span></span><br /><span data-ttu-id="4c224-172">-   証明書ストアが HKEY_LOCAL_MACHINE キーに含まれる場合は `localMachine` を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-172">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="4c224-173">**/s**</span><span class="sxs-lookup"><span data-stu-id="4c224-173">**/s**</span></span>|<span data-ttu-id="4c224-174">証明書ストアがシステム ストアであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-174">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="4c224-175">このオプションを指定しない場合、ストアは **StoreFile** と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4c224-175">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="4c224-176">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="4c224-176">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="4c224-177">追加、削除、または保存する証明書、CTL、または CRL の SHA1 ハッシュを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-177">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="4c224-178">**/v**</span><span class="sxs-lookup"><span data-stu-id="4c224-178">**/v**</span></span>|<span data-ttu-id="4c224-179">詳細出力モードを指定します。このモードでは、証明書、CTL、および CRL に関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c224-179">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="4c224-180">このオプションは、 **/add**、 **/del**、または **/put** のオプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="4c224-180">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="4c224-181">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="4c224-181">**/y** *provider*</span></span>|<span data-ttu-id="4c224-182">ストア プロバイダー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c224-182">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="4c224-183">**/7**</span><span class="sxs-lookup"><span data-stu-id="4c224-183">**/7**</span></span>|<span data-ttu-id="4c224-184">出力証明書ストアを PKCS #7 オブジェクトとして保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-184">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="4c224-185">**/?**</span><span class="sxs-lookup"><span data-stu-id="4c224-185">**/?**</span></span>|<span data-ttu-id="4c224-186">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-186">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c224-187">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c224-187">Remarks</span></span>  

 <span data-ttu-id="4c224-188">Certmgr.exe は次の基本的な機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="4c224-188">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="4c224-189">証明書、CTL、および CRL をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-189">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="4c224-190">証明書、CTL、および CRL を証明書ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="4c224-190">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="4c224-191">証明書、CTL、および CRL を証明書ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="4c224-191">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="4c224-192">証明書ストアに含まれている X.509 証明書、CTL、または CRL をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="4c224-192">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="4c224-193">Certmgr.exe は、**StoreFile** とシステム ストアという 2 つの種類の証明書ストアに対して機能します。</span><span class="sxs-lookup"><span data-stu-id="4c224-193">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="4c224-194">証明書ストアの種類を指定する必要はありません。Certmgr.exe がストアの種類を識別し、適切な操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="4c224-194">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="4c224-195">オプションを何も指定せずに Certmgr.exe を実行すると、証明書の管理タスクの実行時に役立つ GUI を備えた certmgr.msc スナップインが起動します。これらのタスクはコマンド ラインでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="4c224-195">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="4c224-196">この GUI には、証明書、CTL、および CRL をディスクから証明書ストアへとコピーする、インポート ウィザードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4c224-196">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="4c224-197">次のコードをコンパイルおよび実行することによって、`sourceStorename` パラメーターおよび `destinationStorename` パラメーターについて X509Certificate ストアの名前を検索できます。</span><span class="sxs-lookup"><span data-stu-id="4c224-197">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="4c224-198">証明書の詳細については、「[証明書の使用](../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c224-198">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4c224-199">使用例</span><span class="sxs-lookup"><span data-stu-id="4c224-199">Examples</span></span>  

 <span data-ttu-id="4c224-200">既定のシステム ストアである `my` を詳細出力モードで表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-200">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="4c224-201">`myFile.ext` という名前のファイルに含まれるすべての証明書を `newFile.ext` という名前の新しいファイルに追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-201">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="4c224-202">`testcert.cer` という名前のファイルに含まれる証明書をシステム ストア `my` に追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-202">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="4c224-203">`TrustedCert.cer` という名前のファイルに含まれる証明書をルート証明書ストアに追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-203">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="4c224-204">システム ストア `myCert` に含まれていて共通名が `my` の証明書を `newCert.cer` という名前のファイルに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-204">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="4c224-205">システム ストア `my` に含まれるすべての CTL を削除し、その結果得られるストアを `newStore.str` という名前のファイルに格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-205">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="4c224-206">システム ストア `my` に含まれる証明書をファイル `newFile` に保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c224-206">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="4c224-207">`my` から `newFile` に保存する証明書の番号を入力するためのプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c224-207">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c224-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c224-208">See also</span></span>

- [<span data-ttu-id="4c224-209">ツール</span><span class="sxs-lookup"><span data-stu-id="4c224-209">Tools</span></span>](index.md)
- [<span data-ttu-id="4c224-210">Makecert.exe (証明書作成ツール)</span><span class="sxs-lookup"><span data-stu-id="4c224-210">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="4c224-211">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="4c224-211">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
