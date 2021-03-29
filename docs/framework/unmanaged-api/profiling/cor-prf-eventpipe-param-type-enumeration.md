---
description: '詳細情報: COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型'
title: COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805780"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a><span data-ttu-id="a03cb-103">COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="a03cb-103">COR_PRF_EVENTPIPE_PARAM_TYPE Enumeration</span></span>

<span data-ttu-id="a03cb-104">EventPipe イベントのパラメーターの型を記述します。</span><span class="sxs-lookup"><span data-stu-id="a03cb-104">Describes the type of a parameter for an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="a03cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="a03cb-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a><span data-ttu-id="a03cb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a03cb-106">Members</span></span>  
  
|<span data-ttu-id="a03cb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a03cb-107">Member</span></span>|<span data-ttu-id="a03cb-108">説明</span><span class="sxs-lookup"><span data-stu-id="a03cb-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|<span data-ttu-id="a03cb-109">このパラメーターの型は自己記述型のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a03cb-109">The parameter type is a self describing object.</span></span>|
|`COR_PRF_EVENTPIPE_BOOLEAN`|<span data-ttu-id="a03cb-110">このパラメーターの型はブール値です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-110">The parameter type is a boolean.</span></span>|
|`COR_PRF_EVENTPIPE_CHAR`|<span data-ttu-id="a03cb-111">このパラメーターの型は 16 ビット ワイド文字です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-111">The parameter type is a 16 bit wide character.</span></span>|
|`COR_PRF_EVENTPIPE_SBYTE`|<span data-ttu-id="a03cb-112">このパラメーターの型は符号付き 8 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-112">The parameter type is a signed 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_BYTE`|<span data-ttu-id="a03cb-113">このパラメーターの型は符号なし 8 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-113">The parameter type is an unsigned 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT16`|<span data-ttu-id="a03cb-114">このパラメーターの型は符号付き 16 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-114">The parameter type is a signed 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT16`|<span data-ttu-id="a03cb-115">このパラメーターの型は符号なし 16 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-115">The parameter type is an unsigned 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT32`|<span data-ttu-id="a03cb-116">このパラメーターの型は符号付き 32 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-116">The parameter type is a signed 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT32`|<span data-ttu-id="a03cb-117">このパラメーターの型は符号なし 32 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-117">The parameter type is an unsigned 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT64`|<span data-ttu-id="a03cb-118">このパラメーターの型は符号付き 64 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-118">The parameter type is a signed 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT64`|<span data-ttu-id="a03cb-119">このパラメーターの型は符号なし 64 ビット整数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-119">The parameter type is an unsigned 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_SINGLE`|<span data-ttu-id="a03cb-120">このパラメーターの型は 32 ビット浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-120">The parameter type is a 32 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DOUBLE`|<span data-ttu-id="a03cb-121">このパラメーターの型は 64 ビット浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-121">The parameter type is a 64 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DECIMAL`|<span data-ttu-id="a03cb-122">このパラメーターの型は 128 ビット浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-122">The parameter type is a 128 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DATETIME`|<span data-ttu-id="a03cb-123">このパラメーターの型はシリアル化された DataTime 構造体です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-123">The parameter type is a serialized DataTime structure.</span></span>|
|`COR_PRF_EVENTPIPE_GUID`|<span data-ttu-id="a03cb-124">このパラメーターの型は GUID です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-124">The parameter type is a GUID.</span></span>|
|`COR_PRF_EVENTPIPE_STRING`|<span data-ttu-id="a03cb-125">このパラメーターの型は 16 ビットの null で終わるワイド文字列です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-125">The parameter type is a 16 bit null terminated wide character string.</span></span>|
|`COR_PRF_EVENTPIPE_ARRAY`|<span data-ttu-id="a03cb-126">このパラメーターの型は前のいずれかの型の配列です。</span><span class="sxs-lookup"><span data-stu-id="a03cb-126">The parameter type is an array of one of the preceding types.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="a03cb-127">解説</span><span class="sxs-lookup"><span data-stu-id="a03cb-127">Remarks</span></span>  

 <span data-ttu-id="a03cb-128">`COR_PRF_EVENTPIPE_PARAM_TYPE` 列挙型は、パラメーターの型を示すために [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) 構造体によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a03cb-128">The `COR_PRF_EVENTPIPE_PARAM_TYPE` enumeration is used by the [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) structure to indicate the type of the parameter.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="a03cb-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="a03cb-129">Requirements</span></span>  

<span data-ttu-id="a03cb-130">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a03cb-130">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="a03cb-131">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a03cb-131">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a03cb-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="a03cb-132">See also</span></span>

- [<span data-ttu-id="a03cb-133">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a03cb-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
