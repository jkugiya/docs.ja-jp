---
description: '詳細について: ICorDebugProcess6:: GetExportStepInfo メソッド'
title: ICorDebugProcess6::GetExportStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: e14b5e66d90fb2ece91991b3634fc2ad86fac895
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722010"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="45ab5-103">ICorDebugProcess6::GetExportStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="45ab5-103">ICorDebugProcess6::GetExportStepInfo Method</span></span>

<span data-ttu-id="45ab5-104">マネージド コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="45ab5-104">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ab5-105">構文</span><span class="sxs-lookup"><span data-stu-id="45ab5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45ab5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45ab5-106">Parameters</span></span>  

 <span data-ttu-id="45ab5-107">pszExportName</span><span class="sxs-lookup"><span data-stu-id="45ab5-107">pszExportName</span></span>  
 <span data-ttu-id="45ab5-108">[入力] PE エクスポート テーブルに書き込まれるランタイム エクスポート関数の名前。</span><span class="sxs-lookup"><span data-stu-id="45ab5-108">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="45ab5-109">invokeKind</span><span class="sxs-lookup"><span data-stu-id="45ab5-109">invokeKind</span></span>  
 <span data-ttu-id="45ab5-110">入出力エクスポートされた関数がマネージコードを呼び出す方法を記述する [Cordebugcodeinvokekind](cordebugcodeinvokekind-enumeration.md) 列挙体のメンバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="45ab5-110">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="45ab5-111">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="45ab5-111">invokePurpose</span></span>  
 <span data-ttu-id="45ab5-112">入出力エクスポートされた関数がマネージコードを呼び出す理由を示す [Cordebugcodeinvokepurpose](cordebugcodeinvokepurpose-enumeration.md) の列挙体のメンバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="45ab5-112">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45ab5-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="45ab5-113">Return Value</span></span>  

 <span data-ttu-id="45ab5-114">メソッドは、次の表に記載されている値を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="45ab5-114">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="45ab5-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="45ab5-115">Return value</span></span>|<span data-ttu-id="45ab5-116">説明</span><span class="sxs-lookup"><span data-stu-id="45ab5-116">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="45ab5-117">メソッド呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="45ab5-117">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="45ab5-118">`pInvokeKind` または `pInvokePurpose` が **null** です。</span><span class="sxs-lookup"><span data-stu-id="45ab5-118">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="45ab5-119">その他の失敗した `HRESULT` 値。</span><span class="sxs-lookup"><span data-stu-id="45ab5-119">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="45ab5-120">必要に応じて。</span><span class="sxs-lookup"><span data-stu-id="45ab5-120">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45ab5-121">解説</span><span class="sxs-lookup"><span data-stu-id="45ab5-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45ab5-122">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="45ab5-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ab5-123">要件</span><span class="sxs-lookup"><span data-stu-id="45ab5-123">Requirements</span></span>  

 <span data-ttu-id="45ab5-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45ab5-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ab5-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45ab5-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45ab5-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45ab5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45ab5-127">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ab5-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ab5-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="45ab5-128">See also</span></span>

- [<span data-ttu-id="45ab5-129">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45ab5-129">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="45ab5-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="45ab5-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
