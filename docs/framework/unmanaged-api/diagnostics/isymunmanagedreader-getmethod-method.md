---
description: '詳細について: ISymUnmanagedReader:: GetMethod メソッド'
title: ISymUnmanagedReader::GetMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 7c0bb65840a3bc1c9450ad29fa8438cdb0377a16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689496"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="3ac78-103">ISymUnmanagedReader::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="3ac78-103">ISymUnmanagedReader::GetMethod Method</span></span>

<span data-ttu-id="3ac78-104">メソッドトークンを指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="3ac78-104">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac78-105">構文</span><span class="sxs-lookup"><span data-stu-id="3ac78-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ac78-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ac78-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="3ac78-107">からメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="3ac78-107">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3ac78-108">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3ac78-108">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ac78-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ac78-109">Return Value</span></span>  

 <span data-ttu-id="3ac78-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ac78-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ac78-111">要件</span><span class="sxs-lookup"><span data-stu-id="3ac78-111">Requirements</span></span>  

 <span data-ttu-id="3ac78-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="3ac78-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac78-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ac78-113">See also</span></span>

- [<span data-ttu-id="3ac78-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ac78-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
