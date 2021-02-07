---
description: '詳細について: ISymUnmanagedENCUpdate:: GetLocalVariables メソッド'
title: ISymUnmanagedENCUpdate::GetLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: bc034603dd6a09ea78dad789e11ea951d65e839b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721464"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="25100-103">ISymUnmanagedENCUpdate::GetLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="25100-103">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="25100-104">ローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="25100-104">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25100-105">構文</span><span class="sxs-lookup"><span data-stu-id="25100-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25100-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25100-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="25100-107">からメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="25100-107">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="25100-108">から `ULONG` パラメーターのサイズを示す `rgLocals` 。</span><span class="sxs-lookup"><span data-stu-id="25100-108">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="25100-109">入出力返される [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="25100-109">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="25100-110">入出力 `ULONG` `rgLocals` ローカルを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25100-110">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25100-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="25100-111">Return Value</span></span>  

 <span data-ttu-id="25100-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="25100-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25100-113">要件</span><span class="sxs-lookup"><span data-stu-id="25100-113">Requirements</span></span>  

 <span data-ttu-id="25100-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="25100-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25100-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="25100-115">See also</span></span>

- [<span data-ttu-id="25100-116">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25100-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
