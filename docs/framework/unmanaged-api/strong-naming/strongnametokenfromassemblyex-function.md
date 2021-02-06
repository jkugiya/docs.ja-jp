---
description: '詳細情報: StrongNameTokenFromAssemblyEx 関数'
title: StrongNameTokenFromAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 4ca08c8cfa90415723fc2632e32aa8f45c334db3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636281"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="6fbe6-103">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="6fbe6-103">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="6fbe6-104">指定したアセンブリファイルから厳密な名前トークンを作成し、トークンが表す公開キーを返します。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-104">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="6fbe6-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-105">This function has been deprecated.</span></span> <span data-ttu-id="6fbe6-106">代わりに [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-106">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbe6-107">構文</span><span class="sxs-lookup"><span data-stu-id="6fbe6-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fbe6-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6fbe6-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="6fbe6-109">からアセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-109">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="6fbe6-110">入出力返された厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-110">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="6fbe6-111">入出力厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-111">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="6fbe6-112">入出力返された公開キー。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-112">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="6fbe6-113">入出力公開キーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-113">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fbe6-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6fbe6-114">Return Value</span></span>  

 <span data-ttu-id="6fbe6-115">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fbe6-116">解説</span><span class="sxs-lookup"><span data-stu-id="6fbe6-116">Remarks</span></span>  

 <span data-ttu-id="6fbe6-117">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-117">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="6fbe6-118">トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-118">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="6fbe6-119">トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-119">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="6fbe6-120">キーを取得してトークンを作成したら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-120">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="6fbe6-121">関数が `StrongNameTokenFromAssemblyEx` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-121">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbe6-122">要件</span><span class="sxs-lookup"><span data-stu-id="6fbe6-122">Requirements</span></span>  

 <span data-ttu-id="6fbe6-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fbe6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fbe6-124">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="6fbe6-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6fbe6-125">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6fbe6-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="6fbe6-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fbe6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbe6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fbe6-127">See also</span></span>

- [<span data-ttu-id="6fbe6-128">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6fbe6-128">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="6fbe6-129">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="6fbe6-129">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="6fbe6-130">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6fbe6-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
