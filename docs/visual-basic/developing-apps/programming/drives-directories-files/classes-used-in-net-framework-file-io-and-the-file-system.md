---
description: '詳細情報: .NET Framework のファイル I/O とファイル システムで使用するクラス (Visual Basic)'
title: .NET Framework のファイル I/O とファイル システムで使用するクラス
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: a8cbe476044df92fcdbdd0421b91f3c7c098e063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666330"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="626d9-103">.NET Framework のファイル I/O とファイル システムで使用するクラス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="626d9-103">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>

<span data-ttu-id="626d9-104">以下の表は、.NET Framework のファイル I/O で一般的に使用するクラスの一覧です。ファイル I/O クラス、ストリームの作成に使用するクラス、ストリームの読み取りと書き込みに使用するクラスに分類されています。</span><span class="sxs-lookup"><span data-stu-id="626d9-104">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
<span data-ttu-id="626d9-105">詳細な一覧を参照するには、[クラス ライブラリの概要](../../../../standard/class-library-overview.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="626d9-105">For a more comprehensive listing, see [Class Library Overview](../../../../standard/class-library-overview.md).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="626d9-106">ファイル、ドライブ、およびディレクトリ用の基本 I/O クラス</span><span class="sxs-lookup"><span data-stu-id="626d9-106">Basic I/O Classes for Files, Drives, and Directories</span></span>  

 <span data-ttu-id="626d9-107">次の表は、ファイル I/O に使用する主要なクラスの一覧と各クラスの説明です。</span><span class="sxs-lookup"><span data-stu-id="626d9-107">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="626d9-108">インスタンス</span><span class="sxs-lookup"><span data-stu-id="626d9-108">Class</span></span>|<span data-ttu-id="626d9-109">説明</span><span class="sxs-lookup"><span data-stu-id="626d9-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|<span data-ttu-id="626d9-110">ディレクトリやサブディレクトリを作成、移動、および反復処理するための静的メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-110">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|<span data-ttu-id="626d9-111">ディレクトリやサブディレクトリを作成、移動、および反復処理するためのインスタンス メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-111">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|<span data-ttu-id="626d9-112">ドライブを作成、移動、および反復処理するためのインスタンス メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-112">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=nameWithType>|<span data-ttu-id="626d9-113">ファイルを作成、コピー、削除、移動、およびオープンするための静的メソッドを提供し、`FileStream`の作成を支援します。</span><span class="sxs-lookup"><span data-stu-id="626d9-113">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|<span data-ttu-id="626d9-114">ファイルの読み取り、書き込み、または読み取り/書き込みアクセスのための定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="626d9-114">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|<span data-ttu-id="626d9-115">`Archive`、`Hidden`、`ReadOnly` など、ファイルとディレクトリの属性を提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-115">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|<span data-ttu-id="626d9-116">ファイルを作成、コピー、削除、移動、およびオープンするための静的メソッドを提供し、`FileStream`の作成を支援します。</span><span class="sxs-lookup"><span data-stu-id="626d9-116">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|<span data-ttu-id="626d9-117">ファイルを開く方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="626d9-117">Controls how a file is opened.</span></span> <span data-ttu-id="626d9-118">このパラメーターは、`FileStream` と `IsolatedStorageFileStream` の多数のコンストラクター、および <xref:System.IO.File> と <xref:System.IO.FileInfo> の `Open` メソッドで使用します。</span><span class="sxs-lookup"><span data-stu-id="626d9-118">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|<span data-ttu-id="626d9-119">他のファイル ストリームから同一のファイルに対して可能なアクセスの種類を制御する定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="626d9-119">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=nameWithType>|<span data-ttu-id="626d9-120">ディレクトリ文字列を処理するためのメソッドとプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-120">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|<span data-ttu-id="626d9-121"><xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> の各アクセス許可を定義してファイルおよびフォルダーへのアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="626d9-121">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="626d9-122">ストリームの作成に使用するクラス</span><span class="sxs-lookup"><span data-stu-id="626d9-122">Classes Used to Create Streams</span></span>  

 <span data-ttu-id="626d9-123">次の表は、ストリームの作成に使用する主要なクラスの一覧と各クラスの説明です。</span><span class="sxs-lookup"><span data-stu-id="626d9-123">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="626d9-124">インスタンス</span><span class="sxs-lookup"><span data-stu-id="626d9-124">Class</span></span>|<span data-ttu-id="626d9-125">説明</span><span class="sxs-lookup"><span data-stu-id="626d9-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|<span data-ttu-id="626d9-126">他のストリームの読み取りおよび書き込み操作に対してバッファリング レイヤーを追加します。</span><span class="sxs-lookup"><span data-stu-id="626d9-126">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<span data-ttu-id="626d9-127"><xref:System.IO.FileStream.Seek%2A> メソッドにより、ファイルへのランダム アクセスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="626d9-127">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="626d9-128"><xref:System.IO.FileStream> は、既定では同期的にファイルを開きますが、非同期操作もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="626d9-128"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|<span data-ttu-id="626d9-129">バッキング ストアがファイルではなくメモリであるストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="626d9-129">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|<span data-ttu-id="626d9-130">ネットワーク アクセスの基になるデータ ストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="626d9-130">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|<span data-ttu-id="626d9-131">データ ストリームを暗号変換にリンクするストリームを定義します。</span><span class="sxs-lookup"><span data-stu-id="626d9-131">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="626d9-132">ストリームの読み取りと書き込みに使用するクラス</span><span class="sxs-lookup"><span data-stu-id="626d9-132">Classes Used to Read from and Write to Streams</span></span>  

 <span data-ttu-id="626d9-133">次の表は、ストリームによるファイルの読み取りと書き込みに使用する固有のクラスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="626d9-133">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="626d9-134">**クラス**</span><span class="sxs-lookup"><span data-stu-id="626d9-134">**Class**</span></span>|<span data-ttu-id="626d9-135">**説明**</span><span class="sxs-lookup"><span data-stu-id="626d9-135">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|<span data-ttu-id="626d9-136">エンコードされた文字列とプリミティブ データ型を <xref:System.IO.FileStream> から読み取ります。</span><span class="sxs-lookup"><span data-stu-id="626d9-136">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|<span data-ttu-id="626d9-137">エンコードされた文字列とプリミティブ データ型を <xref:System.IO.FileStream> に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="626d9-137">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|<span data-ttu-id="626d9-138"><xref:System.IO.StreamReader.CurrentEncoding%2A> を使用して文字とバイト間の変換を行い、<xref:System.IO.FileStream> から文字を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="626d9-138">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="626d9-139"><xref:System.IO.StreamReader> には、指定したストリームに適した <xref:System.IO.StreamReader.CurrentEncoding%2A> を <xref:System.IO.StreamReader.CurrentEncoding%2A> 固有のプリアンブル (バイト オーダー マークなど) に基づいて確認するコンストラクターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="626d9-139"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|<span data-ttu-id="626d9-140"><xref:System.IO.StreamWriter.Encoding%2A> を使用して文字をバイトに変換し、`FileStream` に文字を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="626d9-140">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|<span data-ttu-id="626d9-141">`String` から文字を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="626d9-141">Reads characters from a `String`.</span></span> <span data-ttu-id="626d9-142">出力は、任意のエンコーディングのストリームまたは `String` です。</span><span class="sxs-lookup"><span data-stu-id="626d9-142">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|<span data-ttu-id="626d9-143">`String` に文字を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="626d9-143">Writes characters to a `String`.</span></span> <span data-ttu-id="626d9-144">出力は、任意のエンコーディングのストリームまたは `String` です。</span><span class="sxs-lookup"><span data-stu-id="626d9-144">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="626d9-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="626d9-145">See also</span></span>

- [<span data-ttu-id="626d9-146">ストリームの構成</span><span class="sxs-lookup"><span data-stu-id="626d9-146">Composing Streams</span></span>](../../../../standard/io/composing-streams.md)
- [<span data-ttu-id="626d9-147">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="626d9-147">File and Stream I/O</span></span>](../../../../standard/io/index.md)
- [<span data-ttu-id="626d9-148">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="626d9-148">Asynchronous File I/O</span></span>](../../../../standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="626d9-149">.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="626d9-149">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](basics-of-net-framework-file-io-and-the-file-system.md)
