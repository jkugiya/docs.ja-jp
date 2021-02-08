---
description: '詳細については、次を参照してください: CorErrorIfEmitOutOfOrder 列挙型'
title: CorErrorIfEmitOutOfOrder 列挙型
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: b45d3204ae386b7ad9d7ab1daccdfdef35e2ad9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784523"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="d453d-103">CorErrorIfEmitOutOfOrder 列挙型</span><span class="sxs-lookup"><span data-stu-id="d453d-103">CorErrorIfEmitOutOfOrder Enumeration</span></span>

<span data-ttu-id="d453d-104">メタデータの生成順序が不適切である場合にエラー メッセージが生成される条件を示すフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d453d-104">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d453d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d453d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="d453d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d453d-106">Members</span></span>  
  
|<span data-ttu-id="d453d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="d453d-107">Member</span></span>|<span data-ttu-id="d453d-108">説明</span><span class="sxs-lookup"><span data-stu-id="d453d-108">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="d453d-109">エラーメッセージを生成しない既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-109">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="d453d-110">コンパイラがエラーメッセージを生成しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-110">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="d453d-111">フィールド、プロパティ、イベント、メソッド、またはパラメーターが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成することを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-111">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="d453d-112">メソッドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-112">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="d453d-113">フィールドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-113">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="d453d-114">パラメーターが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-114">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="d453d-115">プロパティが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-115">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="d453d-116">イベントが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d453d-116">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d453d-117">要件</span><span class="sxs-lookup"><span data-stu-id="d453d-117">Requirements</span></span>  

 <span data-ttu-id="d453d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d453d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d453d-119">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d453d-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d453d-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d453d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d453d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d453d-121">See also</span></span>

- [<span data-ttu-id="d453d-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="d453d-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
