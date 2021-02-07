---
description: '詳細情報: <linkedConfiguration> 要素'
title: <linkedConfiguration> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: e4312cf788784241efc35304b632dfe1fdef1bc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698662"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="07e12-103">\<linkedConfiguration> 要素</span><span class="sxs-lookup"><span data-stu-id="07e12-103">\<linkedConfiguration> element</span></span>

<span data-ttu-id="07e12-104">インクルードする構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="07e12-104">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="07e12-105">構文</span><span class="sxs-lookup"><span data-stu-id="07e12-105">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="07e12-106">属性</span><span class="sxs-lookup"><span data-stu-id="07e12-106">Attribute</span></span>

|           | <span data-ttu-id="07e12-107">説明</span><span class="sxs-lookup"><span data-stu-id="07e12-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="07e12-108">**href**</span><span class="sxs-lookup"><span data-stu-id="07e12-108">**href**</span></span>  | <span data-ttu-id="07e12-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="07e12-109">Required attribute.</span></span><br><br><span data-ttu-id="07e12-110">含める構成ファイルの URL。</span><span class="sxs-lookup"><span data-stu-id="07e12-110">The URL of the configuration file to include.</span></span> <span data-ttu-id="07e12-111">**Href** 属性でサポートされている形式はのみ `file://` です。</span><span class="sxs-lookup"><span data-stu-id="07e12-111">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="07e12-112">ローカルファイルと UNC ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="07e12-112">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="07e12-113">親要素</span><span class="sxs-lookup"><span data-stu-id="07e12-113">Parent element</span></span>

|     | <span data-ttu-id="07e12-114">説明</span><span class="sxs-lookup"><span data-stu-id="07e12-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="07e12-115">**\<assemblyBinding>** 要素</span><span class="sxs-lookup"><span data-stu-id="07e12-115">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="07e12-116">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="07e12-116">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07e12-117">子要素</span><span class="sxs-lookup"><span data-stu-id="07e12-117">Child elements</span></span>

<span data-ttu-id="07e12-118">なし</span><span class="sxs-lookup"><span data-stu-id="07e12-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="07e12-119">解説</span><span class="sxs-lookup"><span data-stu-id="07e12-119">Remarks</span></span>

<span data-ttu-id="07e12-120">要素は、 **\<linkedConfiguration>** コンポーネントアセンブリのサービスを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="07e12-120">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="07e12-121">既知の場所に構成ファイルが存在するアセンブリを1つ以上のアプリケーションが使用する場合、そのアセンブリを使用するアプリケーションの構成ファイルでは、 **\<linkedConfiguration>** 構成情報を直接含めるのではなく、要素を使用してアセンブリ構成ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="07e12-121">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="07e12-122">コンポーネントアセンブリがサービスされている場合、共通構成ファイルを更新すると、そのアセンブリを使用するすべてのアプリケーションに対して、更新された構成情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="07e12-122">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="07e12-123">**\<linkedConfiguration>** 要素は、Windows サイドバイサイドマニフェストを持つアプリケーションではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="07e12-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="07e12-124">次の規則は、リンクされた構成ファイルの使用を制御します。</span><span class="sxs-lookup"><span data-stu-id="07e12-124">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="07e12-125">インクルードされる構成ファイルの設定は、ローダーバインドポリシーにのみ影響し、ローダーによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="07e12-125">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="07e12-126">含まれる構成ファイルには、バインドポリシー以外の設定を含めることができますが、これらの設定は何の効果もありません。</span><span class="sxs-lookup"><span data-stu-id="07e12-126">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="07e12-127">属性でサポートされている形式 `href` はのみ `file://` です。</span><span class="sxs-lookup"><span data-stu-id="07e12-127">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="07e12-128">ローカルファイルと UNC ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="07e12-128">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="07e12-129">構成ファイルごとにリンクされる構成の数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="07e12-129">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="07e12-130">`#include`C/c + + のディレクティブの動作と同様に、すべてのリンクされた構成ファイルが1つのファイルに結合されます。</span><span class="sxs-lookup"><span data-stu-id="07e12-130">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="07e12-131">**\<linkedConfiguration>** 要素は、アプリケーション構成ファイル内でのみ許可されます。 *Machine.config* では無視されます。</span><span class="sxs-lookup"><span data-stu-id="07e12-131">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="07e12-132">循環参照が検出され、終了します。</span><span class="sxs-lookup"><span data-stu-id="07e12-132">Circular references are detected and terminated.</span></span> <span data-ttu-id="07e12-133">つまり、 **\<linkedConfiguration>** 一連の構成ファイルの要素がループを形成すると、ループが検出され、停止されます。</span><span class="sxs-lookup"><span data-stu-id="07e12-133">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="07e12-134">例</span><span class="sxs-lookup"><span data-stu-id="07e12-134">Example</span></span>

<span data-ttu-id="07e12-135">次の例は、ローカルハードディスクの構成ファイルを含める方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="07e12-135">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="07e12-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="07e12-136">See also</span></span>

- [<span data-ttu-id="07e12-137">**\<assemblyBinding>** 要素</span><span class="sxs-lookup"><span data-stu-id="07e12-137">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="07e12-138">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="07e12-138">Configuration file schema for the .NET Framework</span></span>](index.md)
