---
description: '詳細について: ISymUnmanagedAsyncMethodPropertiesWriter::D efineKickoffMethod メソッド'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 7333823bce27eace4e9cb988ac31252743cca952
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790231"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="8d119-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="8d119-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="8d119-104">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="8d119-104">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d119-105">構文</span><span class="sxs-lookup"><span data-stu-id="8d119-105">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d119-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d119-106">Parameters</span></span>  
  
|<span data-ttu-id="8d119-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d119-107">Parameter</span></span>|<span data-ttu-id="8d119-108">説明</span><span class="sxs-lookup"><span data-stu-id="8d119-108">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="8d119-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d119-109">Return Value</span></span>  

 <span data-ttu-id="8d119-110">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="8d119-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d119-111">要件</span><span class="sxs-lookup"><span data-stu-id="8d119-111">Requirements</span></span>  

 <span data-ttu-id="8d119-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8d119-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d119-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d119-113">See also</span></span>

- [<span data-ttu-id="8d119-114">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d119-114">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
