---
description: '詳細情報: GetHashFromBlob 関数'
title: GetHashFromBlob 関数
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: dc5039e44440afa7a000bc61167faec0e5b6cc84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736610"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="26661-103">GetHashFromBlob 関数</span><span class="sxs-lookup"><span data-stu-id="26661-103">GetHashFromBlob Function</span></span>

<span data-ttu-id="26661-104">指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。</span><span class="sxs-lookup"><span data-stu-id="26661-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="26661-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="26661-105">This function has been deprecated.</span></span> <span data-ttu-id="26661-106">代わりに [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="26661-106">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="26661-107">構文</span><span class="sxs-lookup"><span data-stu-id="26661-107">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="26661-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26661-108">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="26661-109">からハッシュされるメモリブロックのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26661-109">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="26661-110">からメモリブロックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="26661-110">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="26661-111">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="26661-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="26661-112">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="26661-112">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="26661-113">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="26661-113">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="26661-114">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="26661-114">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="26661-115">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="26661-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="26661-116">要件</span><span class="sxs-lookup"><span data-stu-id="26661-116">Requirements</span></span>

<span data-ttu-id="26661-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26661-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="26661-118">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="26661-118">**Header:** StrongName.h</span></span>

<span data-ttu-id="26661-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="26661-119">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="26661-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26661-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="26661-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="26661-121">See also</span></span>

- [<span data-ttu-id="26661-122">GetHashFromBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="26661-122">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="26661-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26661-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
