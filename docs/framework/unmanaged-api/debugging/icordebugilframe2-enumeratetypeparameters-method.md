---
description: '詳細について: ICorDebugILFrame2:: EnumerateTypeParameters メソッド'
title: ICorDebugILFrame2::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 34f305b7793e4909318ae2301d72e2af7c12f2c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791292"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="86ab1-103">ICorDebugILFrame2::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="86ab1-103">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="86ab1-104">このフレームのパラメーターを格納している、テキスト型の型の列挙体オブジェクトを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="86ab1-104">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ab1-105">構文</span><span class="sxs-lookup"><span data-stu-id="86ab1-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86ab1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86ab1-106">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="86ab1-107">型パラメーターの列挙を可能にする、テキスト型のインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86ab1-107">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="86ab1-108">型パラメーターの一覧には、クラス型パラメーター (存在する場合) と、その後にメソッド型パラメーター (存在する場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="86ab1-108">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86ab1-109">解説</span><span class="sxs-lookup"><span data-stu-id="86ab1-109">Remarks</span></span>  

 <span data-ttu-id="86ab1-110">[IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md)メソッドを使用して、このリストに含まれるクラス型パラメーターとメソッド型パラメーターの数を確認します。</span><span class="sxs-lookup"><span data-stu-id="86ab1-110">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="86ab1-111">型パラメーターは常に使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="86ab1-111">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86ab1-112">要件</span><span class="sxs-lookup"><span data-stu-id="86ab1-112">Requirements</span></span>  

 <span data-ttu-id="86ab1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ab1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86ab1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86ab1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86ab1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86ab1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86ab1-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ab1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
