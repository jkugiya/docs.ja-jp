---
description: 詳細については、「CorDebugCodeInvokePurpose の列挙」を参照してください。
title: CorDebugCodeInvokePurpose 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 1402343cc15e451975567564e6ce353900454bf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801723"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="2b9e6-103">CorDebugCodeInvokePurpose 列挙体</span><span class="sxs-lookup"><span data-stu-id="2b9e6-103">CorDebugCodeInvokePurpose Enumeration</span></span>

<span data-ttu-id="2b9e6-104">エクスポートされた関数がマネージド コードを呼び出す理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-104">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b9e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b9e6-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="2b9e6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2b9e6-106">Members</span></span>  
  
|<span data-ttu-id="2b9e6-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="2b9e6-107">Member</span></span>|<span data-ttu-id="2b9e6-108">説明</span><span class="sxs-lookup"><span data-stu-id="2b9e6-108">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="2b9e6-109">None または不明です。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-109">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="2b9e6-110">マネージド コードは、逆 p-invoke などのすべてのマネージド エントリ ポイントを実行します。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-110">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="2b9e6-111">より詳細な目的は、ランタイムによって認識されません。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-111">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="2b9e6-112">マネージド コードは、静的コンストラクターを実行します。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-112">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="2b9e6-113">マネージド コードは、呼び出されたいくつかのインターフェイス メソッドの実装を実行します。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-113">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b9e6-114">解説</span><span class="sxs-lookup"><span data-stu-id="2b9e6-114">Remarks</span></span>  

 <span data-ttu-id="2b9e6-115">この列挙体は、マネージコードのステップ実行に関する情報を提供するために、 [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-115">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b9e6-116">この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b9e6-117">要件</span><span class="sxs-lookup"><span data-stu-id="2b9e6-117">Requirements</span></span>  

 <span data-ttu-id="2b9e6-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b9e6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b9e6-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b9e6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b9e6-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b9e6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b9e6-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b9e6-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b9e6-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b9e6-122">See also</span></span>

- [<span data-ttu-id="2b9e6-123">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2b9e6-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="2b9e6-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2b9e6-124">Debugging</span></span>](index.md)
