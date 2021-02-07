---
description: '詳細について: ISymUnmanagedReader:: GetMethodVersion メソッド'
title: ISymUnmanagedReader::GetMethodVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: 027f65f858aab3e4ad0bc0bfbffd91f6118b80b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764022"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="e07da-103">ISymUnmanagedReader::GetMethodVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="e07da-103">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="e07da-104">メソッドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="e07da-104">Gets the method version.</span></span> <span data-ttu-id="e07da-105">メソッドのバージョンは1から始まり、メソッドが再コンパイルされるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="e07da-105">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="e07da-106">再コンパイルは、メソッドを変更せずに発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e07da-106">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07da-107">構文</span><span class="sxs-lookup"><span data-stu-id="e07da-107">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07da-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e07da-108">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="e07da-109">からバージョンを取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="e07da-109">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="e07da-110">入出力メソッドのバージョンを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e07da-110">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e07da-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="e07da-111">Return Value</span></span>  

 <span data-ttu-id="e07da-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e07da-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07da-113">要件</span><span class="sxs-lookup"><span data-stu-id="e07da-113">Requirements</span></span>  

 <span data-ttu-id="e07da-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e07da-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07da-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e07da-115">See also</span></span>

- [<span data-ttu-id="e07da-116">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e07da-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
