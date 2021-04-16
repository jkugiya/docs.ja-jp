---
description: '詳細情報: ICLRStrongName::GetHashFromFileW メソッド'
title: ICLRStrongName::GetHashFromFileW メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 6145a044f490ef3827de6db8d84d16222306642d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636976"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="d6dcb-103">ICLRStrongName::GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="d6dcb-103">ICLRStrongName::GetHashFromFileW Method</span></span>

<span data-ttu-id="d6dcb-104">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6dcb-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6dcb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d6dcb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6dcb-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="d6dcb-107">[in] ハッシュするファイルの Unicode 名。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-107">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d6dcb-108">[in、out] ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d6dcb-109">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d6dcb-110">`piHashAlg` が 0 に設定されている場合は、既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d6dcb-111">[out] 生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d6dcb-112">[in] `pbHash` が指すバッファーの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-112">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d6dcb-113">[out] `pbHash` のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-113">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6dcb-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6dcb-114">Return Value</span></span>  

 <span data-ttu-id="d6dcb-115">メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6dcb-116">解説</span><span class="sxs-lookup"><span data-stu-id="d6dcb-116">Remarks</span></span>  

 <span data-ttu-id="d6dcb-117">このメソッドは [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) メソッドと基本的に同じですが、ファイル名の指定が ANSI ではなく Unicode である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-117">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6dcb-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="d6dcb-118">Requirements</span></span>  

 <span data-ttu-id="d6dcb-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6dcb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6dcb-120">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d6dcb-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d6dcb-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="d6dcb-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6dcb-122">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6dcb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dcb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6dcb-123">See also</span></span>

- [<span data-ttu-id="d6dcb-124">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="d6dcb-124">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="d6dcb-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6dcb-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
