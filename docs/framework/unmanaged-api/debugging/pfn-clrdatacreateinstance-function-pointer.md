---
description: 詳細については、「関数ポインターの PFN_CLRDataCreateInstance」を参照してください。
title: PFN_CLRDataCreateInstance 関数ポインター
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: fc048f840084eff0270944d3190ccbb153bf22d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800631"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="9ead8-103">PFN_CLRDataCreateInstance 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="9ead8-103">PFN_CLRDataCreateInstance Function Pointer</span></span>

<span data-ttu-id="9ead8-104">指定されたターゲット項目のインターフェイスオブジェクトを作成する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="9ead8-104">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ead8-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ead8-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ead8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ead8-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="9ead8-107">からインスタンス化するインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="9ead8-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="9ead8-108">からインターフェイスオブジェクトの作成対象となる項目を表す、ユーザーによって実装された [ICLRDataTarget](iclrdatatarget-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ead8-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="9ead8-109">入出力返されたインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ead8-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ead8-110">解説</span><span class="sxs-lookup"><span data-stu-id="9ead8-110">Remarks</span></span>  

 <span data-ttu-id="9ead8-111">`ICLRDataTarget`オブジェクトは、デバッグアプリケーションのライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="9ead8-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="9ead8-112">実装は、表示されるターゲット項目の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9ead8-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="9ead8-113">ターゲット項目には、プロセス、メモリダンプ、リモートコンピューターなどがあります。</span><span class="sxs-lookup"><span data-stu-id="9ead8-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ead8-114">要件</span><span class="sxs-lookup"><span data-stu-id="9ead8-114">Requirements</span></span>  

 <span data-ttu-id="9ead8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ead8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ead8-116">**ヘッダー:** ClrData .idl</span><span class="sxs-lookup"><span data-stu-id="9ead8-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="9ead8-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ead8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ead8-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ead8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ead8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ead8-119">See also</span></span>

- [<span data-ttu-id="9ead8-120">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="9ead8-120">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
