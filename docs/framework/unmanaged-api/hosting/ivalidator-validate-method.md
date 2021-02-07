---
description: '詳細情報: IValidator:: Validate メソッド'
title: IValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 6df70274a788b949686fe2509b525c5a8b04089c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680019"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="73ae4-103">IValidator::Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="73ae4-103">IValidator::Validate Method</span></span>

<span data-ttu-id="73ae4-104">指定された移植可能な実行可能 (PE) ファイルまたは MSIL (Microsoft 中間言語) ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="73ae4-104">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ae4-105">構文</span><span class="sxs-lookup"><span data-stu-id="73ae4-105">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73ae4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73ae4-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="73ae4-107">から `IVEHandler` 検証エラーを処理するインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="73ae4-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="73ae4-108">からファイルが読み込まれるアプリケーションドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="73ae4-108">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="73ae4-109">から実行する必要のある検証を示す、 [Validatorflags](validatorflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="73ae4-109">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="73ae4-110">から検証を終了するまでに許容されるエラーの最大数。</span><span class="sxs-lookup"><span data-stu-id="73ae4-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="73ae4-111">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="73ae4-111">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="73ae4-112">から検証するファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="73ae4-112">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="73ae4-113">からファイルが格納されているメモリバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="73ae4-113">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="73ae4-114">から検証するファイルのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="73ae4-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ae4-115">要件</span><span class="sxs-lookup"><span data-stu-id="73ae4-115">Requirements</span></span>  

 <span data-ttu-id="73ae4-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73ae4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ae4-117">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="73ae4-117">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="73ae4-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="73ae4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73ae4-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ae4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
