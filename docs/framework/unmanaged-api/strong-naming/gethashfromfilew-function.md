---
description: '詳細情報: GetHashFromFileW 関数'
title: GetHashFromFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: daebd06de02dfe936f1bdeb8697de4fe6524dce3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736550"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="98775-103">GetHashFromFileW 関数</span><span class="sxs-lookup"><span data-stu-id="98775-103">GetHashFromFileW Function</span></span>

<span data-ttu-id="98775-104">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="98775-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="98775-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="98775-105">This function has been deprecated.</span></span> <span data-ttu-id="98775-106">代わりに [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="98775-106">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98775-107">構文</span><span class="sxs-lookup"><span data-stu-id="98775-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="98775-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98775-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="98775-109">からハッシュするファイルの Unicode 名。</span><span class="sxs-lookup"><span data-stu-id="98775-109">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="98775-110">[入力、出力]ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="98775-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="98775-111">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="98775-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="98775-112">が0に設定されている場合は、 `piHashAlg` 既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98775-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="98775-113">入出力生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="98775-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="98775-114">からが指すバッファーの最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="98775-114">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="98775-115">入出力のサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="98775-115">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98775-116">解説</span><span class="sxs-lookup"><span data-stu-id="98775-116">Remarks</span></span>  

 <span data-ttu-id="98775-117">この関数は [GetHashFromFile](gethashfromfile-function.md)と同じですが、ファイル名の指定は ANSI ではなく Unicode である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="98775-117">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98775-118">要件</span><span class="sxs-lookup"><span data-stu-id="98775-118">Requirements</span></span>  

 <span data-ttu-id="98775-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98775-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98775-120">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="98775-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="98775-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="98775-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98775-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98775-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98775-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="98775-123">See also</span></span>

- [<span data-ttu-id="98775-124">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="98775-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="98775-125">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="98775-125">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="98775-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98775-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
