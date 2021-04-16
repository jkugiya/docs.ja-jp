---
description: '詳細情報: ICLRValidator インターフェイス'
title: ICLRValidator インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: 72ff94915d35967b6a8a87b022789ca697f61711
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636755"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="ca492-103">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca492-103">ICLRValidator Interface</span></span>

<span data-ttu-id="ca492-104">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ca492-104">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca492-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca492-105">Methods</span></span>  
  
|<span data-ttu-id="ca492-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca492-106">Method</span></span>|<span data-ttu-id="ca492-107">説明</span><span class="sxs-lookup"><span data-stu-id="ca492-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca492-108">FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="ca492-108">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="ca492-109">指定された検証エラーに関する詳細メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="ca492-109">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="ca492-110">Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="ca492-110">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="ca492-111">指定されたファイル内のポータブル実行可能または Microsoft 中間言語 (MSIL) を検証します。</span><span class="sxs-lookup"><span data-stu-id="ca492-111">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca492-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="ca492-112">Requirements</span></span>  

 <span data-ttu-id="ca492-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca492-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca492-114">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="ca492-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ca492-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="ca492-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca492-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca492-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca492-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca492-117">See also</span></span>

- [<span data-ttu-id="ca492-118">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca492-118">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="ca492-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca492-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ca492-120">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="ca492-120">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
