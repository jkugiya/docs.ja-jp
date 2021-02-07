---
description: '詳細については、次を参照してください: StackOverflowInfo 構造体'
title: StackOverflowInfo 構造体
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: cca65e4293c05b89ebefc3c6dd36a6b8898eb15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679395"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="9172e-103">StackOverflowInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="9172e-103">StackOverflowInfo Structure</span></span>

<span data-ttu-id="9172e-104">発生したオーバーフローの種類とオーバーフローによってスローされた例外に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="9172e-104">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9172e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9172e-105">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="9172e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9172e-106">Members</span></span>  
  
|<span data-ttu-id="9172e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="9172e-107">Member</span></span>|<span data-ttu-id="9172e-108">説明</span><span class="sxs-lookup"><span data-stu-id="9172e-108">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="9172e-109">オーバーフローの種類を指定する [StackOverflowType](stackoverflowtype-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="9172e-109">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="9172e-110">Win32 オブジェクトへのポインター。このオブジェクトには、例外 `EXCEPTION_POINTERS` のコンピューターに依存しない記述と、例外の発生時にプロセッサコンテキストのコンピューターに依存する記述を持つコンテキストレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9172e-110">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9172e-111">解説</span><span class="sxs-lookup"><span data-stu-id="9172e-111">Remarks</span></span>  

 <span data-ttu-id="9172e-112">`StackOverflowInfo`オブジェクトは、イベントの[Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドに渡され `Event_StackOverflow` ます。</span><span class="sxs-lookup"><span data-stu-id="9172e-112">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9172e-113">要件</span><span class="sxs-lookup"><span data-stu-id="9172e-113">Requirements</span></span>  

 <span data-ttu-id="9172e-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9172e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9172e-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9172e-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9172e-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9172e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9172e-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9172e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9172e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9172e-118">See also</span></span>

- [<span data-ttu-id="9172e-119">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="9172e-119">Hosting Structures</span></span>](hosting-structures.md)
