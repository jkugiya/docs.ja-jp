---
title: CorFlags.exe (CorFlags 変換ツール)
description: CorFlags.exe (CorFlags 変換ツール) を理解します。 このツールにより、ポータブル実行可能ファイル イメージのヘッダー内の CorFlags セクションを構成できます。
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 2b801ba28e0513c899123daa98fd649cbc3d9c28
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654168"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="91f0f-104">CorFlags.exe (CorFlags 変換ツール)</span><span class="sxs-lookup"><span data-stu-id="91f0f-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="91f0f-105">CorFlags 変換ツールを使用して、ポータブル実行可能 (PE) ファイル イメージのヘッダー内の CorFlags セクションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="91f0f-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="91f0f-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="91f0f-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="91f0f-107">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="91f0f-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f0f-109">構文</span><span class="sxs-lookup"><span data-stu-id="91f0f-109">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="91f0f-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91f0f-110">Parameters</span></span>  
  
|<span data-ttu-id="91f0f-111">必須パラメーター</span><span class="sxs-lookup"><span data-stu-id="91f0f-111">Required parameter</span></span>|<span data-ttu-id="91f0f-112">説明</span><span class="sxs-lookup"><span data-stu-id="91f0f-112">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="91f0f-113">CorFlags を設定するアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="91f0f-113">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="91f0f-114">オプション</span><span class="sxs-lookup"><span data-stu-id="91f0f-114">Option</span></span>|<span data-ttu-id="91f0f-115">説明</span><span class="sxs-lookup"><span data-stu-id="91f0f-115">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="91f0f-116">32BITREQUIRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-116">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="91f0f-117">32BITREQUIRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="91f0f-117">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="91f0f-118">32BITPREFERRED フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-118">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="91f0f-119">アプリは、64 ビット プラットフォーム上でも 32 ビット プロセスとして実行します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-119">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="91f0f-120">このフラグは、EXE ファイルでのみ設定します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-120">Set this flag only on EXE files.</span></span> <span data-ttu-id="91f0f-121">このフラグを DLL で設定した場合、64 ビット プロセスで DLL を読み込むことができず、<xref:System.BadImageFormatException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="91f0f-121">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="91f0f-122">このフラグを設定した EXE ファイルは、64 ビット プロセスで読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="91f0f-122">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="91f0f-123">.NET Framework 4.5 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="91f0f-123">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="91f0f-124">32BITPREFERRED フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="91f0f-124">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="91f0f-125">.NET Framework 4.5 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="91f0f-125">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="91f0f-126">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-126">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="91f0f-127">厳密な名前が付けられているアセンブリであっても、強制的に更新します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-127">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="91f0f-128">**重要:** 厳密な名前が付けられているアセンブリを更新する場合は、そのコードを実行する前に再署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f0f-128">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="91f0f-129">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-129">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="91f0f-130">ILONLY フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-130">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="91f0f-131">ILONLY フラグをクリアします。</span><span class="sxs-lookup"><span data-stu-id="91f0f-131">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="91f0f-132">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="91f0f-132">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="91f0f-133">CLR ヘッダー バージョンを 2.0 に戻します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-133">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="91f0f-134">CLR ヘッダー バージョンを 2.5 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="91f0f-134">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="91f0f-135">**注:** アセンブリをネイティブに実行するには、CLR ヘッダー バージョン 2.5 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="91f0f-135">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91f0f-136">Remarks</span><span class="sxs-lookup"><span data-stu-id="91f0f-136">Remarks</span></span>  

 <span data-ttu-id="91f0f-137">オプションが何も指定されていない場合、CorFlags 変換ツールは指定されているアセンブリのフラグを表示します。</span><span class="sxs-lookup"><span data-stu-id="91f0f-137">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f0f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="91f0f-138">See also</span></span>

- [<span data-ttu-id="91f0f-139">ツール</span><span class="sxs-lookup"><span data-stu-id="91f0f-139">Tools</span></span>](index.md)
- [<span data-ttu-id="91f0f-140">64 ビット アプリケーション</span><span class="sxs-lookup"><span data-stu-id="91f0f-140">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="91f0f-141">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="91f0f-141">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
