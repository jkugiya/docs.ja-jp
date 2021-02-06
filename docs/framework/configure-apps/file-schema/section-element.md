---
description: 詳細については、下記のリンクをクリックしてください。 <section> 要素
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639940"
---
# <a name="section-element"></a><span data-ttu-id="5a2fb-104">\<section> 要素</span><span class="sxs-lookup"><span data-stu-id="5a2fb-104">\<section> element</span></span>

<span data-ttu-id="5a2fb-105">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-105">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="5a2fb-106">構文</span><span class="sxs-lookup"><span data-stu-id="5a2fb-106">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="5a2fb-107">必須属性</span><span class="sxs-lookup"><span data-stu-id="5a2fb-107">Required attributes</span></span>

|           | <span data-ttu-id="5a2fb-108">説明</span><span class="sxs-lookup"><span data-stu-id="5a2fb-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5a2fb-109">**name**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-109">**name**</span></span>  | <span data-ttu-id="5a2fb-110">構成セクションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-110">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="5a2fb-111">**type**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-111">**type**</span></span>  | <span data-ttu-id="5a2fb-112">構成ファイルからセクションを読み取る構成セクションハンドラークラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-112">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="5a2fb-113">型の値には、"完全修飾名"、"完全修飾名"、".. アセンブリ名" の構文があります。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-113">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="5a2fb-114">単純なアセンブリ名は、 *.dll* ファイル拡張子のないルートファイル名です。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-114">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="5a2fb-115">省略可能な属性</span><span class="sxs-lookup"><span data-stu-id="5a2fb-115">Optional attributes</span></span>

<span data-ttu-id="5a2fb-116">次の属性は、ASP.NET アプリケーションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-116">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="5a2fb-117">構成システムは、他のアプリケーションの種類に対してこれらの属性を無視します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-117">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="5a2fb-118">説明</span><span class="sxs-lookup"><span data-stu-id="5a2fb-118">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="5a2fb-119">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-119">**allowDefinition**</span></span> | <span data-ttu-id="5a2fb-120">セクションを使用できる構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-120">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="5a2fb-121">次のいずれかの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-121">Use one of the following values:</span></span><br><br><span data-ttu-id="5a2fb-122">**すべての場所**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-122">**Everywhere**</span></span><br><span data-ttu-id="5a2fb-123">すべての構成ファイルでセクションを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-123">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="5a2fb-124">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-124">This is the default.</span></span><br><span data-ttu-id="5a2fb-125">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-125">**MachineOnly**</span></span><br><span data-ttu-id="5a2fb-126">セクションをコンピューターの構成ファイル (*Machine.config*) でのみ使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-126">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="5a2fb-127">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-127">**MachineToApplication**</span></span><br><span data-ttu-id="5a2fb-128">コンピューターの構成ファイルまたはアプリケーション構成ファイルでセクションを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-128">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="5a2fb-129">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-129">**allowLocation**</span></span>   | <span data-ttu-id="5a2fb-130">要素内でセクションを使用できるかどうかを判断し **\<location>** ます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-130">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="5a2fb-131">次のいずれかの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-131">Use one of the following values:</span></span><br><br><span data-ttu-id="5a2fb-132">**true**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-132">**true**</span></span><br><span data-ttu-id="5a2fb-133">要素内でセクションを使用できるようにし **\<location>** ます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-133">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="5a2fb-134">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-134">This is the default.</span></span><br><span data-ttu-id="5a2fb-135">**false**</span><span class="sxs-lookup"><span data-stu-id="5a2fb-135">**false**</span></span><br><span data-ttu-id="5a2fb-136">では、要素内でセクションを使用することはできません **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-136">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="5a2fb-137">親要素</span><span class="sxs-lookup"><span data-stu-id="5a2fb-137">Parent elements</span></span>

|     | <span data-ttu-id="5a2fb-138">説明</span><span class="sxs-lookup"><span data-stu-id="5a2fb-138">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5a2fb-139">**\<configSections>** 要素</span><span class="sxs-lookup"><span data-stu-id="5a2fb-139">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="5a2fb-140">構成セクションと名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-140">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="5a2fb-141">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="5a2fb-141">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="5a2fb-142">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-142">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="5a2fb-143">**\<section>** 要素はまたはのいずれかの子要素であり、両方では **\<configSections>** **\<sectionGroup>** ありません。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-143">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="5a2fb-144">子要素</span><span class="sxs-lookup"><span data-stu-id="5a2fb-144">Child elements</span></span>

<span data-ttu-id="5a2fb-145">なし</span><span class="sxs-lookup"><span data-stu-id="5a2fb-145">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5a2fb-146">解説</span><span class="sxs-lookup"><span data-stu-id="5a2fb-146">Remarks</span></span>

<span data-ttu-id="5a2fb-147">構成セクションを宣言すると、基本的に構成ファイルの新しい要素が定義されます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-147">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="5a2fb-148">新しい要素には、構成セクションハンドラー (つまり、インターフェイスを実装するクラス) の読み取りの設定が含まれ <xref:System.Configuration.IConfigurationSectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-148">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="5a2fb-149">定義するセクションの属性と子要素は、設定の読み取りに使用するセクションハンドラーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-149">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="5a2fb-150">*Machine.config* ファイルで構成セクションハンドラーを宣言すると、 **allowdefinition** 属性で特に指定されていない限り、そのコンピューター上の任意のアプリケーション構成ファイルの構成セクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-150">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="5a2fb-151">例</span><span class="sxs-lookup"><span data-stu-id="5a2fb-151">Example</span></span>

<span data-ttu-id="5a2fb-152">次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-152">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5a2fb-153">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="5a2fb-153">Configuration file</span></span>

<span data-ttu-id="5a2fb-154">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2fb-154">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a2fb-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a2fb-155">See also</span></span>

- [<span data-ttu-id="5a2fb-156">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="5a2fb-156">Configuration file schema for the .NET Framework</span></span>](index.md)
