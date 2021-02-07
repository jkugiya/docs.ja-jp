---
description: '詳細情報: IMetaDataDispenserEx:: GetOption メソッド'
title: IMetaDataDispenserEx::GetOption メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: cf52a251c3c0e0485558a150b727d58eeae81995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753550"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="0764c-103">IMetaDataDispenserEx::GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="0764c-103">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="0764c-104">現在のメタデータスコープの指定したオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0764c-104">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="0764c-105">オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="0764c-105">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0764c-106">構文</span><span class="sxs-lookup"><span data-stu-id="0764c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0764c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0764c-107">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="0764c-108">から取得するオプションを指定する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0764c-108">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="0764c-109">サポートされている Guid の一覧については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0764c-109">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0764c-110">入出力返されたオプションの値。</span><span class="sxs-lookup"><span data-stu-id="0764c-110">[out] The value of the returned option.</span></span> <span data-ttu-id="0764c-111">この値の型は、指定されたオプションの型のバリアントになります。</span><span class="sxs-lookup"><span data-stu-id="0764c-111">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0764c-112">解説</span><span class="sxs-lookup"><span data-stu-id="0764c-112">Remarks</span></span>  

 <span data-ttu-id="0764c-113">次の一覧は、このメソッドでサポートされている Guid を示しています。</span><span class="sxs-lookup"><span data-stu-id="0764c-113">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="0764c-114">説明については、 [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0764c-114">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="0764c-115">`optionId`がこのリストに含まれていない場合、このメソッドは HRESULT を返し `E_INVALIDARG` ます。パラメーターが正しくないことを示します。</span><span class="sxs-lookup"><span data-stu-id="0764c-115">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="0764c-116">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="0764c-116">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="0764c-117">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="0764c-117">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="0764c-118">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="0764c-118">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="0764c-119">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="0764c-119">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="0764c-120">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="0764c-120">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="0764c-121">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="0764c-121">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="0764c-122">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="0764c-122">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0764c-123">要件</span><span class="sxs-lookup"><span data-stu-id="0764c-123">Requirements</span></span>  

 <span data-ttu-id="0764c-124">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0764c-124">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0764c-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0764c-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0764c-126">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0764c-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0764c-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0764c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0764c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0764c-128">See also</span></span>

- [<span data-ttu-id="0764c-129">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0764c-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="0764c-130">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0764c-130">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
