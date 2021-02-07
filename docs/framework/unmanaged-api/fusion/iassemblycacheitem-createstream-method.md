---
description: '詳細については、次を参照してください: IAssemblyCacheItem:: CreateStream メソッド'
title: IAssemblyCacheItem::CreateStream メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 89592d8fe1a7f43a7da20dd10883881c3339f088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760873"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="b8d95-103">IAssemblyCacheItem::CreateStream メソッド</span><span class="sxs-lookup"><span data-stu-id="b8d95-103">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="b8d95-104">指定された名前と形式を使用してストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8d95-104">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8d95-105">構文</span><span class="sxs-lookup"><span data-stu-id="b8d95-105">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="b8d95-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8d95-106">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="b8d95-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="b8d95-107">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="b8d95-108">から作成されるストリームの名前。</span><span class="sxs-lookup"><span data-stu-id="b8d95-108">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="b8d95-109">からストリーム配信されるファイルの形式。</span><span class="sxs-lookup"><span data-stu-id="b8d95-109">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="b8d95-110">からFusion に定義されている形式固有のフラグ。</span><span class="sxs-lookup"><span data-stu-id="b8d95-110">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="b8d95-111">入出力返された [IStream](/windows/desktop/api/objidl/nn-objidl-istream) インスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8d95-111">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="b8d95-112">[in、optional]によって参照されるストリームの最大サイズ `ppIStream` 。</span><span class="sxs-lookup"><span data-stu-id="b8d95-112">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8d95-113">要件</span><span class="sxs-lookup"><span data-stu-id="b8d95-113">Requirements</span></span>

<span data-ttu-id="b8d95-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8d95-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b8d95-115">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b8d95-115">**Header:** Fusion.h</span></span>

<span data-ttu-id="b8d95-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d95-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d95-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8d95-117">See also</span></span>

- [<span data-ttu-id="b8d95-118">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d95-118">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
