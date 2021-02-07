---
description: '詳細情報: StrongNameKeyInstall 関数'
title: StrongNameKeyInstall 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 0a5d3971ac0927dda7066405adc01a5c80b7faca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670542"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="c794b-103">StrongNameKeyInstall 関数</span><span class="sxs-lookup"><span data-stu-id="c794b-103">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="c794b-104">公開/秘密キーの組がコンテナーにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="c794b-104">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="c794b-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="c794b-105">This function has been deprecated.</span></span> <span data-ttu-id="c794b-106">代わりに [ICLRStrongName:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c794b-106">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="c794b-107">構文</span><span class="sxs-lookup"><span data-stu-id="c794b-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="c794b-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c794b-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="c794b-109">からキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="c794b-109">[in] The name of the key container.</span></span> <span data-ttu-id="c794b-110">`wszKeyContainer` は空でない文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c794b-110">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="c794b-111">からバイナリキーペア。</span><span class="sxs-lookup"><span data-stu-id="c794b-111">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="c794b-112">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="c794b-112">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c794b-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="c794b-113">Return Value</span></span>

<span data-ttu-id="c794b-114">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="c794b-114">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c794b-115">解説</span><span class="sxs-lookup"><span data-stu-id="c794b-115">Remarks</span></span>

<span data-ttu-id="c794b-116">キーコンテナーを削除するには、 [StrongNameKeyDelete](strongnamekeydelete-function.md) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="c794b-116">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="c794b-117">関数が `StrongNameKeyInstall` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="c794b-117">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="c794b-118">要件</span><span class="sxs-lookup"><span data-stu-id="c794b-118">Requirements</span></span>

<span data-ttu-id="c794b-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c794b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c794b-120">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="c794b-120">**Header:** StrongName.h</span></span>

<span data-ttu-id="c794b-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c794b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="c794b-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c794b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c794b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c794b-123">See also</span></span>

- [<span data-ttu-id="c794b-124">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="c794b-124">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="c794b-125">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="c794b-125">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="c794b-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c794b-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
