---
description: '詳細について: ICLRDataTarget3:: GetExceptionThreadID メソッド'
title: ICLRDataTarget3::GetExceptionThreadID メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 8202b6d83d0c81853111c5da7cfb8deec4d4e222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794820"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="3e58e-103">ICLRDataTarget3::GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="3e58e-103">ICLRDataTarget3::GetExceptionThreadID Method</span></span>

<span data-ttu-id="3e58e-104">例外をスローしたスレッドの ID を取得するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3e58e-104">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e58e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e58e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e58e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e58e-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="3e58e-107">[out] 例外をスローしたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="3e58e-107">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e58e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3e58e-108">Return Value</span></span>  

 <span data-ttu-id="3e58e-109">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="3e58e-109">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="3e58e-110">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3e58e-110">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="3e58e-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="3e58e-111">Return code</span></span>|<span data-ttu-id="3e58e-112">説明</span><span class="sxs-lookup"><span data-stu-id="3e58e-112">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="3e58e-113">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="3e58e-113">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="3e58e-114">例外の有効なスレッド ID を見つけることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="3e58e-114">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e58e-115">解説</span><span class="sxs-lookup"><span data-stu-id="3e58e-115">Remarks</span></span>  

 <span data-ttu-id="3e58e-116">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="3e58e-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e58e-117">要件</span><span class="sxs-lookup"><span data-stu-id="3e58e-117">Requirements</span></span>  

 <span data-ttu-id="3e58e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e58e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e58e-119">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="3e58e-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3e58e-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e58e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e58e-121">**.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e58e-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e58e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e58e-122">See also</span></span>

- [<span data-ttu-id="3e58e-123">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e58e-123">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="3e58e-124">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="3e58e-124">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="3e58e-125">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="3e58e-125">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
