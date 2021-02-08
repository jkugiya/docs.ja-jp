---
description: 詳細については、「GetHostName メソッド」を参照してください。
title: ICorDebugRemoteTarget::GetHostName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: a24f34dd638c7031211c2185cd761af0aa24105e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803527"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="cadd6-103">ICorDebugRemoteTarget::GetHostName メソッド</span><span class="sxs-lookup"><span data-stu-id="cadd6-103">ICorDebugRemoteTarget::GetHostName Method</span></span>

<span data-ttu-id="cadd6-104">リモート デバッグ対象コンピューターの完全修飾ドメイン名または IPv4 アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="cadd6-104">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="cadd6-105">IPV6 はこの時点ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="cadd6-105">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadd6-106">構文</span><span class="sxs-lookup"><span data-stu-id="cadd6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="cadd6-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cadd6-107">Parameters</span></span>  

 `cchHostName`  
 <span data-ttu-id="cadd6-108">[入力] `szHostName` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="cadd6-108">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="cadd6-109">このパラメーターが 0 である場合、`szHostName` は null であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cadd6-109">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="cadd6-110">[出力] 配列に返される文字数。ホスト名または IP アドレスの null 終端文字を含みます。</span><span class="sxs-lookup"><span data-stu-id="cadd6-110">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="cadd6-111">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cadd6-111">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="cadd6-112">[出力] ホスト名または IP アドレスを含むバッファー。</span><span class="sxs-lookup"><span data-stu-id="cadd6-112">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cadd6-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="cadd6-113">Return Value</span></span>  

 <span data-ttu-id="cadd6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cadd6-114">S_OK</span></span>  
 <span data-ttu-id="cadd6-115">ホスト名または IP アドレスは正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cadd6-115">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="cadd6-116">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="cadd6-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cadd6-117">ホスト名または IP アドレスを返すことができません。</span><span class="sxs-lookup"><span data-stu-id="cadd6-117">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cadd6-118">解説</span><span class="sxs-lookup"><span data-stu-id="cadd6-118">Remarks</span></span>  

 <span data-ttu-id="cadd6-119">このメソッドは、デバッガー ライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="cadd6-119">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="cadd6-120">これは、複数の呼び出しパラダイムに従う必要があります。1回目の呼び出しでは、呼び出し元がとの両方に null を渡し、 `cchHostName` `szHostName` `pcchHostName` 必要なバッファーのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="cadd6-120">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="cadd6-121">第 2 の呼び出しでは、以前に返されたサイズが `cchHostName` に渡され、適切にサイズ設定されたバッファーが `szHostName` に渡されます。</span><span class="sxs-lookup"><span data-stu-id="cadd6-121">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadd6-122">要件</span><span class="sxs-lookup"><span data-stu-id="cadd6-122">Requirements</span></span>  

 <span data-ttu-id="cadd6-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cadd6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadd6-124">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="cadd6-124">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cadd6-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cadd6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cadd6-126">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cadd6-126">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadd6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="cadd6-127">See also</span></span>

- [<span data-ttu-id="cadd6-128">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cadd6-128">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="cadd6-129">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cadd6-129">ICorDebug Interface</span></span>](icordebug-interface.md)
