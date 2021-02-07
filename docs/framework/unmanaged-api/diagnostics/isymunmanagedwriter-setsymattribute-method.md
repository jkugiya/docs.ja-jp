---
description: '詳細について: ISymUnmanagedWriter:: SetSymAttribute メソッド'
title: ISymUnmanagedWriter::SetSymAttribute メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 0509e6430646fa67112b29d30d5053eb4a541415
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761994"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="c7ea5-103">ISymUnmanagedWriter::SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="c7ea5-103">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="c7ea5-104">名前に基づいてカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-104">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="c7ea5-105">これらの属性は、メタデータのカスタム属性とは異なり、シンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-105">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ea5-106">構文</span><span class="sxs-lookup"><span data-stu-id="c7ea5-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7ea5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7ea5-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="c7ea5-108">から属性を定義するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-108">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="c7ea5-109">から `WCHAR` 属性名を格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-109">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="c7ea5-110">から `ULONG32` 配列のサイズを示す `data` 。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-110">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="c7ea5-111">から属性値。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-111">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7ea5-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7ea5-112">Return Value</span></span>  

 <span data-ttu-id="c7ea5-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7ea5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7ea5-114">要件</span><span class="sxs-lookup"><span data-stu-id="c7ea5-114">Requirements</span></span>  

 <span data-ttu-id="c7ea5-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c7ea5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ea5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7ea5-116">See also</span></span>

- [<span data-ttu-id="c7ea5-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7ea5-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
