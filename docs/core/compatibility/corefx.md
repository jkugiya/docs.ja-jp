---
title: .NET ライブラリの破壊的変更
description: .NET Core バージョン 1.0-3.0 の Core .NET ライブラリにおける破壊的変更の一覧を示します。
ms.date: 07/27/2020
ms.openlocfilehash: 99c72b5ff36d0c0cb821d50b1ec04fdef56189da
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494364"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="2ae0c-103">.NET Core 1.0-3.0 の Core .NET ライブラリの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="2ae0c-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="2ae0c-104">Core .NET ライブラリでは、.NET Core で使用されるプリミティブとその他の一般的な型が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2ae0c-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="2ae0c-105">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ae0c-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="2ae0c-106">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="2ae0c-106">Breaking change</span></span> | <span data-ttu-id="2ae0c-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2ae0c-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="2ae0c-108">IEnumerable\<T> を受け取る拡張メソッドに GroupCollection を渡すにはあいまいさが必要</span><span class="sxs-lookup"><span data-stu-id="2ae0c-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="2ae0c-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-109">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-110">バージョンをレポートする API が、ファイル バージョンではなく製品をレポートするようになった</span><span class="sxs-lookup"><span data-stu-id="2ae0c-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="2ae0c-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-111">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-112">カスタム EncoderFallbackBuffer インスタンスが再帰的にフォールバックしない</span><span class="sxs-lookup"><span data-stu-id="2ae0c-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="2ae0c-113">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-113">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-114">浮動小数点の書式設定と解析の動作の変更</span><span class="sxs-lookup"><span data-stu-id="2ae0c-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="2ae0c-115">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-115">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-116">浮動小数点の解析操作が失敗したり OverflowException がスローされたりすることがなくなった</span><span class="sxs-lookup"><span data-stu-id="2ae0c-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="2ae0c-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-117">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-118">InvalidAsynchronousStateException を別のアセンブリに移動</span><span class="sxs-lookup"><span data-stu-id="2ae0c-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="2ae0c-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-119">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-120">Unicode のガイドラインに従って不適切な形式の UTF-8 バイト シーケンスを置き換える</span><span class="sxs-lookup"><span data-stu-id="2ae0c-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="2ae0c-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-121">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-122">TypeDescriptionProviderAttribute を別のアセンブリに移動</span><span class="sxs-lookup"><span data-stu-id="2ae0c-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="2ae0c-123">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-123">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-124">ZipArchiveEntry による、エントリ サイズに一貫性のないアーカイブ処理の中止</span><span class="sxs-lookup"><span data-stu-id="2ae0c-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="2ae0c-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-125">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-126">FieldInfo.SetValue で、静的な初期化専用フィールドに対する例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="2ae0c-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="2ae0c-127">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-127">.NET Core 3.0</span></span> |
| [<span data-ttu-id="2ae0c-128">パス API から、無効な文字に対する例外はスローされません</span><span class="sxs-lookup"><span data-stu-id="2ae0c-128">Path APIs don't throw an exception for invalid characters</span></span>](#path-apis-dont-throw-an-exception-for-invalid-characters) | <span data-ttu-id="2ae0c-129">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ae0c-129">.NET Core 2.1</span></span> |
| [<span data-ttu-id="2ae0c-130">組み込みの構造体型に追加されたプライベート フィールド</span><span class="sxs-lookup"><span data-stu-id="2ae0c-130">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="2ae0c-131">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ae0c-131">.NET Core 2.1</span></span> |
| [<span data-ttu-id="2ae0c-132">UseShellExecute の既定値の変更</span><span class="sxs-lookup"><span data-stu-id="2ae0c-132">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="2ae0c-133">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ae0c-133">.NET Core 2.1</span></span> |
| [<span data-ttu-id="2ae0c-134">macOS 上の OpenSSL バージョン</span><span class="sxs-lookup"><span data-stu-id="2ae0c-134">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="2ae0c-135">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ae0c-135">.NET Core 2.1</span></span> |
| [<span data-ttu-id="2ae0c-136">FileSystemInfo.Attributes によってスローされる UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="2ae0c-136">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="2ae0c-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-137">.NET Core 1.0</span></span> |
| [<span data-ttu-id="2ae0c-138">プロセス破損状態例外の処理がサポートされない</span><span class="sxs-lookup"><span data-stu-id="2ae0c-138">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="2ae0c-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-139">.NET Core 1.0</span></span> |
| [<span data-ttu-id="2ae0c-140">UriBuilder のプロパティでは今後、先頭に文字が付加されない</span><span class="sxs-lookup"><span data-stu-id="2ae0c-140">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="2ae0c-141">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-141">.NET Core 1.0</span></span> |
| [<span data-ttu-id="2ae0c-142">開始されなかったプロセスについて Process.StartInfo が InvalidOperationException をスローする</span><span class="sxs-lookup"><span data-stu-id="2ae0c-142">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="2ae0c-143">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-143">.NET Core 1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="2ae0c-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-144">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="2ae0c-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ae0c-145">.NET Core 2.1</span></span>

[!INCLUDE [path-apis-dont-throw-exception-for-invalid-paths](../../../includes/core-changes/corefx/2.1/path-apis-dont-throw-exception-for-invalid-paths.md)]

***

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="2ae0c-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2ae0c-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
