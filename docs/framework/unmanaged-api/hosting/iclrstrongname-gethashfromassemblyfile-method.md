---
description: '詳細について: ICLRStrongName:: GetHashFromAssemblyFile メソッド'
title: ICLRStrongName::GetHashFromAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 40a8e2aabe9ade00243c535d63389f4265cc6ab0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799700"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="10d75-103">ICLRStrongName::GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="10d75-103">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>

<span data-ttu-id="10d75-104">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="10d75-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d75-105">構文</span><span class="sxs-lookup"><span data-stu-id="10d75-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10d75-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10d75-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="10d75-107">からハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="10d75-107">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="10d75-108">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="10d75-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="10d75-109">既定のハッシュアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="10d75-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="10d75-110">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="10d75-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="10d75-111">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="10d75-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="10d75-112">入出力の返されたサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="10d75-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10d75-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="10d75-113">Return Value</span></span>  

 <span data-ttu-id="10d75-114">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="10d75-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10d75-115">要件</span><span class="sxs-lookup"><span data-stu-id="10d75-115">Requirements</span></span>  

 <span data-ttu-id="10d75-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10d75-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d75-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="10d75-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="10d75-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="10d75-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10d75-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d75-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d75-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="10d75-120">See also</span></span>

- [<span data-ttu-id="10d75-121">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="10d75-121">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="10d75-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10d75-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
