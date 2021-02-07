---
description: '詳細については、次のページを参照してください: GetOffset メソッド'
title: 'いい変数 Home:: GetOffset メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 48b57856d2825dd2ea9328064a28783b4b36029b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728770"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="b7b74-103">いい変数 Home:: GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="b7b74-103">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="b7b74-104">変数の基本レジスタからのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b7b74-104">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b74-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7b74-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7b74-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7b74-106">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="b7b74-107">入出力基本レジスタからのオフセット。</span><span class="sxs-lookup"><span data-stu-id="b7b74-107">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7b74-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b7b74-108">Return Value</span></span>  

 <span data-ttu-id="b7b74-109">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="b7b74-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="b7b74-110">値</span><span class="sxs-lookup"><span data-stu-id="b7b74-110">Value</span></span>|<span data-ttu-id="b7b74-111">説明</span><span class="sxs-lookup"><span data-stu-id="b7b74-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b7b74-112">変数は、レジスタ相対メモリの場所にあります。</span><span class="sxs-lookup"><span data-stu-id="b7b74-112">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b7b74-113">変数がレジスタ相対メモリ位置にありません。</span><span class="sxs-lookup"><span data-stu-id="b7b74-113">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7b74-114">要件</span><span class="sxs-lookup"><span data-stu-id="b7b74-114">Requirements</span></span>  

 <span data-ttu-id="b7b74-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7b74-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b74-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7b74-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7b74-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7b74-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7b74-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b74-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b74-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7b74-119">See also</span></span>

- [<span data-ttu-id="b7b74-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7b74-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
