---
description: '詳細について: ISymUnmanagedDocument:: HasEmbeddedSource メソッド'
title: ISymUnmanagedDocument::HasEmbeddedSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: fcab83fea65d9a9e483bff9d2d75714c233718eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710128"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="4a3d5-103">ISymUnmanagedDocument::HasEmbeddedSource メソッド</span><span class="sxs-lookup"><span data-stu-id="4a3d5-103">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>

<span data-ttu-id="4a3d5-104">`true`ドキュメントがデバッグシンボルに埋め込まれている場合はを返します。それ以外の場合はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="4a3d5-104">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a3d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="4a3d5-105">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a3d5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a3d5-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="4a3d5-107">入出力ドキュメントにデバッグシンボルに埋め込まれたソースがあるかどうかを示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4a3d5-107">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a3d5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4a3d5-108">Return Value</span></span>  

 <span data-ttu-id="4a3d5-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="4a3d5-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3d5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a3d5-110">See also</span></span>

- [<span data-ttu-id="4a3d5-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a3d5-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
