---
description: '詳細について: ICLRDataTarget3:: GetExceptionContextRecord メソッド'
title: ICLRDataTarget3::GetExceptionContextRecord メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: c722eaaf0f9935bc7adaa69a1792f934f631a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794833"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="33f64-103">ICLRDataTarget3::GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="33f64-103">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>

<span data-ttu-id="33f64-104">ターゲット プロセスに関連付けられたコンテキスト レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="33f64-104">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="33f64-105">たとえば、ダンプターゲットの場合、これは `ExceptionParam` Windows デバッグヘルプライブラリ (dbghelp) の [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) 関数の引数を使用して渡されたコンテキストレコードと同じになります。</span><span class="sxs-lookup"><span data-stu-id="33f64-105">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f64-106">構文</span><span class="sxs-lookup"><span data-stu-id="33f64-106">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f64-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33f64-107">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="33f64-108">[入力] 入力バッファー サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="33f64-108">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="33f64-109">これはコンテキスト レコードを格納するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="33f64-109">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="33f64-110">[出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="33f64-110">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="33f64-111">[出力] コンテキスト レコードのコピーを受け取るメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="33f64-111">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="33f64-112">例外レコードは、 [コンテキスト](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) 型として返されます。</span><span class="sxs-lookup"><span data-stu-id="33f64-112">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33f64-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="33f64-113">Return Value</span></span>  

 <span data-ttu-id="33f64-114">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="33f64-114">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="33f64-115">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="33f64-115">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="33f64-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="33f64-116">Return code</span></span>|<span data-ttu-id="33f64-117">説明</span><span class="sxs-lookup"><span data-stu-id="33f64-117">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="33f64-118">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="33f64-118">Method succeeded.</span></span> <span data-ttu-id="33f64-119">コンテキスト レコードは出力バッファーにコピーされました。</span><span class="sxs-lookup"><span data-stu-id="33f64-119">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="33f64-120">コンテキスト レコードはターゲットに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="33f64-120">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="33f64-121">入力バッファーのサイズが足りないため、コンテキスト レコードを格納できません。</span><span class="sxs-lookup"><span data-stu-id="33f64-121">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33f64-122">解説</span><span class="sxs-lookup"><span data-stu-id="33f64-122">Remarks</span></span>  

 <span data-ttu-id="33f64-123">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) は、Windows SDK によって提供されるヘッダーで定義されているプラットフォーム固有の構造体です。</span><span class="sxs-lookup"><span data-stu-id="33f64-123">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="33f64-124">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="33f64-124">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f64-125">要件</span><span class="sxs-lookup"><span data-stu-id="33f64-125">Requirements</span></span>  

 <span data-ttu-id="33f64-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33f64-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f64-127">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="33f64-127">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="33f64-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33f64-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33f64-129">**.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="33f64-129">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f64-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="33f64-130">See also</span></span>

- [<span data-ttu-id="33f64-131">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33f64-131">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="33f64-132">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="33f64-132">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="33f64-133">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="33f64-133">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
