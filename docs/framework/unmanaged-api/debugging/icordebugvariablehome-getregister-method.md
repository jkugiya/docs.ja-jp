---
description: 詳細については、次のページを参照してください
title: 'いい変数 Home:: GetRegister メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: c394d455048cf7451b8320ed72a6aa7adfb3518e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790660"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="fa676-103">いい変数 Home:: GetRegister メソッド</span><span class="sxs-lookup"><span data-stu-id="fa676-103">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="fa676-104">の場所の種類がである変数 `VLT_REGISTER` と、の場所の種類がの変数の基本レジスタを含むレジスタを取得し `VLT_REGISTER_RELATIVE` ます。</span><span class="sxs-lookup"><span data-stu-id="fa676-104">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa676-105">構文</span><span class="sxs-lookup"><span data-stu-id="fa676-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa676-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa676-106">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="fa676-107">入出力の場所の種類がである変数のレジスタ、 `VLT_REGISTER` およびの場所の種類がの変数の基本レジスタを示す CorDebugRegister 列挙値 `VLT_REGISTER_RELATIVE` 。</span><span class="sxs-lookup"><span data-stu-id="fa676-107">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa676-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fa676-108">Return Value</span></span>  

 <span data-ttu-id="fa676-109">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="fa676-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="fa676-110">値</span><span class="sxs-lookup"><span data-stu-id="fa676-110">Value</span></span>|<span data-ttu-id="fa676-111">説明</span><span class="sxs-lookup"><span data-stu-id="fa676-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="fa676-112">変数は、引数で指定されたレジスタにあり `pRegister` ます。</span><span class="sxs-lookup"><span data-stu-id="fa676-112">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="fa676-113">変数がレジスタまたはレジスタの相対位置にありません。</span><span class="sxs-lookup"><span data-stu-id="fa676-113">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa676-114">要件</span><span class="sxs-lookup"><span data-stu-id="fa676-114">Requirements</span></span>  

 <span data-ttu-id="fa676-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa676-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa676-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa676-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa676-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa676-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa676-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa676-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa676-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa676-119">See also</span></span>

- [<span data-ttu-id="fa676-120">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fa676-120">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="fa676-121">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa676-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
