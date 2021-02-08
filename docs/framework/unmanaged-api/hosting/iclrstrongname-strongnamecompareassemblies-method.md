---
description: '詳細について: ICLRStrongName:: StrongNameCompareAssemblies メソッド'
title: ICLRStrongName::StrongNameCompareAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ab02312073f9caf5059ecf7b4eeddaef864bd7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799651"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="07d98-103">ICLRStrongName::StrongNameCompareAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="07d98-103">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>

<span data-ttu-id="07d98-104">厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="07d98-104">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d98-105">構文</span><span class="sxs-lookup"><span data-stu-id="07d98-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07d98-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07d98-106">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="07d98-107">から最初のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="07d98-107">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="07d98-108">から2番目のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="07d98-108">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="07d98-109">入出力次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="07d98-109">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="07d98-110">`SN_CMP_DIFFERENT` (0)-アセンブリに異なるデータが含まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07d98-110">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="07d98-111">`SN_CMP_IDENTICAL` (1)-署名やチェックサムなど、アセンブリがまったく同じであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07d98-111">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="07d98-112">`SN_CMP_SIGONLY` (2)-アセンブリが署名とチェックサムのみで異なることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07d98-112">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07d98-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="07d98-113">Return Value</span></span>  

 <span data-ttu-id="07d98-114">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="07d98-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07d98-115">要件</span><span class="sxs-lookup"><span data-stu-id="07d98-115">Requirements</span></span>  

 <span data-ttu-id="07d98-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07d98-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d98-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="07d98-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="07d98-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="07d98-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07d98-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07d98-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07d98-120">解説</span><span class="sxs-lookup"><span data-stu-id="07d98-120">Remarks</span></span>  

 <span data-ttu-id="07d98-121">アセンブリの厳密な名前の署名は、アセンブリのテキスト名、バージョン、カルチャ、および公開キートークンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="07d98-121">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d98-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="07d98-122">See also</span></span>

- [<span data-ttu-id="07d98-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07d98-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
