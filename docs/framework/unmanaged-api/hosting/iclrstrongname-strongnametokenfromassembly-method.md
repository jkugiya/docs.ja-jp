---
description: '詳細について: ICLRStrongName:: StrongNameTokenFromAssembly メソッド'
title: ICLRStrongName::StrongNameTokenFromAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 520d327767f91763f8f2b3efea098c7c2790939e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781819"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="c81ca-103">ICLRStrongName::StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c81ca-103">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>

<span data-ttu-id="c81ca-104">指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c81ca-104">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="c81ca-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c81ca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c81ca-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="c81ca-107">からアセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="c81ca-107">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="c81ca-108">入出力返された厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="c81ca-108">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="c81ca-109">入出力厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="c81ca-109">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c81ca-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c81ca-110">Return Value</span></span>  

 <span data-ttu-id="c81ca-111">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c81ca-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c81ca-112">解説</span><span class="sxs-lookup"><span data-stu-id="c81ca-112">Remarks</span></span>  

 <span data-ttu-id="c81ca-113">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="c81ca-113">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="c81ca-114">トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="c81ca-114">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="c81ca-115">トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c81ca-115">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="c81ca-116">トークンが作成されたら、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c81ca-116">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81ca-117">要件</span><span class="sxs-lookup"><span data-stu-id="c81ca-117">Requirements</span></span>  

 <span data-ttu-id="c81ca-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c81ca-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81ca-119">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="c81ca-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c81ca-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c81ca-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c81ca-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81ca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81ca-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c81ca-122">See also</span></span>

- [<span data-ttu-id="c81ca-123">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="c81ca-123">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="c81ca-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c81ca-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
