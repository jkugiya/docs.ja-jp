---
description: '詳細について: ICLRStrongName:: GetHashFromFileW メソッド'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636976"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="2297f-103">ICLRStrongName::GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="2297f-103">ICLRStrongName::GetHashFromFileW Method</span></span>

<span data-ttu-id="2297f-104">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2297f-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2297f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2297f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2297f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2297f-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="2297f-107">からハッシュするファイルの Unicode 名。</span><span class="sxs-lookup"><span data-stu-id="2297f-107">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2297f-108">[入力、出力]ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="2297f-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="2297f-109">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="2297f-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="2297f-110">が0に設定されている場合は、 `piHashAlg` 既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2297f-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2297f-111">入出力生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="2297f-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2297f-112">からが指すバッファーの最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="2297f-112">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2297f-113">入出力のサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="2297f-113">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2297f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="2297f-114">Return Value</span></span>  

 <span data-ttu-id="2297f-115">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2297f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2297f-116">解説</span><span class="sxs-lookup"><span data-stu-id="2297f-116">Remarks</span></span>  

 <span data-ttu-id="2297f-117">このメソッドは [ICLRStrongName:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) メソッドと同じですが、ファイル名の指定は ANSI ではなく Unicode である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="2297f-117">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2297f-118">要件</span><span class="sxs-lookup"><span data-stu-id="2297f-118">Requirements</span></span>  

 <span data-ttu-id="2297f-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2297f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2297f-120">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="2297f-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2297f-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2297f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2297f-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2297f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2297f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2297f-123">See also</span></span>

- [<span data-ttu-id="2297f-124">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="2297f-124">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="2297f-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2297f-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
