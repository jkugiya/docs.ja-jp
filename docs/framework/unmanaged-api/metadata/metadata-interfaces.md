---
description: '詳細情報: メタデータインターフェイス'
title: メタデータ インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4851fbc93bfa29f1b4b5015c82f05c1b200b9092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799136"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="414c3-103">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-103">Metadata Interfaces</span></span>

<span data-ttu-id="414c3-104">このセクションでは、.NET Framework の型、メソッド、フィールドなどによって公開されるメタデータにアクセスできるようにするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="414c3-104">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="414c3-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="414c3-105">In This Section</span></span>  

 [<span data-ttu-id="414c3-106">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-106">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="414c3-107">動的なコード コンパイルのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-107">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="414c3-108">IHostFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-108">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="414c3-109">ランタイム ホストがメタデータ トークンに処理済みのマークを付けるためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-109">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="414c3-110">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-110">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="414c3-111">インポートされたメタデータ署名と生成されたメタデータ署名との間の割り当て機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-111">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="414c3-112">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-112">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="414c3-113">共通言語ランタイム (CLR) がリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-113">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="414c3-114">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="414c3-115">アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-115">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="414c3-116">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="414c3-117">タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-117">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="414c3-118">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="414c3-119">`IMetaDataDispenser` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="414c3-119">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="414c3-120">代わりに `IMetaDataDispenserEx` を使用してください</span><span class="sxs-lookup"><span data-stu-id="414c3-120">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="414c3-121">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="414c3-122">メタデータを作成または変更するためのメモリ領域を割り当てるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-122">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="414c3-123">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="414c3-124">現在定義されているスコープ内のアセンブリについてのメタデータを作成、変更、格納するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-124">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="414c3-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="414c3-126"><xref:System.Type?displayProperty=nameWithType> 型のパラメーターを持つメソッドおよびコンストラクターのメタデータ署名を定義および変更するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-126">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="414c3-127">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-127">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="414c3-128">アセンブリのメタデータ署名の解決時のエラーを報告するためのコールバック機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-128">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="414c3-129">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-129">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="414c3-130">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-130">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="414c3-131">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="414c3-132">他のアセンブリの型をインポートおよび操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-132">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="414c3-133">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="414c3-134">`IMetaDataImport` を拡張して、ジェネリック型を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="414c3-134">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="414c3-135">IMetaDataInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-135">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="414c3-136">ディスク上のファイルからメモリへのメタデータのマッピングに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-136">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="414c3-137">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-137">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="414c3-138">テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-138">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="414c3-139">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-139">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="414c3-140">`IMetaDataTables` を拡張して、メタデータ ストリームを使用するためのメソッドを含めます。</span><span class="sxs-lookup"><span data-stu-id="414c3-140">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="414c3-141">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="414c3-141">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="414c3-142">メタデータ署名の検証で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="414c3-142">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="414c3-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="414c3-143">Related Sections</span></span>  

 [<span data-ttu-id="414c3-144">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="414c3-144">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="414c3-145">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="414c3-145">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="414c3-146">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="414c3-146">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="414c3-147">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="414c3-147">Metadata Unions</span></span>](metadata-unions.md)
