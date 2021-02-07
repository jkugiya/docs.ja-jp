---
description: '詳細情報: IValidator インターフェイス'
title: IValidator インターフェイス
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: bc18b68d0e9a0e978789ab92afaed28751925870
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680097"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="fad95-103">IValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fad95-103">IValidator Interface</span></span>

<span data-ttu-id="fad95-104">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fad95-104">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fad95-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fad95-105">Methods</span></span>  
  
|<span data-ttu-id="fad95-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fad95-106">Method</span></span>|<span data-ttu-id="fad95-107">説明</span><span class="sxs-lookup"><span data-stu-id="fad95-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fad95-108">検証</span><span class="sxs-lookup"><span data-stu-id="fad95-108">Validate</span></span>|<span data-ttu-id="fad95-109">指定された PE または Microsoft 中間言語 (MSIL) ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="fad95-109">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="fad95-110">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="fad95-110">FormatEventInfo</span></span>|<span data-ttu-id="fad95-111">指定した検証エラーに対応するエラーメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="fad95-111">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fad95-112">要件</span><span class="sxs-lookup"><span data-stu-id="fad95-112">Requirements</span></span>  

 <span data-ttu-id="fad95-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fad95-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fad95-114">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="fad95-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="fad95-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fad95-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fad95-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fad95-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad95-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fad95-117">See also</span></span>

- [<span data-ttu-id="fad95-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fad95-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fad95-119">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="fad95-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
