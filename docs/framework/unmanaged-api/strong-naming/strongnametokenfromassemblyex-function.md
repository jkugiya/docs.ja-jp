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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636281"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="39643-103">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="39643-103">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="39643-104">指定したアセンブリ ファイルから厳密な名前のトークンが作成され、トークンが表す公開キーが返されます。</span><span class="sxs-lookup"><span data-stu-id="39643-104">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="39643-105">この関数は非推奨とされています。</span><span class="sxs-lookup"><span data-stu-id="39643-105">This function has been deprecated.</span></span> <span data-ttu-id="39643-106">代わりに、[ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="39643-106">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39643-107">構文</span><span class="sxs-lookup"><span data-stu-id="39643-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39643-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39643-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="39643-109">[in] アセンブリの移植可能な実行可能ファイル (PE) のパス。</span><span class="sxs-lookup"><span data-stu-id="39643-109">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="39643-110">[out] 返された厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="39643-110">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="39643-111">[out] 厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="39643-111">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="39643-112">[out] 返された公開キー。</span><span class="sxs-lookup"><span data-stu-id="39643-112">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="39643-113">[out] 公開キーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="39643-113">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39643-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="39643-114">Return Value</span></span>  

 <span data-ttu-id="39643-115">正常に完了した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="39643-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39643-116">解説</span><span class="sxs-lookup"><span data-stu-id="39643-116">Remarks</span></span>  

 <span data-ttu-id="39643-117">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="39643-117">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="39643-118">トークンは、アセンブリの署名に使用される公開キーから作成された 64 ビットのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="39643-118">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="39643-119">トークンはアセンブリの厳密な名前の一部であり、アセンブリ メタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="39643-119">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="39643-120">キーが取得されてトークンが作成されたら、[StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出し、割り当てられてメモリを解放してください。</span><span class="sxs-lookup"><span data-stu-id="39643-120">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="39643-121">`StrongNameTokenFromAssemblyEx` 関数が正常に完了しない場合、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出し、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="39643-121">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39643-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="39643-122">Requirements</span></span>  

 <span data-ttu-id="39643-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39643-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39643-124">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="39643-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39643-125">**ライブラリ:** mscoree.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="39643-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="39643-126">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39643-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39643-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="39643-127">See also</span></span>

- [<span data-ttu-id="39643-128">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="39643-128">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="39643-129">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="39643-129">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="39643-130">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39643-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
