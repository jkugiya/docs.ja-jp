---
description: '詳細情報: GetHashFromHandle 関数'
title: GetHashFromHandle 関数
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: 5951a5befd9e66b13a3b3033398614fca1f1a9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736548"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="9dbea-103">GetHashFromHandle 関数</span><span class="sxs-lookup"><span data-stu-id="9dbea-103">GetHashFromHandle Function</span></span>

<span data-ttu-id="9dbea-104">指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを含むファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9dbea-104">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="9dbea-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="9dbea-105">This function has been deprecated.</span></span> <span data-ttu-id="9dbea-106">代わりに [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9dbea-106">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dbea-107">構文</span><span class="sxs-lookup"><span data-stu-id="9dbea-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dbea-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9dbea-108">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="9dbea-109">からハッシュされるファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="9dbea-109">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9dbea-110">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="9dbea-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9dbea-111">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dbea-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9dbea-112">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="9dbea-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9dbea-113">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="9dbea-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9dbea-114">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="9dbea-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dbea-115">要件</span><span class="sxs-lookup"><span data-stu-id="9dbea-115">Requirements</span></span>  

 <span data-ttu-id="9dbea-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dbea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dbea-117">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="9dbea-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9dbea-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9dbea-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dbea-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dbea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbea-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dbea-120">See also</span></span>

- [<span data-ttu-id="9dbea-121">GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="9dbea-121">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="9dbea-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dbea-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
