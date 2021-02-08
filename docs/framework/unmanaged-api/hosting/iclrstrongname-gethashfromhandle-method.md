---
description: '詳細について: ICLRStrongName:: GetHashFromHandle メソッド'
title: ICLRStrongName::GetHashFromHandle メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 30248b5cb5d102adaa06293c92cc4f21e905cba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799682"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="adbe5-103">ICLRStrongName::GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="adbe5-103">ICLRStrongName::GetHashFromHandle Method</span></span>

<span data-ttu-id="adbe5-104">指定したハッシュアルゴリズムを使用して、指定したファイルハンドルを持つファイルの内容に対してハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="adbe5-104">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adbe5-105">構文</span><span class="sxs-lookup"><span data-stu-id="adbe5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adbe5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="adbe5-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="adbe5-107">からハッシュされるファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="adbe5-107">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="adbe5-108">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="adbe5-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="adbe5-109">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="adbe5-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="adbe5-110">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="adbe5-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="adbe5-111">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="adbe5-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="adbe5-112">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="adbe5-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adbe5-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="adbe5-113">Return Value</span></span>  

 <span data-ttu-id="adbe5-114">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="adbe5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adbe5-115">要件</span><span class="sxs-lookup"><span data-stu-id="adbe5-115">Requirements</span></span>  

 <span data-ttu-id="adbe5-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adbe5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adbe5-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="adbe5-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="adbe5-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="adbe5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adbe5-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adbe5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adbe5-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="adbe5-120">See also</span></span>

- [<span data-ttu-id="adbe5-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="adbe5-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
