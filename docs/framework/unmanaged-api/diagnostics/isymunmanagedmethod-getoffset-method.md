---
description: '詳細について: ISymUnmanagedMethod:: GetOffset メソッド'
title: ISymUnmanagedMethod::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 3bc7154a47a38fd2cbadc62921f6e57f7901087e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790127"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="05334-103">ISymUnmanagedMethod::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="05334-103">ISymUnmanagedMethod::GetOffset Method</span></span>

<span data-ttu-id="05334-104">ドキュメント内の指定された位置に対応する、このメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="05334-104">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05334-105">構文</span><span class="sxs-lookup"><span data-stu-id="05334-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05334-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05334-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="05334-107">からオフセットが要求されるドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="05334-107">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="05334-108">からオフセットの要求対象となるドキュメント行。</span><span class="sxs-lookup"><span data-stu-id="05334-108">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="05334-109">からオフセットが要求されるドキュメント列。</span><span class="sxs-lookup"><span data-stu-id="05334-109">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="05334-110">入出力オフセットを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="05334-110">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05334-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="05334-111">Return Value</span></span>  

 <span data-ttu-id="05334-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="05334-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05334-113">要件</span><span class="sxs-lookup"><span data-stu-id="05334-113">Requirements</span></span>  

 <span data-ttu-id="05334-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="05334-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05334-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="05334-115">See also</span></span>

- [<span data-ttu-id="05334-116">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05334-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
