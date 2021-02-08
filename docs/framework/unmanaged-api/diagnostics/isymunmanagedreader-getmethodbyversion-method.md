---
description: '詳細について: ISymUnmanagedReader:: GetMethodByVersion メソッド'
title: ISymUnmanagedReader::GetMethodByVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 6b2fa3ff3af91d59bb79029d039e5656610bebff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772069"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="71a73-103">ISymUnmanagedReader::GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="71a73-103">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="71a73-104">メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="71a73-104">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="71a73-105">バージョン番号は1から始まり、編集とコピー操作の結果としてメソッドが変更されるたびに増分されます。</span><span class="sxs-lookup"><span data-stu-id="71a73-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a73-106">構文</span><span class="sxs-lookup"><span data-stu-id="71a73-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71a73-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71a73-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="71a73-108">からメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="71a73-108">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="71a73-109">からメソッドのバージョン。</span><span class="sxs-lookup"><span data-stu-id="71a73-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="71a73-110">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71a73-110">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71a73-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="71a73-111">Return Value</span></span>  

 <span data-ttu-id="71a73-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="71a73-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71a73-113">要件</span><span class="sxs-lookup"><span data-stu-id="71a73-113">Requirements</span></span>  

 <span data-ttu-id="71a73-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="71a73-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a73-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="71a73-115">See also</span></span>

- [<span data-ttu-id="71a73-116">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71a73-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
