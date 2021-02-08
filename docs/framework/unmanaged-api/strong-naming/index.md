---
description: '詳細情報: 厳密な名前付け (アンマネージ API リファレンス)'
title: 厳密な名前付け (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 058cc51d8e9eb2ef4a2d0670811aefcd32dafb6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646362"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="edd2e-103">厳密な名前付け (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="edd2e-103">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="edd2e-104">厳密な名前付け API を使用すると、アセンブリに対する厳密な名前の署名をクライアントで管理できます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-104">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="edd2e-105">厳密な名前を使用してアセンブリに署名すると、アセンブリ マニフェストを格納しているファイルに公開キー暗号化が追加されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-105">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="edd2e-106">厳密な名前による署名では、名前の一意性の検証を支援し、名前の悪用を防止し、参照が解決されたときに呼び出し元に一意の ID を提供できます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-106">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="edd2e-107">しかし、厳密な名前に信頼性のレベルは関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="edd2e-107">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="edd2e-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="edd2e-108">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edd2e-109">.NET Framework 4 以降、これらの関数すべてが非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="edd2e-109">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="edd2e-110">推奨されている代わりの関数については、[ICLRStrongName](../hosting/iclrstrongname-interface.md) インターフェイスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="edd2e-110">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="edd2e-111">GetHashFromAssemblyFile 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-111">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="edd2e-112">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-112">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="edd2e-113">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-113">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-114">GetHashFromAssemblyFileW 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-114">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="edd2e-115">指定したハッシュ アルゴリズムを使用して、Unicode 文字列として指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-115">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="edd2e-116">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-116">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-117">GetHashFromBlob 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-117">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="edd2e-118">指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-118">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="edd2e-119">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-119">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-120">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-120">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="edd2e-121">指定したファイルの内容に対してハッシュが生成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-121">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="edd2e-122">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-122">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-123">GetHashFromFileW 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-123">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="edd2e-124">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-124">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="edd2e-125">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-125">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-126">GetHashFromHandle 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-126">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="edd2e-127">指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを含むファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-127">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="edd2e-128">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-128">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-129">StrongNameCompareAssemblies 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-129">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="edd2e-130">厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-130">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="edd2e-131">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-131">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-132">StrongNameErrorInfo 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-132">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="edd2e-133">厳密な名前の関数のいずれかに基づいて最後に発生したエラー コードが取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-133">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="edd2e-134">StrongNameFreeBuffer 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-134">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="edd2e-135">[StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md) などの厳密な名前の関数に対する前の呼び出しで割り当てられたメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-135">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="edd2e-136">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-136">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-137">StrongNameGetBlob 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-137">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="edd2e-138">指定したアドレスにある実行可能ファイルのバイナリ表現が、指定したバッファーに入れられます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-138">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="edd2e-139">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-139">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-140">StrongNameGetBlobFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-140">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="edd2e-141">指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-141">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="edd2e-142">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-142">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-143">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-143">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="edd2e-144">秘密/公開キーの組から公開キーが取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-144">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="edd2e-145">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-145">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-146">StrongNameHashSize 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-146">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="edd2e-147">指定したハッシュ アルゴリズムを使用して、ハッシュに必須のバッファー サイズが取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-147">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="edd2e-148">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-148">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-149">StrongNameKeyDelete 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-149">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="edd2e-150">指定したキー コンテナーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-150">Deletes the specified key container.</span></span> <span data-ttu-id="edd2e-151">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-151">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-152">StrongNameKeyGen 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-152">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="edd2e-153">厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-153">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="edd2e-154">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-154">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-155">StrongNameKeyGenEx 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-155">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="edd2e-156">厳密な名前を使用するために、指定したキー サイズによって新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-156">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="edd2e-157">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-157">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-158">StrongNameKeyInstall 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-158">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="edd2e-159">公開/秘密キーの組がコンテナーにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-159">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="edd2e-160">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-160">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-161">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-161">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="edd2e-162">指定したアセンブリに対して厳密な名前の署名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-162">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="edd2e-163">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-163">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-164">StrongNameSignatureGenerationEx 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-164">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="edd2e-165">指定したフラグに基づいて、指定したアセンブリに対する厳密な名前の署名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-165">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="edd2e-166">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-166">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-167">StrongNameSignatureSize 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-167">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="edd2e-168">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-168">Returns the size of the strong name signature.</span></span> <span data-ttu-id="edd2e-169">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-169">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-170">StrongNameSignatureVerification 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-170">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="edd2e-171">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-171">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="edd2e-172">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-172">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-173">StrongNameSignatureVerificationEx 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-173">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="edd2e-174">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-174">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="edd2e-175">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-175">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-176">StrongNameSignatureVerificationFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-176">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="edd2e-177">メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-177">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="edd2e-178">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-178">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-179">StrongNameTokenFromAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-179">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="edd2e-180">指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-180">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="edd2e-181">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-181">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-182">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-182">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="edd2e-183">指定したアセンブリ ファイルから厳密な名前のトークンが作成され、公開キーが返されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-183">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="edd2e-184">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-184">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-185">StrongNameTokenFromPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="edd2e-185">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="edd2e-186">公開キーを表すトークンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-186">Gets a token representing a public key.</span></span> <span data-ttu-id="edd2e-187">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-187">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="edd2e-188">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="edd2e-188">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="edd2e-189">公開/秘密キーの組の公開キーがバイナリ形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="edd2e-189">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd2e-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="edd2e-190">See also</span></span>

- [<span data-ttu-id="edd2e-191">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="edd2e-191">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="edd2e-192">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="edd2e-192">Unmanaged API Reference</span></span>](../index.md)
