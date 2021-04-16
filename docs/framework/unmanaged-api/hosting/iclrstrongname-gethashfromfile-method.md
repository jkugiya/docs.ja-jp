---
description: '詳細情報: ICLRStrongName::GetHashFromFile メソッド'
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: e930f1c21e5b0be441fe44ad352b2ef2f43d0f67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637054"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="724d2-103">ICLRStrongName::GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="724d2-103">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="724d2-104">指定したファイルの内容に対してハッシュが生成されます。</span><span class="sxs-lookup"><span data-stu-id="724d2-104">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="724d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="724d2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="724d2-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="724d2-107">[in] ハッシュするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="724d2-107">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="724d2-108">[in、out] ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="724d2-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="724d2-109">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="724d2-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="724d2-110">`piHashAlg` が 0 に設定されている場合は、既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="724d2-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="724d2-111">[out] 生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="724d2-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="724d2-112">[in] `pbHash` が指すバッファーの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="724d2-112">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="724d2-113">[out] 返された `pbHash` のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="724d2-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="724d2-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="724d2-114">Return Value</span></span>  

 <span data-ttu-id="724d2-115">メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。</span><span class="sxs-lookup"><span data-stu-id="724d2-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="724d2-116">解説</span><span class="sxs-lookup"><span data-stu-id="724d2-116">Remarks</span></span>  

 <span data-ttu-id="724d2-117">このメソッドは [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) メソッドと基本的に同じですが、ファイル名の指定が Unicode ではなく ANSI である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="724d2-117">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724d2-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="724d2-118">Requirements</span></span>  

 <span data-ttu-id="724d2-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="724d2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724d2-120">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="724d2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="724d2-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="724d2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="724d2-122">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724d2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724d2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="724d2-123">See also</span></span>

- [<span data-ttu-id="724d2-124">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="724d2-124">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="724d2-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="724d2-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
