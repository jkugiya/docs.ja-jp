---
description: '詳細情報: ICLRValidator::Validate メソッド'
title: ICLRValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: a188315d44021fc8bf40be9bb9aecac436351467
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636742"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="a0740-103">ICLRValidator::Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="a0740-103">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="a0740-104">指定されたファイル内のポータブル実行可能 (PE) または Microsoft 中間言語 (MSIL) を検証します。</span><span class="sxs-lookup"><span data-stu-id="a0740-104">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0740-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0740-105">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="a0740-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0740-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="a0740-107">[in] 検証エラーを処理する `IVEHandler` インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a0740-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="a0740-108">[in] 現在の <xref:System.AppDomain> の識別子。</span><span class="sxs-lookup"><span data-stu-id="a0740-108">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="a0740-109">[in] 実行する必要のある検証の種類を示す、[ValidatorFlags](validatorflags-enumeration.md) 値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="a0740-109">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="a0740-110">[in] 検証を終了するまでに許容されるエラーの最大数。</span><span class="sxs-lookup"><span data-stu-id="a0740-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="a0740-111">[in] 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="a0740-111">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="a0740-112">[in] 検証対象のファイル名。</span><span class="sxs-lookup"><span data-stu-id="a0740-112">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="a0740-113">[in] ファイル バッファーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="a0740-113">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="a0740-114">[in] 検証するファイルのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a0740-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0740-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0740-115">Return Value</span></span>  
  
|<span data-ttu-id="a0740-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0740-116">HRESULT</span></span>|<span data-ttu-id="a0740-117">説明</span><span class="sxs-lookup"><span data-stu-id="a0740-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0740-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0740-118">S_OK</span></span>|<span data-ttu-id="a0740-119">`Validate` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a0740-119">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="a0740-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0740-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0740-121">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを正常に処理できない状態です。</span><span class="sxs-lookup"><span data-stu-id="a0740-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0740-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0740-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0740-123">呼び出しがタイムアウトになりました。</span><span class="sxs-lookup"><span data-stu-id="a0740-123">The call timed out.</span></span>|  
|<span data-ttu-id="a0740-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0740-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0740-125">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a0740-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0740-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0740-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0740-127">ブロックされたスレッドまたはファイバーでの待機時に、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a0740-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0740-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0740-128">E_FAIL</span></span>|<span data-ttu-id="a0740-129">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a0740-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0740-130">メソッドにより E_FAIL が返されると、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a0740-130">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0740-131">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a0740-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0740-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="a0740-132">Requirements</span></span>  

 <span data-ttu-id="a0740-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0740-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0740-134">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="a0740-134">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a0740-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="a0740-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0740-136">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0740-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0740-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0740-137">See also</span></span>

- [<span data-ttu-id="a0740-138">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0740-138">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
