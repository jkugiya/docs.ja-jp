---
description: '詳細について: ISymUnmanagedReader2:: GetSymAttributePreRemap メソッド'
title: ISymUnmanagedReader2::GetSymAttributePreRemap メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 843a3d2d2a568fdff83d2e416fff426daad14645
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763632"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="47b48-103">ISymUnmanagedReader2::GetSymAttributePreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="47b48-103">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="47b48-104">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="47b48-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="47b48-105">メタデータのカスタム属性とは異なり、これらの属性はシンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="47b48-105">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b48-106">構文</span><span class="sxs-lookup"><span data-stu-id="47b48-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47b48-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47b48-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="47b48-108">から親のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="47b48-108">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="47b48-109">から名前を格納し `WCHAR` ているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="47b48-109">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="47b48-110">から `ULONG32` 配列のサイズを示す `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="47b48-110">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="47b48-111">入出力 `ULONG32` 属性バイトを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="47b48-111">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="47b48-112">入出力属性バイトを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="47b48-112">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47b48-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="47b48-113">Return Value</span></span>  

 <span data-ttu-id="47b48-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="47b48-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b48-115">要件</span><span class="sxs-lookup"><span data-stu-id="47b48-115">Requirements</span></span>  

 <span data-ttu-id="47b48-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="47b48-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b48-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="47b48-117">See also</span></span>

- [<span data-ttu-id="47b48-118">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47b48-118">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
