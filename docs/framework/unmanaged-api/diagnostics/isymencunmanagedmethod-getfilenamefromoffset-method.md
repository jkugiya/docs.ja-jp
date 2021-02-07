---
description: '詳細について: ISymENCUnmanagedMethod:: GetFileNameFromOffset メソッド'
title: ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 1322e55f115958a2f4b2634dfa25eff127167d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738001"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="66d04-103">ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="66d04-103">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>

<span data-ttu-id="66d04-104">オフセットに関連付けられた行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="66d04-104">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d04-105">構文</span><span class="sxs-lookup"><span data-stu-id="66d04-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66d04-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66d04-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="66d04-107">から `ULONG32` オフセットを格納している。</span><span class="sxs-lookup"><span data-stu-id="66d04-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="66d04-108">から `ULONG32` バッファーのサイズを示す `szName` 。</span><span class="sxs-lookup"><span data-stu-id="66d04-108">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="66d04-109">入出力 `ULONG32` ファイル名を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66d04-109">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="66d04-110">入出力ファイル名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="66d04-110">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66d04-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="66d04-111">Return Value</span></span>  

 <span data-ttu-id="66d04-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="66d04-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66d04-113">要件</span><span class="sxs-lookup"><span data-stu-id="66d04-113">Requirements</span></span>  

 <span data-ttu-id="66d04-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="66d04-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d04-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="66d04-115">See also</span></span>

- [<span data-ttu-id="66d04-116">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66d04-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
