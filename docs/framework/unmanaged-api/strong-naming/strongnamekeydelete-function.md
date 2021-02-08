---
description: '詳細情報: StrongNameKeyDelete 関数'
title: StrongNameKeyDelete 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: 9314d961f79e673925125c2362308f9ab4533e75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781208"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="9faad-103">StrongNameKeyDelete 関数</span><span class="sxs-lookup"><span data-stu-id="9faad-103">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="9faad-104">指定したキー コンテナーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9faad-104">Deletes the specified key container.</span></span>

<span data-ttu-id="9faad-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="9faad-105">This function has been deprecated.</span></span> <span data-ttu-id="9faad-106">代わりに [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9faad-106">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="9faad-107">構文</span><span class="sxs-lookup"><span data-stu-id="9faad-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="9faad-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9faad-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="9faad-109">から削除するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="9faad-109">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="9faad-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9faad-110">Return Value</span></span>

<span data-ttu-id="9faad-111">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="9faad-111">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9faad-112">解説</span><span class="sxs-lookup"><span data-stu-id="9faad-112">Remarks</span></span>

<span data-ttu-id="9faad-113">公開/秘密キーのペアをコンテナーにインポートするには、 [StrongNameKeyInstall](strongnamekeyinstall-function.md) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="9faad-113">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="9faad-114">関数が `StrongNameKeyDelete` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9faad-114">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="9faad-115">要件</span><span class="sxs-lookup"><span data-stu-id="9faad-115">Requirements</span></span>

<span data-ttu-id="9faad-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9faad-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9faad-117">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="9faad-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="9faad-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9faad-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="9faad-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9faad-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9faad-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9faad-120">See also</span></span>

- [<span data-ttu-id="9faad-121">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="9faad-121">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="9faad-122">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="9faad-122">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="9faad-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9faad-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
