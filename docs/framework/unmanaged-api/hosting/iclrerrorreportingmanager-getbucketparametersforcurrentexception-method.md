---
description: '詳細について: ICLRErrorReportingManager:: GetBucketParametersForCurrentException メソッド'
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: ba2b6cf1215e5d57f608a76a870b0a9c846ee8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689405"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="10e43-103">ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="10e43-103">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>

<span data-ttu-id="10e43-104">呼び出し元のスレッドで現在の例外の Watson バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="10e43-104">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="10e43-105">*バケット* は、同じコード障害に関連するエラーデータのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="10e43-105">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="10e43-106">*Watson* は、例外に関連付けられているデータを収集および分析するための一連のテクノロジを指します。</span><span class="sxs-lookup"><span data-stu-id="10e43-106">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e43-107">構文</span><span class="sxs-lookup"><span data-stu-id="10e43-107">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10e43-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10e43-108">Parameters</span></span>  

 `pParams`  
 <span data-ttu-id="10e43-109">入出力例外のエラーデータを格納している [BucketParameters](bucketparameters-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="10e43-109">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e43-110">要件</span><span class="sxs-lookup"><span data-stu-id="10e43-110">Requirements</span></span>  

 <span data-ttu-id="10e43-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10e43-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10e43-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="10e43-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10e43-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="10e43-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10e43-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10e43-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e43-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="10e43-115">See also</span></span>

- [<span data-ttu-id="10e43-116">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10e43-116">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
