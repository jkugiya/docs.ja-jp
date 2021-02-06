---
description: '詳細について: ICLRRuntimeInfo:: BindAsLegacyV2Runtime メソッド'
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 77b340cba18ea86546e1a8f4a17933f09289b1de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637180"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="96148-103">ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド</span><span class="sxs-lookup"><span data-stu-id="96148-103">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="96148-104">すべてのレガシ共通言語ランタイム (CLR) バージョン2アクティブ化ポリシーの決定に現在のランタイムをバインドします。</span><span class="sxs-lookup"><span data-stu-id="96148-104">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96148-105">構文</span><span class="sxs-lookup"><span data-stu-id="96148-105">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="96148-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="96148-106">Return Value</span></span>  

 <span data-ttu-id="96148-107">このメソッドは、次の特定の Hresult を返します。</span><span class="sxs-lookup"><span data-stu-id="96148-107">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="96148-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96148-108">HRESULT</span></span>|<span data-ttu-id="96148-109">説明</span><span class="sxs-lookup"><span data-stu-id="96148-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96148-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="96148-110">S_OK</span></span>|<span data-ttu-id="96148-111">バインドが成功したか、またはこのランタイムが従来の CLR バージョン2アクティブ化ポリシーのランタイムとして既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="96148-111">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="96148-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="96148-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="96148-113">以前の CLR バージョン2のアクティブ化ポリシーに、別のランタイムが既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="96148-113">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96148-114">解説</span><span class="sxs-lookup"><span data-stu-id="96148-114">Remarks</span></span>  

 <span data-ttu-id="96148-115">現在のランタイムが、従来の CLR バージョン2アクティブ化ポリシーの決定 (構成ファイルの要素で属性を使用するなど) に対して既にバインドされている場合 `useLegacyV2RuntimeActivationPolicy` 、このメソッドはエラー結果を返しません。メソッドが従来のアクティブ化ポリシーに正常にバインドされている場合と同じように、結果が S_OK されます。 [ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="96148-115">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96148-116">要件</span><span class="sxs-lookup"><span data-stu-id="96148-116">Requirements</span></span>  

 <span data-ttu-id="96148-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96148-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96148-118">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="96148-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="96148-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="96148-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96148-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96148-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96148-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="96148-121">See also</span></span>

- [<span data-ttu-id="96148-122">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96148-122">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="96148-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96148-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="96148-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="96148-124">Hosting</span></span>](index.md)
- [<span data-ttu-id="96148-125">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="96148-125">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
