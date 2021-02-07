---
description: '詳細について: ISymUnmanagedMethod:: GetSequencePoints メソッド'
title: ISymUnmanagedMethod::GetSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721295"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="4d5ea-103">ISymUnmanagedMethod::GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="4d5ea-103">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="4d5ea-104">このメソッド内のすべてのシーケンスポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-104">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="4d5ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d5ea-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d5ea-106">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="4d5ea-107">から、、、、、 `ULONG32` およびの各配列のサイズを受け取る `offsets` `documents` `lines` `columns` `endLines` `endColumns` 。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-107">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="4d5ea-108">入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーの長さを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-108">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="4d5ea-109">からシーケンスポイントのメソッドの先頭からの MSIL (Microsoft 中間言語) オフセットを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-109">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="4d5ea-110">からシーケンスポイントが配置されているドキュメントを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-110">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="4d5ea-111">からシーケンスポイントが配置されているドキュメント内の行を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-111">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="4d5ea-112">からシーケンスポイントが配置されているドキュメント内の列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-112">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="4d5ea-113">からシーケンスポイントが終了するドキュメント内の行の配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-113">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="4d5ea-114">からシーケンスポイントが終了するドキュメント内の列の配列。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-114">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d5ea-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="4d5ea-115">Return Value</span></span>  

 <span data-ttu-id="4d5ea-116">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d5ea-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d5ea-117">要件</span><span class="sxs-lookup"><span data-stu-id="4d5ea-117">Requirements</span></span>  

 <span data-ttu-id="4d5ea-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="4d5ea-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5ea-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d5ea-119">See also</span></span>

- [<span data-ttu-id="4d5ea-120">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d5ea-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
