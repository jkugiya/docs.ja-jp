---
description: '詳細情報: CreateICeeFileGen 関数'
title: CreateICeeFileGen 関数
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 10aefaad4dd1173e4ef55f727371bab508e2d40c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716930"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="672ac-103">CreateICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="672ac-103">CreateICeeFileGen Function</span></span>

<span data-ttu-id="672ac-104">[ICeeFileGen](iceefilegen-class.md)オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="672ac-104">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="672ac-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="672ac-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="672ac-106">構文</span><span class="sxs-lookup"><span data-stu-id="672ac-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="672ac-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="672ac-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="672ac-108">入出力新しいオブジェクトのアドレスへのポインター `ICeeFileGen` 。</span><span class="sxs-lookup"><span data-stu-id="672ac-108">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="672ac-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="672ac-109">Return Value</span></span>  

 <span data-ttu-id="672ac-110">このメソッドは、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="672ac-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="672ac-111">解説</span><span class="sxs-lookup"><span data-stu-id="672ac-111">Remarks</span></span>  

 <span data-ttu-id="672ac-112">`ICeeFileGen`オブジェクトは、共通言語ランタイム (CLR) の移植可能な実行可能 (PE) ファイルを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="672ac-112">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="672ac-113">完了したら、 [DestroyICeeFileGen](destroyiceefilegen-function.md) 関数を呼び出してオブジェクトを破棄し `ICeeFileGen` ます。</span><span class="sxs-lookup"><span data-stu-id="672ac-113">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="672ac-114">要件</span><span class="sxs-lookup"><span data-stu-id="672ac-114">Requirements</span></span>  

 <span data-ttu-id="672ac-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="672ac-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="672ac-116">**ヘッダー:** ICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="672ac-116">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="672ac-117">**ライブラリ:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="672ac-117">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="672ac-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="672ac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672ac-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="672ac-119">See also</span></span>

- [<span data-ttu-id="672ac-120">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="672ac-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
