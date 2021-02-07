---
description: '詳細について: ISymUnmanagedSourceServerModule:: GetSourceServerData メソッド'
title: ISymUnmanagedSourceServerModule::GetSourceServerData メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: cdba764534000273170ccd693a3fbc7b5df9c3c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763164"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="09e5b-103">ISymUnmanagedSourceServerModule::GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="09e5b-103">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>

<span data-ttu-id="09e5b-104">モジュールのソースサーバーデータを返します。</span><span class="sxs-lookup"><span data-stu-id="09e5b-104">Returns the source server data for the module.</span></span> <span data-ttu-id="09e5b-105">呼び出し元は、を使用してリソースを解放する必要があり `CoTaskMemFree` ます。</span><span class="sxs-lookup"><span data-stu-id="09e5b-105">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e5b-106">構文</span><span class="sxs-lookup"><span data-stu-id="09e5b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09e5b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09e5b-107">Parameters</span></span>  

 `pDataByteCount`  
 <span data-ttu-id="09e5b-108">入出力 `ULONG32` 転送元サーバーのデータのサイズ (バイト単位) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09e5b-108">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="09e5b-109">入出力戻り値へのポインター `pDataByteCount` 。</span><span class="sxs-lookup"><span data-stu-id="09e5b-109">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09e5b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="09e5b-110">Return Value</span></span>  

 <span data-ttu-id="09e5b-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="09e5b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e5b-112">要件</span><span class="sxs-lookup"><span data-stu-id="09e5b-112">Requirements</span></span>  

 <span data-ttu-id="09e5b-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="09e5b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e5b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="09e5b-114">See also</span></span>

- [<span data-ttu-id="09e5b-115">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09e5b-115">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
