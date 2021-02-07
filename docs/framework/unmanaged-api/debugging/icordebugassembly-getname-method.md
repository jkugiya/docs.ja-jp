---
description: '詳細については、次を参照してください: いい Assembly:: GetName メソッド'
title: ICorDebugAssembly::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: c2ffa910eaf97c5539a33dbcd3486b7dfb117b51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711987"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="1c804-103">ICorDebugAssembly::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="1c804-103">ICorDebugAssembly::GetName Method</span></span>

<span data-ttu-id="1c804-104">このインスタンスが表すアセンブリの名前を取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="1c804-104">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c804-105">構文</span><span class="sxs-lookup"><span data-stu-id="1c804-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c804-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c804-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="1c804-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1c804-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1c804-108">入出力名前の実際の長さを指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1c804-108">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1c804-109">入出力名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="1c804-109">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c804-110">解説</span><span class="sxs-lookup"><span data-stu-id="1c804-110">Remarks</span></span>  

 <span data-ttu-id="1c804-111">メソッドは、 `GetName` アセンブリの完全なパスとファイル名を返します。</span><span class="sxs-lookup"><span data-stu-id="1c804-111">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c804-112">要件</span><span class="sxs-lookup"><span data-stu-id="1c804-112">Requirements</span></span>  

 <span data-ttu-id="1c804-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c804-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c804-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c804-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c804-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c804-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c804-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c804-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
