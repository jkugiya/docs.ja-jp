---
title: 破壊的変更:Cryptography.Oid は機能的に初期化専用
description: .NET 5 の破壊的変更について学習します。この変更後、Cryptography.Oid クラスのプロパティ setter は、値を変更しようとしたときに例外をスローするようになりました。
ms.date: 08/16/2020
ms.openlocfilehash: aa1e72adcda61f2292574729e36cdc578bf907d2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256869"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="318ad-103">System.Security.Cryptography.Oid は機能的に初期化専用</span><span class="sxs-lookup"><span data-stu-id="318ad-103">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="318ad-104">ASN.1 オブジェクト識別子の値とその "わかりやすい" 名前を表すために使用される <xref:System.Security.Cryptography.Oid?displayProperty=fullName> クラスは、以前は完全に変更可能でした。</span><span class="sxs-lookup"><span data-stu-id="318ad-104">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="318ad-105">この変更可能性は意外にも見落とされがちでした。</span><span class="sxs-lookup"><span data-stu-id="318ad-105">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="318ad-106">割り当てられた後に値を変更しようとすると、プロパティの setter で <xref:System.PlatformNotSupportedException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="318ad-106">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

## <a name="change-description"></a><span data-ttu-id="318ad-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="318ad-107">Change description</span></span>

<span data-ttu-id="318ad-108">以前のバージョンでは、<xref:System.Security.Cryptography.Oid> のプロパティの setter を使用して、<xref:System.Security.Cryptography.Oid.FriendlyName> および <xref:System.Security.Cryptography.Oid.Value> プロパティの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="318ad-108">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="318ad-109">.NET 5 以降のバージョンでは、プロパティの setter は値の初期化にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="318ad-109">In .NET 5 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="318ad-110">プロパティにコンストラクターから、あるいはプロパティの setter の前の呼び出しからの値が設定されると、プロパティの setter で常に <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="318ad-110">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="318ad-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="318ad-111">Reason for change</span></span>

<span data-ttu-id="318ad-112">この変更により、パブリック API で戻り値の一部として <xref:System.Security.Cryptography.Oid> オブジェクトを再利用し、オブジェクト割り当てプロファイルを減らせるようになります。</span><span class="sxs-lookup"><span data-stu-id="318ad-112">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="318ad-113"><xref:System.Security.Cryptography.Oid> 値が入力として使用されるときに、一時的な "防御用" コピーを作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="318ad-113">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="318ad-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="318ad-114">Version introduced</span></span>

<span data-ttu-id="318ad-115">5.0</span><span class="sxs-lookup"><span data-stu-id="318ad-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="318ad-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="318ad-116">Recommended action</span></span>

<span data-ttu-id="318ad-117">オブジェクトの初期化以外に、<xref:System.Security.Cryptography.Oid> プロパティの setter を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="318ad-117">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="318ad-118">新しい値を表す場合は、既存のオブジェクトの値を変更するのではなく、新しいインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="318ad-118">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="318ad-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="318ad-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
