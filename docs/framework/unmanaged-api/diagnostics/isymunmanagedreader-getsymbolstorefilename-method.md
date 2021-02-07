---
description: '詳細について: ISymUnmanagedReader:: Getシンボル Storefilename メソッド'
title: ISymUnmanagedReader::GetSymbolStoreFileName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: 5cbb33a39cf2e93eab64d5f1f1fefc5ceba1d418
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763944"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="6f3e4-103">ISymUnmanagedReader::GetSymbolStoreFileName メソッド</span><span class="sxs-lookup"><span data-stu-id="6f3e4-103">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="6f3e4-104">シンボルストアのディスク上のファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-104">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f3e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f3e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f3e4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f3e4-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="6f3e4-107">からバッファーのサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-107">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6f3e4-108">入出力Null 終了を含む、で返された名前の長さを受け取る変数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-108">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="6f3e4-109">入出力シンボルストアのファイル名を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-109">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f3e4-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f3e4-110">Return Value</span></span>  

 <span data-ttu-id="6f3e4-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f3e4-112">要件</span><span class="sxs-lookup"><span data-stu-id="6f3e4-112">Requirements</span></span>  

 <span data-ttu-id="6f3e4-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="6f3e4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3e4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f3e4-114">See also</span></span>

- [<span data-ttu-id="6f3e4-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f3e4-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
