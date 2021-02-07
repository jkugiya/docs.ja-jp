---
description: '詳細情報: GetScope2 メソッド'
title: GetScope2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 9a68f02a638b58e7a70207d8610607bf24b2b96b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718344"
---
# <a name="getscope2-method"></a><span data-ttu-id="08ad8-103">GetScope2 メソッド</span><span class="sxs-lookup"><span data-stu-id="08ad8-103">GetScope2 Method</span></span>

<span data-ttu-id="08ad8-104">インポートスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="08ad8-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08ad8-105">構文</span><span class="sxs-lookup"><span data-stu-id="08ad8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="08ad8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08ad8-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="08ad8-107">ターゲットアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="08ad8-107">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="08ad8-108">インポート元のファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="08ad8-108">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="08ad8-109">インポートする0から始まるスコープ。</span><span class="sxs-lookup"><span data-stu-id="08ad8-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="08ad8-110">指定されたスコープの [IMetaDataImport2 インターフェイス](../metadata/imetadataimport2-interface.md) インターフェイスへのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08ad8-110">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08ad8-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="08ad8-111">Return Value</span></span>  

 <span data-ttu-id="08ad8-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="08ad8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08ad8-113">要件</span><span class="sxs-lookup"><span data-stu-id="08ad8-113">Requirements</span></span>  

 <span data-ttu-id="08ad8-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="08ad8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ad8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="08ad8-115">See also</span></span>

- [<span data-ttu-id="08ad8-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08ad8-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="08ad8-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08ad8-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="08ad8-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="08ad8-118">ALink API</span></span>](index.md)
