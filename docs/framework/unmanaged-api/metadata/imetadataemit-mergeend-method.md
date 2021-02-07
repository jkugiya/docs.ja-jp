---
description: '詳細について: IMetaDataEmit:: MergeEnd メソッド'
title: IMetaDataEmit::MergeEnd メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: aac48b9bafb60cee4e3d73232d9f9c00cca7f796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745880"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="dad53-103">IMetaDataEmit::MergeEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="dad53-103">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="dad53-104">[IMetaDataEmit:: Merge](imetadataemit-merge-method.md)の1つ以上の前の呼び出しで指定されたすべてのメタデータスコープを現在のスコープにマージします。</span><span class="sxs-lookup"><span data-stu-id="dad53-104">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="dad53-105">構文</span><span class="sxs-lookup"><span data-stu-id="dad53-105">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="dad53-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad53-106">Parameters</span></span>

<span data-ttu-id="dad53-107">このメソッドはパラメーターを受け取りません。</span><span class="sxs-lookup"><span data-stu-id="dad53-107">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="dad53-108">解説</span><span class="sxs-lookup"><span data-stu-id="dad53-108">Remarks</span></span>

<span data-ttu-id="dad53-109">このルーチンは、の前の呼び出しで指定されたすべてのインポートスコープのメタデータの実際のマージを `IMetaDataEmit::Merge` 現在の出力スコープにトリガーします。</span><span class="sxs-lookup"><span data-stu-id="dad53-109">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="dad53-110">マージには、次の特殊な条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="dad53-110">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="dad53-111">モジュールバージョン識別子 (MVID) はインポートされません。これは、インポートスコープ内のメタデータに固有であるためです。</span><span class="sxs-lookup"><span data-stu-id="dad53-111">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="dad53-112">既存のモジュール全体のプロパティは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="dad53-112">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="dad53-113">モジュールのプロパティが現在のスコープに対して既に設定されている場合は、モジュールのプロパティはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="dad53-113">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="dad53-114">ただし、モジュールのプロパティが現在のスコープで設定されていない場合は、最初に検出されたときに1回だけインポートされます。</span><span class="sxs-lookup"><span data-stu-id="dad53-114">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="dad53-115">これらのモジュールのプロパティが再度検出された場合、それらは重複しています。</span><span class="sxs-lookup"><span data-stu-id="dad53-115">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="dad53-116">すべてのモジュールプロパティ (MVID を除く) の値が比較され、重複が見つからない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad53-116">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="dad53-117">型定義 () の場合 `TypeDef` 、重複は現在のスコープにマージされません。</span><span class="sxs-lookup"><span data-stu-id="dad53-117">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="dad53-118">`TypeDef`オブジェクトは、完全修飾された *オブジェクト名*  +  *GUID* の  +  *バージョン番号* ごとに重複しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="dad53-118">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="dad53-119">名前または GUID に一致するものがあり、他の2つの要素のいずれかが異なる場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad53-119">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="dad53-120">それ以外の場合、3つのすべての項目が一致すると、は、 `MergeEnd` エントリが実際に重複していることを確認するための大まかなチェックを行います。そうでない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad53-120">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="dad53-121">この大まかなチェックは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad53-121">This cursory check looks for:</span></span>

  - <span data-ttu-id="dad53-122">同じ順序で発生する同じメンバー宣言。</span><span class="sxs-lookup"><span data-stu-id="dad53-122">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="dad53-123">としてフラグが設定されているメンバー `mdPrivateScope` ( [CorMethodAttr](cormethodattr-enumeration.md) 列挙を参照) は、このチェックには含まれていません。これらは特別にマージされます。</span><span class="sxs-lookup"><span data-stu-id="dad53-123">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="dad53-124">同じクラスレイアウト。</span><span class="sxs-lookup"><span data-stu-id="dad53-124">The same class layout.</span></span>

  <span data-ttu-id="dad53-125">これは、 `TypeDef` オブジェクトが宣言されているすべてのメタデータスコープで常に完全かつ一貫して定義されている必要があることを意味します。そのメンバー実装 (クラスの場合) が複数のコンパイル単位にわたって分散されている場合、完全定義はすべてのスコープに存在し、各スコープに増分されません。</span><span class="sxs-lookup"><span data-stu-id="dad53-125">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="dad53-126">たとえば、パラメーター名がコントラクトに関連する場合は、すべてのスコープに同じ方法で出力する必要があります。これらが関連性のない場合は、メタデータに出力されません。</span><span class="sxs-lookup"><span data-stu-id="dad53-126">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="dad53-127">例外は、オブジェクトが `TypeDef` というフラグが付けられた増分メンバーを持つことができることです `mdPrivateScope` 。</span><span class="sxs-lookup"><span data-stu-id="dad53-127">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="dad53-128">これらが検出さ `MergeEnd` れると、重複を考慮せずに、それらを現在のスコープに増分的に追加します。</span><span class="sxs-lookup"><span data-stu-id="dad53-128">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="dad53-129">コンパイラはプライベートスコープを認識しているため、コンパイラは規則の適用を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad53-129">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="dad53-130">相対仮想アドレス (RVAs) はインポートまたはマージされません。コンパイラは、この情報を再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad53-130">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="dad53-131">カスタム属性は、関連付けられているアイテムがマージされた場合にのみマージされます。</span><span class="sxs-lookup"><span data-stu-id="dad53-131">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="dad53-132">たとえば、クラスに関連付けられているカスタム属性は、クラスが最初に検出されたときにマージされます。</span><span class="sxs-lookup"><span data-stu-id="dad53-132">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="dad53-133">カスタム属性がに関連付けられている場合、 `TypeDef` または `MemberDef` コンパイル単位 (メンバーコンパイルのタイムスタンプなど) に固有の場合は、マージされず、そのようなメタデータを削除または更新するためにコンパイラによって行われます。</span><span class="sxs-lookup"><span data-stu-id="dad53-133">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="dad53-134">要件</span><span class="sxs-lookup"><span data-stu-id="dad53-134">Requirements</span></span>

<span data-ttu-id="dad53-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dad53-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="dad53-136">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dad53-136">**Header:** Cor.h</span></span>

<span data-ttu-id="dad53-137">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad53-137">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="dad53-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad53-138">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dad53-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="dad53-139">See also</span></span>

- [<span data-ttu-id="dad53-140">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dad53-140">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="dad53-141">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dad53-141">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
