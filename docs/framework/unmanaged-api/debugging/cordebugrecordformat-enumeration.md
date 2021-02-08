---
description: 詳細については、「CorDebugRecordFormat 列挙型」を参照してください。
title: CorDebugRecordFormat 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: 856522497a8f858abdb39ac232fb3034d4d91dfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801567"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="1d5ab-103">CorDebugRecordFormat 列挙体</span><span class="sxs-lookup"><span data-stu-id="1d5ab-103">CorDebugRecordFormat Enumeration</span></span>

<span data-ttu-id="1d5ab-104">ネイティブ例外デバッグ イベントに関する情報を格納するバイト配列内のデータの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-104">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5ab-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d5ab-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="1d5ab-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d5ab-106">Members</span></span>  
  
|<span data-ttu-id="1d5ab-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d5ab-107">Member</span></span>|<span data-ttu-id="1d5ab-108">説明</span><span class="sxs-lookup"><span data-stu-id="1d5ab-108">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="1d5ab-109">データは、32 ビット Windows 例外レコードです。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-109">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="1d5ab-110">データは、64 ビット Windows 例外レコードです。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-110">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d5ab-111">解説</span><span class="sxs-lookup"><span data-stu-id="1d5ab-111">Remarks</span></span>  

 <span data-ttu-id="1d5ab-112">列挙体のメンバーは、 `CorDebugRecordFormat` 引数のバイト配列の形式を示すために、 [DecodeEvent](icordebugprocess6-decodeevent-method.md) メソッドに渡され `pRecord` ます。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-112">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d5ab-113">この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d5ab-114">要件</span><span class="sxs-lookup"><span data-stu-id="1d5ab-114">Requirements</span></span>  

 <span data-ttu-id="1d5ab-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d5ab-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d5ab-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d5ab-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d5ab-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d5ab-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d5ab-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d5ab-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5ab-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d5ab-119">See also</span></span>

- [<span data-ttu-id="1d5ab-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="1d5ab-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
