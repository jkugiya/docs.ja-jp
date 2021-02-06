---
description: '詳細について: ICorDebugProcess6:: GetCode メソッド'
title: ICorDebugProcess6::GetCode メソッド
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: a7cb71ddb1e65cda37d762a0fba958d413145138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649664"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="2aa49-103">ICorDebugProcess6::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="2aa49-103">ICorDebugProcess6::GetCode Method</span></span>

<span data-ttu-id="2aa49-104">特定のコード アドレスで、マネージド コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2aa49-104">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa49-105">構文</span><span class="sxs-lookup"><span data-stu-id="2aa49-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aa49-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2aa49-106">Parameters</span></span>  

 `codeAddress`  
 <span data-ttu-id="2aa49-107">からマネージコードセグメントの開始アドレスを指定する [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="2aa49-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="2aa49-108">入出力マネージコードのセグメントを表す "" コード "オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2aa49-108">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aa49-109">解説</span><span class="sxs-lookup"><span data-stu-id="2aa49-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2aa49-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2aa49-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aa49-111">要件</span><span class="sxs-lookup"><span data-stu-id="2aa49-111">Requirements</span></span>  

 <span data-ttu-id="2aa49-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aa49-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aa49-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aa49-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aa49-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aa49-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aa49-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aa49-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa49-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2aa49-116">See also</span></span>

- [<span data-ttu-id="2aa49-117">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aa49-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="2aa49-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2aa49-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
