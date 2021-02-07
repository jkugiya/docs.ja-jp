---
description: CLRDataCreateInstance 関数の詳細について説明します。
title: CLRDataCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- DLLExport
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 923b0c687d2b337eacb475973927452e3b47ad0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747258"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="06b6f-103">CLRDataCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="06b6f-103">CLRDataCreateInstance Function</span></span>

<span data-ttu-id="06b6f-104">指定したターゲット項目のインターフェイスオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="06b6f-104">Creates an interface object for the specified target item.</span></span>

## <a name="syntax"></a><span data-ttu-id="06b6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="06b6f-105">Syntax</span></span>

```cpp
HRESULT CLRDataCreateInstance (
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b6f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06b6f-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="06b6f-107">からインスタンス化するインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="06b6f-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="06b6f-108">からインターフェイスオブジェクトの作成対象となる項目を表す、ユーザーによって実装された [ICLRDataTarget](iclrdatatarget-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06b6f-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="06b6f-109">入出力返されたインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06b6f-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06b6f-110">解説</span><span class="sxs-lookup"><span data-stu-id="06b6f-110">Remarks</span></span>  

 <span data-ttu-id="06b6f-111">`ICLRDataTarget`オブジェクトは、デバッグアプリケーションのライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="06b6f-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="06b6f-112">実装は、表示されるターゲット項目の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="06b6f-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="06b6f-113">ターゲット項目には、プロセス、メモリダンプ、リモートコンピューターなどがあります。</span><span class="sxs-lookup"><span data-stu-id="06b6f-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b6f-114">要件</span><span class="sxs-lookup"><span data-stu-id="06b6f-114">Requirements</span></span>  

 <span data-ttu-id="06b6f-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06b6f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b6f-116">**ヘッダー:** ClrData .idl</span><span class="sxs-lookup"><span data-stu-id="06b6f-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="06b6f-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06b6f-117">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="06b6f-118">**アセンブリ**: mscordacwks.dll、mscordbi.dll</span><span class="sxs-lookup"><span data-stu-id="06b6f-118">**Assembly**: mscordacwks.dll, mscordbi.dll</span></span>
  
 <span data-ttu-id="06b6f-119">**.NET Framework のバージョン:** .NET Framework 2.0 以降で使用可能</span><span class="sxs-lookup"><span data-stu-id="06b6f-119">**.NET Framework Versions:** Available since .NET Framework 2.0</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06b6f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="06b6f-120">See also</span></span>

- [<span data-ttu-id="06b6f-121">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="06b6f-121">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
