---
description: '詳細情報: GetHashFromAssemblyFileW 関数'
title: GetHashFromAssemblyFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: 7f44106f12a2d21ea67acb874b577c5b303632b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736675"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="cf286-103">GetHashFromAssemblyFileW 関数</span><span class="sxs-lookup"><span data-stu-id="cf286-103">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="cf286-104">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="cf286-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="cf286-105">アセンブリファイルへのパスは、Unicode 文字列として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf286-105">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="cf286-106">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="cf286-106">This function has been deprecated.</span></span> <span data-ttu-id="cf286-107">代わりに [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="cf286-107">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf286-108">構文</span><span class="sxs-lookup"><span data-stu-id="cf286-108">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf286-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cf286-109">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="cf286-110">からハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="cf286-110">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="cf286-111">このパラメーターは Unicode 文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf286-111">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cf286-112">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="cf286-112">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="cf286-113">既定のハッシュアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf286-113">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cf286-114">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="cf286-114">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cf286-115">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="cf286-115">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cf286-116">入出力の返されたサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="cf286-116">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf286-117">要件</span><span class="sxs-lookup"><span data-stu-id="cf286-117">Requirements</span></span>  

 <span data-ttu-id="cf286-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf286-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf286-119">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="cf286-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cf286-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cf286-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf286-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf286-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf286-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf286-122">See also</span></span>

- [<span data-ttu-id="cf286-123">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="cf286-123">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="cf286-124">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="cf286-124">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="cf286-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf286-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
