---
description: '詳細情報: ICLRDataTarget:: Request メソッド'
title: ICLRDataTarget::Request メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 75c400a51a2fdaf0044d85b5f483d783fae4628b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712169"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="64dd2-103">ICLRDataTarget::Request メソッド</span><span class="sxs-lookup"><span data-stu-id="64dd2-103">ICLRDataTarget::Request Method</span></span>

<span data-ttu-id="64dd2-104">実装で定義されているように、操作を要求するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="64dd2-104">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64dd2-105">構文</span><span class="sxs-lookup"><span data-stu-id="64dd2-105">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64dd2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64dd2-106">Parameters</span></span>  

 `reqCode`  
 <span data-ttu-id="64dd2-107">からユーザー定義。</span><span class="sxs-lookup"><span data-stu-id="64dd2-107">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="64dd2-108">から受信要求に使用される入力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="64dd2-108">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="64dd2-109">から要求を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="64dd2-109">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="64dd2-110">から応答に使用される出力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="64dd2-110">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="64dd2-111">入出力応答を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="64dd2-111">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64dd2-112">解説</span><span class="sxs-lookup"><span data-stu-id="64dd2-112">Remarks</span></span>  

 <span data-ttu-id="64dd2-113">メソッドは、指定されて `Request` いないカスタム操作の追加を容易にします。</span><span class="sxs-lookup"><span data-stu-id="64dd2-113">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="64dd2-114">つまり、このメソッドは、インターフェイス定義のリビジョンを必要とせずに、拡張機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="64dd2-114">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="64dd2-115">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="64dd2-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64dd2-116">要件</span><span class="sxs-lookup"><span data-stu-id="64dd2-116">Requirements</span></span>  

 <span data-ttu-id="64dd2-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64dd2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64dd2-118">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="64dd2-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="64dd2-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64dd2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64dd2-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64dd2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64dd2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="64dd2-121">See also</span></span>

- [<span data-ttu-id="64dd2-122">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64dd2-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
