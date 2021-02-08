---
description: '詳細情報: <gcAllowVeryLargeObjects> 要素'
title: gcAllowVeryLargeObjects 要素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: ff8380a13c4284cc24178e185344207c3b9a39b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787020"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="30c99-103">\<gcAllowVeryLargeObjects> 要素</span><span class="sxs-lookup"><span data-stu-id="30c99-103">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="30c99-104">64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。</span><span class="sxs-lookup"><span data-stu-id="30c99-104">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="30c99-105">構文</span><span class="sxs-lookup"><span data-stu-id="30c99-105">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="30c99-106">属性</span><span class="sxs-lookup"><span data-stu-id="30c99-106">Attributes</span></span>
  
|<span data-ttu-id="30c99-107">属性</span><span class="sxs-lookup"><span data-stu-id="30c99-107">Attribute</span></span>|<span data-ttu-id="30c99-108">説明</span><span class="sxs-lookup"><span data-stu-id="30c99-108">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="30c99-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="30c99-109">Required attribute.</span></span><br /><br /> <span data-ttu-id="30c99-110">64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列が有効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="30c99-110">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="30c99-111">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="30c99-111">enabled attribute</span></span>  
  
|<span data-ttu-id="30c99-112">値</span><span class="sxs-lookup"><span data-stu-id="30c99-112">Value</span></span>|<span data-ttu-id="30c99-113">説明</span><span class="sxs-lookup"><span data-stu-id="30c99-113">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="30c99-114">合計サイズが 2 GB を超える配列は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="30c99-114">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="30c99-115">既定値です。</span><span class="sxs-lookup"><span data-stu-id="30c99-115">This is the default.</span></span>|  
|`true`|<span data-ttu-id="30c99-116">64 ビット プラットフォームで、合計サイズが 2 GB を超える配列が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="30c99-116">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="30c99-117">子要素</span><span class="sxs-lookup"><span data-stu-id="30c99-117">Child elements</span></span>  

<span data-ttu-id="30c99-118">なし。</span><span class="sxs-lookup"><span data-stu-id="30c99-118">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="30c99-119">親要素</span><span class="sxs-lookup"><span data-stu-id="30c99-119">Parent elements</span></span>
  
|<span data-ttu-id="30c99-120">要素</span><span class="sxs-lookup"><span data-stu-id="30c99-120">Element</span></span>|<span data-ttu-id="30c99-121">説明</span><span class="sxs-lookup"><span data-stu-id="30c99-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30c99-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="30c99-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="30c99-123">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="30c99-123">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30c99-124">解説</span><span class="sxs-lookup"><span data-stu-id="30c99-124">Remarks</span></span>  

 <span data-ttu-id="30c99-125">アプリケーション構成ファイルで次の要素を使用すると 2 GB を超えるサイズの配列が有効になりますが、オブジェクトのサイズや配列のサイズに対するその他の制限は変更されません。</span><span class="sxs-lookup"><span data-stu-id="30c99-125">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="30c99-126">配列の要素の最大数は <xref:System.UInt32.MaxValue?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="30c99-126">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="30c99-127">1つの次元の最大サイズは、バイト配列と1バイト構造の配列の場合は 2147483591 (0x7FFFFFC7)、他の型を含む配列の場合は 2146435071 (0X7FEFFFFF) です。</span><span class="sxs-lookup"><span data-stu-id="30c99-127">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="30c99-128">文字列およびその他の非配列オブジェクトの最大サイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="30c99-128">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="30c99-129">この機能を有効にする前に、すべての配列のサイズが 2 GB よりも小さいことを前提としたアンセーフ コードがアプリケーションに含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="30c99-129">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="30c99-130">たとえば、配列をバッファーとして使用するアンセーフコードは、配列が 2 GB を超えることを想定して記述されている場合、バッファーオーバーランの影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="30c99-130">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30c99-131">例</span><span class="sxs-lookup"><span data-stu-id="30c99-131">Example</span></span>  

 <span data-ttu-id="30c99-132">アプリケーションでこの機能を有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="30c99-132">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="30c99-133">サポート対象 :</span><span class="sxs-lookup"><span data-stu-id="30c99-133">Supported in</span></span>

<span data-ttu-id="30c99-134">.NET Framework 4.5 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="30c99-134">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="30c99-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="30c99-135">See also</span></span>

- [<span data-ttu-id="30c99-136">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="30c99-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="30c99-137">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="30c99-137">Configuration File Schema</span></span>](../index.md)
