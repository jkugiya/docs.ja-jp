---
description: '詳細情報: StrongNameSignatureVerificationEx 関数'
title: StrongNameSignatureVerificationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: 9e20044e9c3caef8c2276ac5f390269ee978d55b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794534"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="2ae26-103">StrongNameSignatureVerificationEx 関数</span><span class="sxs-lookup"><span data-stu-id="2ae26-103">StrongNameSignatureVerificationEx Function</span></span>

<span data-ttu-id="2ae26-104">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="2ae26-104">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="2ae26-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="2ae26-105">This function has been deprecated.</span></span> <span data-ttu-id="2ae26-106">代わりに [ICLRStrongName:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="2ae26-106">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae26-107">構文</span><span class="sxs-lookup"><span data-stu-id="2ae26-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae26-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ae26-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="2ae26-109">から検証するアセンブリの移植可能な実行可能ファイル (.exe または .dll) のパス。</span><span class="sxs-lookup"><span data-stu-id="2ae26-109">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="2ae26-110">[入力] `true` レジストリ設定を上書きする必要がある場合でも、検証を実行するにはそれ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2ae26-110">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="2ae26-111">[出力] `true` 厳密な名前の署名が検証された場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2ae26-111">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="2ae26-112">`pfWasVerified``false`レジストリ設定によって検証が成功した場合は、もに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2ae26-112">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ae26-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="2ae26-113">Return Value</span></span>  

 <span data-ttu-id="2ae26-114">`true` 検証が成功した場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2ae26-114">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae26-115">解説</span><span class="sxs-lookup"><span data-stu-id="2ae26-115">Remarks</span></span>  

 <span data-ttu-id="2ae26-116">`StrongNameSignatureVerificationEx`[StrongNameSignatureVerification](strongnamesignatureverification-function.md)関数と同様の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2ae26-116">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="2ae26-117">ただし、2番目の入力パラメーターとの出力パラメーター `StrongNameSignatureVerificationEx` は、 `BOOLEAN` の代わりに型に `DWORD` なります。</span><span class="sxs-lookup"><span data-stu-id="2ae26-117">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae26-118">要件</span><span class="sxs-lookup"><span data-stu-id="2ae26-118">Requirements</span></span>  

 <span data-ttu-id="2ae26-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae26-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae26-120">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="2ae26-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ae26-121">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2ae26-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="2ae26-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae26-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae26-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ae26-123">See also</span></span>

- [<span data-ttu-id="2ae26-124">StrongNameSignatureVerificationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae26-124">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="2ae26-125">StrongNameSignatureVerification メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae26-125">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="2ae26-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae26-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
