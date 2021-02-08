---
description: 詳細については、「IMetaDataValidate インターフェイス」を参照してください。
title: IMetaDataValidate インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataValidate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate
helpviewer_keywords:
- IMetaDataValidate interface [.NET Framework metadata]
ms.assetid: db98608a-e85c-4f50-9d7b-5f57a426ddb6
topic_type:
- apiref
ms.openlocfilehash: fbdbdf6880d7cb5ee6d4c21df587eb63b26b456e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799218"
---
# <a name="imetadatavalidate-interface"></a><span data-ttu-id="0a504-103">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a504-103">IMetaDataValidate Interface</span></span>

<span data-ttu-id="0a504-104">メタデータ署名を検証するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0a504-104">Provides methods to validate metadata signatures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a504-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a504-105">Methods</span></span>  
  
|<span data-ttu-id="0a504-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a504-106">Method</span></span>|<span data-ttu-id="0a504-107">説明</span><span class="sxs-lookup"><span data-stu-id="0a504-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a504-108">ValidateMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="0a504-108">ValidateMetaData Method</span></span>](imetadatavalidate-validatemetadata-method.md)|<span data-ttu-id="0a504-109">現在のメタデータ スコープ内にあるオブジェクトのメタデータ署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="0a504-109">Validates the metadata signatures of the objects in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0a504-110">ValidatorInit メソッド</span><span class="sxs-lookup"><span data-stu-id="0a504-110">ValidatorInit Method</span></span>](imetadatavalidate-validatorinit-method.md)|<span data-ttu-id="0a504-111">現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。</span><span class="sxs-lookup"><span data-stu-id="0a504-111">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a504-112">要件</span><span class="sxs-lookup"><span data-stu-id="0a504-112">Requirements</span></span>  

 <span data-ttu-id="0a504-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a504-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a504-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0a504-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a504-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a504-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a504-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a504-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a504-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a504-117">See also</span></span>

- [<span data-ttu-id="0a504-118">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a504-118">Metadata Interfaces</span></span>](metadata-interfaces.md)
