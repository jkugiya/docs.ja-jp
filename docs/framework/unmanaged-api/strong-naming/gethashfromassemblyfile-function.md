---
description: '詳細情報: GetHashFromAssemblyFile 関数'
title: GetHashFromAssemblyFile 関数
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 79cc6289ebcf33f5a9ea8b4ef139c4b2a67e55e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736779"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="5849b-103">GetHashFromAssemblyFile 関数</span><span class="sxs-lookup"><span data-stu-id="5849b-103">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="5849b-104">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="5849b-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="5849b-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="5849b-105">This function has been deprecated.</span></span> <span data-ttu-id="5849b-106">代わりに [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5849b-106">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5849b-107">構文</span><span class="sxs-lookup"><span data-stu-id="5849b-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5849b-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5849b-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="5849b-109">からハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="5849b-109">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5849b-110">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="5849b-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5849b-111">既定のハッシュアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="5849b-111">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5849b-112">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="5849b-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5849b-113">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="5849b-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5849b-114">入出力の返されたサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="5849b-114">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5849b-115">要件</span><span class="sxs-lookup"><span data-stu-id="5849b-115">Requirements</span></span>  

 <span data-ttu-id="5849b-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5849b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5849b-117">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="5849b-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5849b-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5849b-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5849b-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5849b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5849b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5849b-120">See also</span></span>

- [<span data-ttu-id="5849b-121">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="5849b-121">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="5849b-122">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="5849b-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="5849b-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5849b-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
