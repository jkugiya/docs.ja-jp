---
description: '詳細については、次のページを参照してください:: いい Appdomain:: GetName メソッド'
title: ICorDebugAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 56995f544e1576534e35b899a659ed409972305f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772433"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="0a596-103">ICorDebugAppDomain::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="0a596-103">ICorDebugAppDomain::GetName Method</span></span>

<span data-ttu-id="0a596-104">アプリケーションドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a596-104">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a596-105">構文</span><span class="sxs-lookup"><span data-stu-id="0a596-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a596-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a596-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="0a596-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0a596-107">[in] The size of the `szName` array.</span></span> <span data-ttu-id="0a596-108">このメソッドをクエリモードにするには、この値を0に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a596-108">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0a596-109">入出力名前のサイズ、またはで実際に返された文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0a596-109">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="0a596-110">クエリモードでは、この値によって、呼び出し元は、名前に割り当てるバッファーの大きさを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="0a596-110">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0a596-111">入出力アプリケーションドメインの名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="0a596-111">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a596-112">解説</span><span class="sxs-lookup"><span data-stu-id="0a596-112">Remarks</span></span>  

 <span data-ttu-id="0a596-113">デバッガーは、 `GetName` メソッドを1回呼び出して、名前に必要なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a596-113">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="0a596-114">デバッガーによってバッファーが割り当てられ、メソッドが2回目に呼び出されてバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0a596-114">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="0a596-115">名前のサイズを取得するための最初の呼び出しは、 *クエリモード* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0a596-115">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a596-116">要件</span><span class="sxs-lookup"><span data-stu-id="0a596-116">Requirements</span></span>  

 <span data-ttu-id="0a596-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a596-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a596-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a596-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a596-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a596-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a596-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a596-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
