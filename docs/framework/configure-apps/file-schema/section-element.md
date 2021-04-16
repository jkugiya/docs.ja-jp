---
description: 各項目の詳細情報 <section> 要素
title: <section> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 7756f7ee3be2391a0d068708f3719083640b5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639940"
---
# <a name="section-element"></a><span data-ttu-id="d4dee-104">\<section> 要素</span><span class="sxs-lookup"><span data-stu-id="d4dee-104">\<section> element</span></span>

<span data-ttu-id="d4dee-105">構成セクション宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4dee-105">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="d4dee-106">構文</span><span class="sxs-lookup"><span data-stu-id="d4dee-106">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="d4dee-107">必須属性</span><span class="sxs-lookup"><span data-stu-id="d4dee-107">Required attributes</span></span>

|           | <span data-ttu-id="d4dee-108">説明</span><span class="sxs-lookup"><span data-stu-id="d4dee-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d4dee-109">**name**</span><span class="sxs-lookup"><span data-stu-id="d4dee-109">**name**</span></span>  | <span data-ttu-id="d4dee-110">構成セクションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-110">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="d4dee-111">**type**</span><span class="sxs-lookup"><span data-stu-id="d4dee-111">**type**</span></span>  | <span data-ttu-id="d4dee-112">構成ファイルからセクションを読み取る構成セクション ハンドラー クラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-112">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="d4dee-113">型の値には、"完全修飾セクション ハンドラー クラス名, 単純アセンブリ名" という構文があります。</span><span class="sxs-lookup"><span data-stu-id="d4dee-113">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="d4dee-114">単純アセンブリ名は、 *.dll* ファイル拡張子のないルート ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="d4dee-114">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="d4dee-115">省略可能な属性</span><span class="sxs-lookup"><span data-stu-id="d4dee-115">Optional attributes</span></span>

<span data-ttu-id="d4dee-116">次の属性は、ASP.NET アプリケーションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-116">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="d4dee-117">構成システムでは、他のアプリケーションの種類に対してこれらの属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-117">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="d4dee-118">説明</span><span class="sxs-lookup"><span data-stu-id="d4dee-118">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="d4dee-119">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="d4dee-119">**allowDefinition**</span></span> | <span data-ttu-id="d4dee-120">セクションを使用できる構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-120">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="d4dee-121">次のいずれかの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-121">Use one of the following values:</span></span><br><br><span data-ttu-id="d4dee-122">**すべての場所**</span><span class="sxs-lookup"><span data-stu-id="d4dee-122">**Everywhere**</span></span><br><span data-ttu-id="d4dee-123">セクションをすべての構成ファイルで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d4dee-123">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="d4dee-124">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d4dee-124">This is the default.</span></span><br><span data-ttu-id="d4dee-125">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="d4dee-125">**MachineOnly**</span></span><br><span data-ttu-id="d4dee-126">セクションを、コンピューターの構成ファイル (*Machine.config*) でのみ使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d4dee-126">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="d4dee-127">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="d4dee-127">**MachineToApplication**</span></span><br><span data-ttu-id="d4dee-128">セクションを、マシン構成ファイルまたはアプリケーション構成ファイルで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d4dee-128">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="d4dee-129">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="d4dee-129">**allowLocation**</span></span>   | <span data-ttu-id="d4dee-130">セクションを **\<location>** 要素内で使用できるようにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-130">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="d4dee-131">次のいずれかの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-131">Use one of the following values:</span></span><br><br><span data-ttu-id="d4dee-132">**true**</span><span class="sxs-lookup"><span data-stu-id="d4dee-132">**true**</span></span><br><span data-ttu-id="d4dee-133">セクションを **\<location>** 要素内で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d4dee-133">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="d4dee-134">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d4dee-134">This is the default.</span></span><br><span data-ttu-id="d4dee-135">**false**</span><span class="sxs-lookup"><span data-stu-id="d4dee-135">**false**</span></span><br><span data-ttu-id="d4dee-136">セクションを **\<location>** 要素内で使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="d4dee-136">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="d4dee-137">親要素</span><span class="sxs-lookup"><span data-stu-id="d4dee-137">Parent elements</span></span>

|     | <span data-ttu-id="d4dee-138">説明</span><span class="sxs-lookup"><span data-stu-id="d4dee-138">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d4dee-139"> **\<configSections>** 要素</span><span class="sxs-lookup"><span data-stu-id="d4dee-139">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d4dee-140">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4dee-140">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="d4dee-141"> **\<sectionGroup>** 要素</span><span class="sxs-lookup"><span data-stu-id="d4dee-141">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="d4dee-142">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4dee-142">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="d4dee-143">**\<section>** 要素は **\<configSections>** または **\<sectionGroup>** のいずれかの子要素ですが、両方の子要素ではありません。</span><span class="sxs-lookup"><span data-stu-id="d4dee-143">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="d4dee-144">子要素</span><span class="sxs-lookup"><span data-stu-id="d4dee-144">Child elements</span></span>

<span data-ttu-id="d4dee-145">なし</span><span class="sxs-lookup"><span data-stu-id="d4dee-145">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d4dee-146">解説</span><span class="sxs-lookup"><span data-stu-id="d4dee-146">Remarks</span></span>

<span data-ttu-id="d4dee-147">構成セクションを宣言すると、基本的に構成ファイルの新しい要素が定義されます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-147">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="d4dee-148">新しい要素には、構成セクション ハンドラー (つまり、<xref:System.Configuration.IConfigurationSectionHandler> インターフェイスを実装するクラス) によって読み取られる設定が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-148">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="d4dee-149">定義するセクションの属性と子要素は、設定の読み取りに使用するセクション ハンドラーによって変わってきます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-149">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="d4dee-150">*Machine.config* ファイルで構成セクション ハンドラーを宣言した場合は、**allowDefinition** 属性で特に指定されていない限り、そのコンピューター上の任意のアプリケーション構成ファイル内の構成セクションを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d4dee-150">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="d4dee-151">例</span><span class="sxs-lookup"><span data-stu-id="d4dee-151">Example</span></span>

<span data-ttu-id="d4dee-152">次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4dee-152">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d4dee-153">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="d4dee-153">Configuration file</span></span>

<span data-ttu-id="d4dee-154">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーション ディレクトリ レベルではない *Web.config* ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4dee-154">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4dee-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4dee-155">See also</span></span>

- [<span data-ttu-id="d4dee-156">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="d4dee-156">Configuration file schema for the .NET Framework</span></span>](index.md)
