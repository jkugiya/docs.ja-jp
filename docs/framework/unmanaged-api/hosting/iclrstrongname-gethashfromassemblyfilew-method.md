---
description: '詳細情報: ICLRStrongName::GetHashFromAssemblyFileW メソッド'
title: ICLRStrongName::GetHashFromAssemblyFileW メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 27123ed8217d49765fe3fd7c19efc92f4e770722
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637080"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="21a8b-103">ICLRStrongName::GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="21a8b-103">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="21a8b-104">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="21a8b-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a8b-105">構文</span><span class="sxs-lookup"><span data-stu-id="21a8b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21a8b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21a8b-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="21a8b-107">[in] ハッシュ化されるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="21a8b-107">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="21a8b-108">このパラメーターは、Unicode 文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="21a8b-108">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="21a8b-109">[in、out] ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="21a8b-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="21a8b-110">既定のハッシュ アルゴリズムでは、ゼロを使用します。</span><span class="sxs-lookup"><span data-stu-id="21a8b-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="21a8b-111">[out] 返されたハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="21a8b-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="21a8b-112">[in] 要求された `pbHash` の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="21a8b-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="21a8b-113">[out] `pbHash` の返されたサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="21a8b-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21a8b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="21a8b-114">Return Value</span></span>  

 <span data-ttu-id="21a8b-115">メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。</span><span class="sxs-lookup"><span data-stu-id="21a8b-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a8b-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="21a8b-116">Requirements</span></span>  

 <span data-ttu-id="21a8b-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21a8b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a8b-118">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="21a8b-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21a8b-119">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="21a8b-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21a8b-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a8b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a8b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="21a8b-121">See also</span></span>

- [<span data-ttu-id="21a8b-122">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="21a8b-122">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="21a8b-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21a8b-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
