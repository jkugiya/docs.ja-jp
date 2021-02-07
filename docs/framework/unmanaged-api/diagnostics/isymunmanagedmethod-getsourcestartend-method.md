---
description: '詳細について: ISymUnmanagedMethod:: GetSourceStartEnd メソッド'
title: ISymUnmanagedMethod::GetSourceStartEnd メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 0d247427998970d86c1ad1ec37f5b32a846a6f7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709985"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="7ed13-103">ISymUnmanagedMethod::GetSourceStartEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="7ed13-103">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>

<span data-ttu-id="7ed13-104">このメソッドのソースのドキュメントの開始位置と終了位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="7ed13-104">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="7ed13-105">最初の配列の位置は start で、2番目の配列の位置は末尾です。</span><span class="sxs-lookup"><span data-stu-id="7ed13-105">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed13-106">構文</span><span class="sxs-lookup"><span data-stu-id="7ed13-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ed13-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ed13-107">Parameters</span></span>  

 `docs`  
 <span data-ttu-id="7ed13-108">から開始と終了のソースドキュメント。</span><span class="sxs-lookup"><span data-stu-id="7ed13-108">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="7ed13-109">から対応するソースドキュメントの開始行と終了行。</span><span class="sxs-lookup"><span data-stu-id="7ed13-109">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="7ed13-110">から対応するソースドキュメント内の開始列と終了列。</span><span class="sxs-lookup"><span data-stu-id="7ed13-110">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7ed13-111">[出力] `true` 位置が定義されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="7ed13-111">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ed13-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="7ed13-112">Return Value</span></span>  

 <span data-ttu-id="7ed13-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ed13-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ed13-114">要件</span><span class="sxs-lookup"><span data-stu-id="7ed13-114">Requirements</span></span>  

 <span data-ttu-id="7ed13-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7ed13-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed13-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ed13-116">See also</span></span>

- [<span data-ttu-id="7ed13-117">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ed13-117">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
