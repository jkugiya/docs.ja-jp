---
description: '詳細情報: GetHashFromFile 関数'
title: GetHashFromFile 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: f91bfe8a3988b6aae563b5a852997d6fd3c309d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736597"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="1e738-103">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="1e738-103">GetHashFromFile Function</span></span>

<span data-ttu-id="1e738-104">指定したファイルの内容に対してハッシュが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1e738-104">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="1e738-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1e738-105">This function has been deprecated.</span></span> <span data-ttu-id="1e738-106">代わりに [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1e738-106">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e738-107">構文</span><span class="sxs-lookup"><span data-stu-id="1e738-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e738-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e738-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="1e738-109">からハッシュするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1e738-109">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1e738-110">[入力、出力]ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="1e738-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="1e738-111">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="1e738-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="1e738-112">が0に設定されている場合は、 `piHashAlg` 既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e738-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1e738-113">入出力生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="1e738-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1e738-114">からが指すバッファーの最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="1e738-114">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1e738-115">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="1e738-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e738-116">解説</span><span class="sxs-lookup"><span data-stu-id="1e738-116">Remarks</span></span>  

 <span data-ttu-id="1e738-117">この関数は [GetHashFromFileW](gethashfromfilew-function.md)と同じですが、ファイル名の指定は Unicode ではなく ANSI である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="1e738-117">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e738-118">要件</span><span class="sxs-lookup"><span data-stu-id="1e738-118">Requirements</span></span>  

 <span data-ttu-id="1e738-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e738-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e738-120">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="1e738-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1e738-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1e738-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e738-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e738-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e738-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e738-123">See also</span></span>

- [<span data-ttu-id="1e738-124">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="1e738-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="1e738-125">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="1e738-125">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="1e738-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e738-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
