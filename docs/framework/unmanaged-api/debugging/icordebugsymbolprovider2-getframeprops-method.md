---
description: '詳細について: ICorDebugSymbolProvider2:: Getフレーム Props メソッド'
title: ICorDebugSymbolProvider2::GetFrameProps メソッド
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659557"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="c4ad1-103">ICorDebugSymbolProvider2::GetFrameProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c4ad1-103">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="c4ad1-104">メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-104">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ad1-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4ad1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ad1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4ad1-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="c4ad1-107">[in] コード相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-107">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="c4ad1-108">[out] メソッドの開始相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-108">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="c4ad1-109">[out] フレームの開始相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-109">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4ad1-110">解説</span><span class="sxs-lookup"><span data-stu-id="c4ad1-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4ad1-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ad1-112">要件</span><span class="sxs-lookup"><span data-stu-id="c4ad1-112">Requirements</span></span>  

 <span data-ttu-id="c4ad1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ad1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4ad1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4ad1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4ad1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4ad1-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ad1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ad1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-117">See also</span></span>

- [<span data-ttu-id="c4ad1-118">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4ad1-118">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="c4ad1-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4ad1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
