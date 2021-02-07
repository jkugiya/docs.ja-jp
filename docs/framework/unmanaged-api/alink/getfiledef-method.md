---
description: '詳細情報: GetFileDef メソッド'
title: GetFileDef メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 5d44336e686ca565f468fb95ce5290ee41d5e16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718448"
---
# <a name="getfiledef-method"></a><span data-ttu-id="2328d-103">GetFileDef メソッド</span><span class="sxs-lookup"><span data-stu-id="2328d-103">GetFileDef Method</span></span>

<span data-ttu-id="2328d-104">ALink によって割り当てられたトークンとは対照的に、メタデータで使用される実際の FileDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2328d-104">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2328d-105">構文</span><span class="sxs-lookup"><span data-stu-id="2328d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2328d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2328d-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="2328d-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="2328d-107">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="2328d-108">AddFile メソッドまたは AddImport メソッドから取得された追加ファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="2328d-108">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="2328d-109">FileDef トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2328d-109">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2328d-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="2328d-110">Return Value</span></span>  

 <span data-ttu-id="2328d-111">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2328d-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2328d-112">要件</span><span class="sxs-lookup"><span data-stu-id="2328d-112">Requirements</span></span>  

 <span data-ttu-id="2328d-113">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2328d-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2328d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2328d-114">See also</span></span>

- [<span data-ttu-id="2328d-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2328d-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2328d-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2328d-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2328d-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="2328d-117">ALink API</span></span>](index.md)
