---
description: '詳細情報: GetScope メソッド'
title: GetScope メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: cdebda457573e70755b49798ae86eae8f076216b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718360"
---
# <a name="getscope-method"></a><span data-ttu-id="77172-103">GetScope メソッド</span><span class="sxs-lookup"><span data-stu-id="77172-103">GetScope Method</span></span>

<span data-ttu-id="77172-104">インポートスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="77172-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77172-105">構文</span><span class="sxs-lookup"><span data-stu-id="77172-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="77172-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77172-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="77172-107">インポート先のアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="77172-107">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="77172-108">インポート元のファイルの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="77172-108">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="77172-109">インポートする0から始まるスコープ。</span><span class="sxs-lookup"><span data-stu-id="77172-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="77172-110">スコープの [IMetaDataImport インターフェイス](../metadata/imetadataimport-interface.md) インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="77172-110">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77172-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="77172-111">Return Value</span></span>  

 <span data-ttu-id="77172-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="77172-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77172-113">要件</span><span class="sxs-lookup"><span data-stu-id="77172-113">Requirements</span></span>  

 <span data-ttu-id="77172-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="77172-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77172-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="77172-115">See also</span></span>

- [<span data-ttu-id="77172-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77172-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="77172-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77172-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="77172-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="77172-118">ALink API</span></span>](index.md)
