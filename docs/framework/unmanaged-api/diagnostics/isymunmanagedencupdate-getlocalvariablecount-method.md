---
description: '詳細について: ISymUnmanagedENCUpdate:: GetLocalVariableCount メソッド'
title: ISymUnmanagedENCUpdate::GetLocalVariableCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: ab75ba0b0dda5722aebdbdc8b9a242cc90b0ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790153"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="2c78c-103">ISymUnmanagedENCUpdate::GetLocalVariableCount メソッド</span><span class="sxs-lookup"><span data-stu-id="2c78c-103">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>

<span data-ttu-id="2c78c-104">ローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="2c78c-104">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c78c-105">構文</span><span class="sxs-lookup"><span data-stu-id="2c78c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c78c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c78c-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="2c78c-107">からメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="2c78c-107">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="2c78c-108">入出力 `ULONG32` ローカル変数の数を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2c78c-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c78c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2c78c-109">Return Value</span></span>  

 <span data-ttu-id="2c78c-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c78c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c78c-111">要件</span><span class="sxs-lookup"><span data-stu-id="2c78c-111">Requirements</span></span>  

 <span data-ttu-id="2c78c-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="2c78c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c78c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c78c-113">See also</span></span>

- [<span data-ttu-id="2c78c-114">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c78c-114">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
