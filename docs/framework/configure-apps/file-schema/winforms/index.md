---
description: 詳細については、「Windows フォーム構成」セクションを参照してください。
title: Windows フォームの構成セクション
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: f1eaf2d74c7645d6cf4580d75e23d8910628cce0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697765"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="82af7-103">Windows フォームの構成セクション</span><span class="sxs-lookup"><span data-stu-id="82af7-103">Windows Forms Configuration Section</span></span>

<span data-ttu-id="82af7-104">Windows フォームの構成設定により、カスタマイズされたアプリケーション設定に関する情報 (マルチ モニターや高 DPI のサポート、その他の定義済みの構成設定など) を Windows フォームのアプリで格納したり、取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="82af7-104">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="82af7-105">Windows フォームのアプリケーション構成設定は、アプリケーション構成ファイルの `System.Windows.Forms.ApplicationConfigurationSection` 要素に格納されます。</span><span class="sxs-lookup"><span data-stu-id="82af7-105">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="82af7-106">構文</span><span class="sxs-lookup"><span data-stu-id="82af7-106">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82af7-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="82af7-107">Attributes and elements</span></span>

<span data-ttu-id="82af7-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="82af7-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82af7-109">属性</span><span class="sxs-lookup"><span data-stu-id="82af7-109">Attributes</span></span>

<span data-ttu-id="82af7-110">なし。</span><span class="sxs-lookup"><span data-stu-id="82af7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82af7-111">子要素</span><span class="sxs-lookup"><span data-stu-id="82af7-111">Child elements</span></span>

<span data-ttu-id="82af7-112">要素</span><span class="sxs-lookup"><span data-stu-id="82af7-112">Element</span></span>  |<span data-ttu-id="82af7-113">説明</span><span class="sxs-lookup"><span data-stu-id="82af7-113">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="82af7-114">指定した値を持つ構成設定キーを追加します</span><span class="sxs-lookup"><span data-stu-id="82af7-114">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="82af7-115">親要素</span><span class="sxs-lookup"><span data-stu-id="82af7-115">Parent elements</span></span>

<span data-ttu-id="82af7-116">要素</span><span class="sxs-lookup"><span data-stu-id="82af7-116">Element</span></span>  |<span data-ttu-id="82af7-117">説明</span><span class="sxs-lookup"><span data-stu-id="82af7-117">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="82af7-118">共通言語ランタイムと Windows フォームのアプリケーションで使用されるすべての構成ファイルのルート要素です</span><span class="sxs-lookup"><span data-stu-id="82af7-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="82af7-119">解説</span><span class="sxs-lookup"><span data-stu-id="82af7-119">Remarks</span></span>

<span data-ttu-id="82af7-120">.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ApplicationConfigurationSection>` 要素で構成できます。</span><span class="sxs-lookup"><span data-stu-id="82af7-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="82af7-121">要素には `<System.Windows.Forms.ApplicationConfigurationSection>` 1 つ以上の子要素を含めることができ [`<add>`](windows-forms-add-configuration-element.md) 、それぞれが特定の構成設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="82af7-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="82af7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="82af7-122">See also</span></span>

- [<span data-ttu-id="82af7-123">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="82af7-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="82af7-124">Windows フォームでの高 DPI サポート</span><span class="sxs-lookup"><span data-stu-id="82af7-124">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
