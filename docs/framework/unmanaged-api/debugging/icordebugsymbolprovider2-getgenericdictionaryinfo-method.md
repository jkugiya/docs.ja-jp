---
description: '詳細について: ICorDebugSymbolProvider2:: GetGenericDictionaryInfo メソッド'
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: 3488cab9ee21ea027e16089f066369ab8c6c69d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659544"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="cefae-103">ICorDebugSymbolProvider2::GetGenericDictionaryInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="cefae-103">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="cefae-104">汎用のディクショナリ マップを取得します。</span><span class="sxs-lookup"><span data-stu-id="cefae-104">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="cefae-105">構文</span><span class="sxs-lookup"><span data-stu-id="cefae-105">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="cefae-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cefae-106">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="cefae-107">入出力ジェネリックディクショナリマップを格納している、 [のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cefae-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="cefae-108">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cefae-108">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="cefae-109">解説</span><span class="sxs-lookup"><span data-stu-id="cefae-109">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="cefae-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cefae-110">This method is available with .NET Native only.</span></span>

<span data-ttu-id="cefae-111">このマップは最上位レベルの 2 つのセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="cefae-111">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="cefae-112">このマップに含まれるすべてのディクショナリの相対仮想アドレス (RVA) を格納している [ディレクトリ](#Directory) 。</span><span class="sxs-lookup"><span data-stu-id="cefae-112">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="cefae-113">オブジェクトのインスタンス化情報を格納するバイト固定 [ヒープ](#Heap) 。</span><span class="sxs-lookup"><span data-stu-id="cefae-113">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="cefae-114">最後のディレクトリ エントリの直後から開始します。</span><span class="sxs-lookup"><span data-stu-id="cefae-114">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="cefae-115">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="cefae-115">The Directory</span></span>

<span data-ttu-id="cefae-116">ディレクトリ内の各エントリは、ヒープ内のオフセットを参照します。つまり、これは、ヒープの開始位置を基準としたオフセットです。</span><span class="sxs-lookup"><span data-stu-id="cefae-116">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="cefae-117">個々のエントリの値が一意とは限りません。このため、複数のディクショナリ エントリがヒープ内の同一オフセットを指すことがあります。</span><span class="sxs-lookup"><span data-stu-id="cefae-117">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="cefae-118">汎用のディクショナリ マップのディレクトリ部分の構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cefae-118">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="cefae-119">最初の 4 バイトには、ディクショナリのエントリ数 (ディクショナリ内の相対仮想アドレスの数) が格納されています。</span><span class="sxs-lookup"><span data-stu-id="cefae-119">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="cefae-120">この値は *N* として参照されます。上位ビットが設定されている場合、エントリは相対仮想アドレスで昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="cefae-120">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="cefae-121">*N* ディレクトリエントリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="cefae-121">The *N* directory entries follow.</span></span> <span data-ttu-id="cefae-122">各エントリは 8 バイトであり、次の 2 つの 4 バイト セグメントからなります。</span><span class="sxs-lookup"><span data-stu-id="cefae-122">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="cefae-123">バイト 0 ～ 3: RVA (ディクショナリの相対仮想アドレス)。</span><span class="sxs-lookup"><span data-stu-id="cefae-123">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="cefae-124">バイト 4 ～ 7: オフセット (ヒープの開始位置を基準としたオフセット)。</span><span class="sxs-lookup"><span data-stu-id="cefae-124">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="cefae-125">ヒープ</span><span class="sxs-lookup"><span data-stu-id="cefae-125">The Heap</span></span>

<span data-ttu-id="cefae-126">ヒープのサイズは、ストリーム リーダーにより、ディレクトリ サイズ + 4 の値からストリームの長さを差し引くことで算出されます。</span><span class="sxs-lookup"><span data-stu-id="cefae-126">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="cefae-127">つまり、以下の要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cefae-127">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="cefae-128">ディレクトリのサイズが `N * 8` であるとします。</span><span class="sxs-lookup"><span data-stu-id="cefae-128">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="cefae-129">ヒープの各インスタンス化情報項目の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cefae-129">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="cefae-130">このインスタンス化情報項目のバイト単位の長さ。圧縮 ECMA メタデータ形式です。</span><span class="sxs-lookup"><span data-stu-id="cefae-130">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="cefae-131">値では、この長さ情報が除外されます。</span><span class="sxs-lookup"><span data-stu-id="cefae-131">The value excludes this length information.</span></span>

- <span data-ttu-id="cefae-132">圧縮された ECMA メタデータ形式のジェネリックインスタンス化型 ( *T*) の数。</span><span class="sxs-lookup"><span data-stu-id="cefae-132">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="cefae-133">*T* 型はそれぞれ ECMA 型シグネチャ形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="cefae-133">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="cefae-134">各ヒープ要素の長さを含めることで、ヒープに影響を与えずに、ディレクトリ セクションの単純な並べ替えを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cefae-134">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="cefae-135">要件</span><span class="sxs-lookup"><span data-stu-id="cefae-135">Requirements</span></span>

<span data-ttu-id="cefae-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cefae-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cefae-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cefae-137">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="cefae-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cefae-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cefae-139">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cefae-139">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cefae-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="cefae-140">See also</span></span>

- [<span data-ttu-id="cefae-141">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cefae-141">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="cefae-142">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cefae-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
