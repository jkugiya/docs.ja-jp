---
description: '詳細については、次を参照してください: MemoryStream メソッド'
title: MemoryStream (System.IO) メソッド ()
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 4232852c0835a43454f36271a43062e1240297a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802542"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="75eac-103">MemoryStream.InternalGetOriginAndLength メソッド</span><span class="sxs-lookup"><span data-stu-id="75eac-103">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="75eac-104">メモリストリームの原点と長さの内部値を取得します。</span><span class="sxs-lookup"><span data-stu-id="75eac-104">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="75eac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="75eac-105">Parameters</span></span>

- <span data-ttu-id="75eac-106">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="75eac-106">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="75eac-107">このメソッドから制御が戻るときに、新しいオブジェクトを作成するときに指定されたバイト配列のオフセット <xref:System.IO.MemoryStream> 。</span><span class="sxs-lookup"><span data-stu-id="75eac-107">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="75eac-108">バイト配列がによって作成された場合は0を格納 <xref:System.IO.MemoryStream> します。</span><span class="sxs-lookup"><span data-stu-id="75eac-108">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="75eac-109">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="75eac-109">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="75eac-110">このメソッドから制御が戻るときに、メモリストリーム内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="75eac-110">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="75eac-111">解説</span><span class="sxs-lookup"><span data-stu-id="75eac-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="75eac-112">`MemoryStream.InternalGetOriginAndLength`メソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="75eac-112">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="75eac-113">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="75eac-113">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="75eac-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="75eac-114">Requirements</span></span>

<span data-ttu-id="75eac-115">**名前空間:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="75eac-115">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="75eac-116">**アセンブリ:** mscorlib.dll (mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="75eac-116">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="75eac-117">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="75eac-117">**.NET Framework versions:** Available since 2.0.</span></span>
