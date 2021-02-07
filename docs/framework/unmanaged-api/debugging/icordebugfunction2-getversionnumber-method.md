---
description: '詳細について: ICorDebugFunction2:: GetVersionNumber メソッド'
title: ICorDebugFunction2::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 7a703789099b82121c65214d6b1929e354405c8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692213"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="c4546-103">ICorDebugFunction2::GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="c4546-103">ICorDebugFunction2::GetVersionNumber Method</span></span>

<span data-ttu-id="c4546-104">この関数のエディットコンティニュバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c4546-104">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4546-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4546-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4546-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4546-106">Parameters</span></span>  

 `pnVersion`  
 <span data-ttu-id="c4546-107">入出力この ICorDebugFunction2 オブジェクトによって表される関数のバージョン番号である整数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="c4546-107">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4546-108">解説</span><span class="sxs-lookup"><span data-stu-id="c4546-108">Remarks</span></span>  

 <span data-ttu-id="c4546-109">ランタイムは、デバッグセッション中に各モジュールに対して行われた編集の数を追跡します。</span><span class="sxs-lookup"><span data-stu-id="c4546-109">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="c4546-110">関数のバージョン番号は、関数を導入した編集の数を1つ超えています。</span><span class="sxs-lookup"><span data-stu-id="c4546-110">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="c4546-111">関数の元のバージョンは、バージョン1です。</span><span class="sxs-lookup"><span data-stu-id="c4546-111">The function's original version is version 1.</span></span> <span data-ttu-id="c4546-112">この値は、そのモジュールで [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md) が呼び出されるたびに、モジュールに対してインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="c4546-112">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="c4546-113">したがって、関数の本体がの最初の呼び出しと3番目の呼び出しで置き換えられた場合、は `ICorDebugModule2::ApplyChanges` 、 `GetVersionNumber` その関数についてバージョン1、2、または4を返すことがありますが、バージョン3は返されません。</span><span class="sxs-lookup"><span data-stu-id="c4546-113">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="c4546-114">(この関数にはバージョン3はありません)。</span><span class="sxs-lookup"><span data-stu-id="c4546-114">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="c4546-115">バージョン番号は、モジュールごとに個別に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="c4546-115">The version number is tracked separately for each module.</span></span> <span data-ttu-id="c4546-116">したがって、モジュール1で4つの編集を実行し、モジュール2では何も実行しない場合、モジュール1の次の編集では、モジュール1のすべての編集された関数にバージョン番号6が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c4546-116">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="c4546-117">同じ編集がモジュール2の場合、モジュール2の関数のバージョン番号は2になります。</span><span class="sxs-lookup"><span data-stu-id="c4546-117">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="c4546-118">メソッドによって取得されたバージョン番号 `GetVersionNumber` が、 [GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)で取得したバージョン番号よりも小さい場合があります。</span><span class="sxs-lookup"><span data-stu-id="c4546-118">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="c4546-119">[コード:: GetVersionNumber](icordebugcode-getversionnumber-method.md)メソッドは、と同じ操作を実行し `ICorDebugFunction2::GetVersionNumber` ます。</span><span class="sxs-lookup"><span data-stu-id="c4546-119">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4546-120">要件</span><span class="sxs-lookup"><span data-stu-id="c4546-120">Requirements</span></span>  

 <span data-ttu-id="c4546-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4546-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4546-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4546-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4546-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4546-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4546-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4546-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
