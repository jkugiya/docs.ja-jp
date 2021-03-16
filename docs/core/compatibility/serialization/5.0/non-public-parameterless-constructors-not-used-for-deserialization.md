---
title: 破壊的変更:非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない
description: .NET 5 での破壊的変更について学習します。JsonSerializer で非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されなくなりました。
ms.date: 10/18/2020
ms.openlocfilehash: 9781061fa89eb3bffb53a4f08bacbd88f3bc9265
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256271"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="9292b-103">非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない</span><span class="sxs-lookup"><span data-stu-id="9292b-103">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="9292b-104">サポートされているすべてのターゲット フレームワーク モニカー (TFM) との間で一貫性を維持するために、既定では、非パブリックのパラメーターなしのコンストラクターは <xref:System.Text.Json.JsonSerializer> での逆シリアル化に使用されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9292b-104">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

## <a name="change-description"></a><span data-ttu-id="9292b-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="9292b-105">Change description</span></span>

<span data-ttu-id="9292b-106">.NET Standard 2.0 以降をサポートするスタンドアロン [System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json/) (つまり、バージョン 4.6.0-4.7.2) の動作は、.NET Core 3.0 および 3.1 の組み込みの動作と一致しません。</span><span class="sxs-lookup"><span data-stu-id="9292b-106">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="9292b-107">.NET Core 3.x では、internal と private コンストラクターを逆シリアル化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9292b-107">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="9292b-108">スタンドアロン パッケージで、非パブリック コンストラクターは使用できません。また、非パブリックのパラメーターなしのコンストラクターが定義されていない場合は、<xref:System.MissingMethodException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9292b-108">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="9292b-109">.NET 5 以降および System.Text.Json NuGet パッケージ 5.0.0 では、NuGet パッケージと組み込み API 間で動作に一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="9292b-109">Starting with .NET 5 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="9292b-110">非パブリック コンストラクター (パラメーターなしのコンストラクターを含む) は、既定ではシリアライザーによって無視されます。</span><span class="sxs-lookup"><span data-stu-id="9292b-110">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="9292b-111">逆シリアル化のために、次のいずれかのコンストラクターがシリアライザーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="9292b-111">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="9292b-112"><xref:System.Text.Json.Serialization.JsonConstructorAttribute> の注釈が付けられたパブリック コンストラクター。</span><span class="sxs-lookup"><span data-stu-id="9292b-112">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="9292b-113">パブリックのパラメーターなしのコンストラクター。</span><span class="sxs-lookup"><span data-stu-id="9292b-113">Public parameterless constructor.</span></span>
- <span data-ttu-id="9292b-114">パブリックのパラメーター化されたコンストラクター (唯一のパブリック コンストラクターが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="9292b-114">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="9292b-115">これらのコンストラクターをいずれも使用できない場合は、型を逆シリアル化しようとすると <xref:System.NotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9292b-115">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9292b-116">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9292b-116">Version introduced</span></span>

<span data-ttu-id="9292b-117">5.0</span><span class="sxs-lookup"><span data-stu-id="9292b-117">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9292b-118">変更理由</span><span class="sxs-lookup"><span data-stu-id="9292b-118">Reason for change</span></span>

- <span data-ttu-id="9292b-119"><xref:System.Text.Json?displayProperty=fullName> のビルド対象のすべてのターゲット フレームワーク モニカー (TFM) の間で一貫した動作を適用するため (.NET Core 3.0 以降のバージョンと .NET Standard 2.0)</span><span class="sxs-lookup"><span data-stu-id="9292b-119">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="9292b-120">コンストラクター、プロパティ、またはフィールドのいずれであるかにかかわらず、<xref:System.Text.Json.JsonSerializer> から型の非パブリック アクセス領域を呼び出すことができないため。</span><span class="sxs-lookup"><span data-stu-id="9292b-120">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9292b-121">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="9292b-121">Recommended action</span></span>

- <span data-ttu-id="9292b-122">型を所有していて、それが実行可能な場合は、パラメーターなしのコンストラクターをパブリックにします。</span><span class="sxs-lookup"><span data-stu-id="9292b-122">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="9292b-123">それ以外の場合は、型に対して <xref:System.Text.Json.Serialization.JsonConverter%601> を実装し、逆シリアル化動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="9292b-123">Otherwise, implement a <xref:System.Text.Json.Serialization.JsonConverter%601> for the type and control the deserialization behavior.</span></span> <span data-ttu-id="9292b-124">そのシナリオの C# アクセシビリティ規則で許可されている場合は、<xref:System.Text.Json.Serialization.JsonConverter%601> の実装から非パブリック コンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9292b-124">You can call a non-public constructor from a <xref:System.Text.Json.Serialization.JsonConverter%601> implementation if C# accessibility rules for that scenario allow it.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9292b-125">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9292b-125">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
