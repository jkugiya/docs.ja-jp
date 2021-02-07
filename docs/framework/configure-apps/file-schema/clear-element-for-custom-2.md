---
description: '詳細情報: <clear> NameValueSectionHandler および DictionarySectionHandler の要素'
title: <clear> NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: 896aa7e8f0e3b41574538fcd9e4be9d6155da889
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699234"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="a4ffc-103">\<clear> NameValueSectionHandler および DictionarySectionHandler の要素</span><span class="sxs-lookup"><span data-stu-id="a4ffc-103">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="a4ffc-104">セクションで以前に定義したすべての設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-104">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="a4ffc-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4ffc-105">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="a4ffc-106">属性</span><span class="sxs-lookup"><span data-stu-id="a4ffc-106">Attributes</span></span>

<span data-ttu-id="a4ffc-107">なし</span><span class="sxs-lookup"><span data-stu-id="a4ffc-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a4ffc-108">親要素</span><span class="sxs-lookup"><span data-stu-id="a4ffc-108">Parent element</span></span>

|     | <span data-ttu-id="a4ffc-109">説明</span><span class="sxs-lookup"><span data-stu-id="a4ffc-109">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="a4ffc-110">**\<sectionName>** 要素</span><span class="sxs-lookup"><span data-stu-id="a4ffc-110">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="a4ffc-111">クラスおよびクラスを使用するカスタム構成セクションの設定を定義し <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-111">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a4ffc-112">子要素</span><span class="sxs-lookup"><span data-stu-id="a4ffc-112">Child elements</span></span>

<span data-ttu-id="a4ffc-113">なし</span><span class="sxs-lookup"><span data-stu-id="a4ffc-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a4ffc-114">解説</span><span class="sxs-lookup"><span data-stu-id="a4ffc-114">Remarks</span></span>

<span data-ttu-id="a4ffc-115">要素を使用して、 **\<clear>** 構成ファイル階層の上位レベルで定義されているすべての設定をアプリケーションから削除できます。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-115">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="a4ffc-116">例</span><span class="sxs-lookup"><span data-stu-id="a4ffc-116">Example</span></span>

<span data-ttu-id="a4ffc-117">この例では、コンピューター構成ファイルとアプリケーション構成ファイルを定義し、 **\<clear>** アプリケーション構成ファイルで要素を使用して、マシン構成ファイルで以前に定義したセクションをクリアする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-117">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="a4ffc-118">次のマシン構成ファイルのコードでは、セクションを宣言してい **\<mySection>** ます。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-118">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="a4ffc-119">次のアプリケーション構成ファイルのコードは、からすべての設定を削除し **\<mySection>** ます。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-119">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="a4ffc-120">アプリケーションは、 **\<mySection>** コンピューター構成ファイルのセクションので宣言された設定を取得できません。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-120">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="a4ffc-121">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a4ffc-121">Configuration file</span></span>

<span data-ttu-id="a4ffc-122">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4ffc-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4ffc-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4ffc-123">See also</span></span>

- [<span data-ttu-id="a4ffc-124">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="a4ffc-124">Configuration file schema for the .NET Framework</span></span>](index.md)
