---
description: '詳細について: ISymUnmanagedReader:: GetSymAttribute メソッド'
title: ISymUnmanagedReader::GetSymAttribute メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: cd1c453e9f2ef68799fc5eccf1288a7665c5cfdf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763970"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="60931-103">ISymUnmanagedReader::GetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="60931-103">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="60931-104">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="60931-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="60931-105">メタデータのカスタム属性とは異なり、これらのカスタム属性はシンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="60931-105">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60931-106">構文</span><span class="sxs-lookup"><span data-stu-id="60931-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60931-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60931-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="60931-108">から属性を要求する対象のオブジェクトのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="60931-108">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="60931-109">から取得する属性を示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60931-109">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="60931-110">[in] `buffer` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="60931-110">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="60931-111">入出力属性データの長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60931-111">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="60931-112">入出力属性データを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60931-112">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60931-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="60931-113">Return Value</span></span>  

 <span data-ttu-id="60931-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="60931-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60931-115">要件</span><span class="sxs-lookup"><span data-stu-id="60931-115">Requirements</span></span>  

 <span data-ttu-id="60931-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="60931-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60931-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="60931-117">See also</span></span>

- [<span data-ttu-id="60931-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60931-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
