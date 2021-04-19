---
title: ユーザー補助のベスト プラクティス
description: .NET でのアクセシビリティのベスト プラクティスについて説明します。 プログラムによるアクセス、ユーザー設定、視覚的な UI デザイン、ナビゲーション、マルチモーダル インターフェイスについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: e2a540678b9f802a3b06a5f3091a7bde33d99739
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427010"
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="8b09d-104">アクセシビリティのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="8b09d-104">Accessibility best practices</span></span>

> [!NOTE]
> <span data-ttu-id="8b09d-105">この記事は、<xref:System.Windows.Automation> 名前空間で定義されているマネージド UI オートメーション クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-105">This article is intended for .NET Framework developers who want to use the managed UI Automation classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8b09d-106">UI オートメーションの最新情報については、[Windows Automation API の「UI オートメーション」](/windows/win32/winauto/entry-uiauto-win32)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-106">For the latest information about UI Automation, see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="8b09d-107">コントロールやアプリケーションで以下のベスト プラクティスを実行すると、支援技術デバイスを使用するユーザーのアクセシビリティ が向上します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-107">Implementing the following best practices in controls or applications will improve their accessibility for people who use assistive technology devices.</span></span> <span data-ttu-id="8b09d-108">このようなベスト プラクティスの多くは、優れたユーザー インターフェイス (UI) の設計に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-108">Many of these best practices focus on good user interface (UI) design.</span></span> <span data-ttu-id="8b09d-109">各ベスト プラクティスには、Windows Presentation Foundation (WPF) のコントロールやアプリケーションの実装情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-109">Each best practice includes implementation information for Windows Presentation Foundation (WPF) controls or applications.</span></span> <span data-ttu-id="8b09d-110">多くの場合、これらのベスト プラクティスに対応する作業は既に WPF コントロールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-110">In many cases, the work to meet these best practices is already included in WPF controls.</span></span>

<a name="Programmatic_Access"></a>

## <a name="programmatic-access"></a><span data-ttu-id="8b09d-111">プログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="8b09d-111">Programmatic Access</span></span>

<span data-ttu-id="8b09d-112">プログラムによるアクセスにより、すべての UI 要素にラベルが付き、プロパティの値が公開され、適切なイベントが発生するようになります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-112">Programmatic access involves ensuring that all UI elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="8b09d-113">標準の WPF コントロールでは、この作業の大部分が <xref:System.Windows.Automation.Peers.AutomationPeer> を介して既に実行されています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-113">For standard WPF controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="8b09d-114">カスタム コントロールでは、プログラムによるアクセスが正しく実装されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-114">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>

<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>

### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="8b09d-115">すべての UI 要素とテキストでのプログラムによるアクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="8b09d-115">Enable Programmatic Access to all UI Elements and Text</span></span>

<span data-ttu-id="8b09d-116">ユーザー インターフェイス (UI) 要素は、プログラムによるアクセスを可能にするようにします。</span><span class="sxs-lookup"><span data-stu-id="8b09d-116">User interface (UI) elements should enable programmatic access.</span></span> <span data-ttu-id="8b09d-117">UI が標準的な WPF コントロールである場合、プログラムによるアクセスのサポートがコントロールに含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b09d-117">If the UI is a standard WPF control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="8b09d-118">コントロールがカスタム コントロール (コモン コントロールのサブクラスに指定されているコントロール、またはコントロールからサブクラスに指定されたコントロール) である場合、変更が必要な領域に対する <xref:System.Windows.Automation.Peers.AutomationPeer> の実装を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-118">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>

<span data-ttu-id="8b09d-119">このベスト プラクティスに従うことで支援技術ベンダーは、製品の UI の要素を特定および操作することができます。</span><span class="sxs-lookup"><span data-stu-id="8b09d-119">Following this best practice allows assistive technology vendors to identify and manipulate elements of your product's UI.</span></span>

<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>

### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="8b09d-120">UI オブジェクト、フレーム、およびページにおける、場所の名前、タイトル、説明</span><span class="sxs-lookup"><span data-stu-id="8b09d-120">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>

<span data-ttu-id="8b09d-121">スクリーン リーダーなどの支援のテクノロジでは、ナビゲーション スキーム内のフレーム、オブジェクト、またはページの場所を理解するためにタイトルを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-121">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="8b09d-122">そのため、タイトルはわかりやすくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-122">Therefore, the title must be descriptive.</span></span> <span data-ttu-id="8b09d-123">たとえば、「Microsoft Web ページ」といった Web ページのタイトルでは、ユーザーはいくつかの特定の領域に深く入っていった場合に役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="8b09d-123">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="8b09d-124">わかりやすいタイトルは、スクリーン リーダーに依存する視覚障がい者にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="8b09d-124">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="8b09d-125">同様に、WPF コントロールの場合、<xref:System.Windows.Automation.AutomationProperties.NameProperty> と <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> が支援技術デバイスにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="8b09d-125">Similarly, for WPF controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for assistive technology devices.</span></span>

<span data-ttu-id="8b09d-126">このベスト プラクティスに従うことで、支援技術により、サンプル コントロールやアプリケーションの UI を識別して操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-126">Following this best practice allows assistive technologies to identify and manipulate UI in sample controls and applications.</span></span>

<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>

### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="8b09d-127">プログラムによるイベントが、すべての UI 操作によってトリガーされることを確認する</span><span class="sxs-lookup"><span data-stu-id="8b09d-127">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>

<span data-ttu-id="8b09d-128">このベスト プラクティスに従うことで、支援技術により、UI の変更をリッスンし、その変更についてユーザーに通知することができます。</span><span class="sxs-lookup"><span data-stu-id="8b09d-128">Following this best practice allows assistive technologies to listen for changes in the UI and notify the user about these changes.</span></span>

<a name="User_Settings"></a>

## <a name="user-settings"></a><span data-ttu-id="8b09d-129">ユーザー設定</span><span class="sxs-lookup"><span data-stu-id="8b09d-129">User Settings</span></span>

<span data-ttu-id="8b09d-130">このセクションのベスト プラクティスでは、コントロールやアプリケーションはユーザー設定をオーバーライドしないようにします。</span><span class="sxs-lookup"><span data-stu-id="8b09d-130">The best practice in this section ensures that controls or applications do not override user settings.</span></span>

<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>

### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="8b09d-131">すべてのシステム全体の設定を尊重し、ユーザー補助機能に干渉しない</span><span class="sxs-lookup"><span data-stu-id="8b09d-131">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>

<span data-ttu-id="8b09d-132">ユーザーは、コントロール パネルを使用して、システム全体のフラグを設定できます。その他のフラグはプログラムで設定できます。</span><span class="sxs-lookup"><span data-stu-id="8b09d-132">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="8b09d-133">これらの設定は、コントロールやアプリケーションで変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-133">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="8b09d-134">また、アプリケーションは、ホスト オペレーティング システムのユーザー補助の設定をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-134">Also, applications must support the accessibility settings of their host operating system.</span></span>

<span data-ttu-id="8b09d-135">このベスト プラクティスに従うことにより、ユーザーはユーザー補助の設定を行えるとともに、これらの設定がアプリケーションによって変更されないことを認識できます。</span><span class="sxs-lookup"><span data-stu-id="8b09d-135">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>

<a name="Visual_UI_Design"></a>

## <a name="visual-ui-design"></a><span data-ttu-id="8b09d-136">UI のビジュアル デザイン</span><span class="sxs-lookup"><span data-stu-id="8b09d-136">Visual UI Design</span></span>

<span data-ttu-id="8b09d-137">このセクションのベスト プラクティスでは、コントロールまたはアプリケーションが色と画像を効果的に使用するとともに、支援技術によって使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8b09d-137">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by Assistive technologies.</span></span>

<a name="Don_t_Hard_Code_Colors"></a>

### <a name="dont-hard-code-colors"></a><span data-ttu-id="8b09d-138">色をハードコーディングしない</span><span class="sxs-lookup"><span data-stu-id="8b09d-138">Don't Hard-Code Colors</span></span>

<span data-ttu-id="8b09d-139">色覚に障がいがあるユーザー、弱視のユーザー、または白黒の画面を使用するユーザーは、ハード コーディングされた色を持つアプリケーションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="8b09d-139">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>

<span data-ttu-id="8b09d-140">このベスト プラクティスに従うことにより、ユーザーは、個人のニーズに基づいて色の組み合わせを調整できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-140">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>

<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>

### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="8b09d-141">ハイ コントラストとすべてのシステム表示属性をサポートする</span><span class="sxs-lookup"><span data-stu-id="8b09d-141">Support High Contrast and all System Display Attributes</span></span>

<span data-ttu-id="8b09d-142">アプリケーションは、ユーザーが選択したシステム全体のコントラスト設定、色の選択、またはその他のシステム全体のディスプレイの設定と属性を中断または無効にしてはなりません。</span><span class="sxs-lookup"><span data-stu-id="8b09d-142">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="8b09d-143">ユーザーが採用しているシステム全体の設定は、アプリケーションのユーザー補助機能を強化します。そのため、これをアプリケーションによって無効にしたり、無視したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-143">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="8b09d-144">色は、正しいコントラストを提供するため、正しい前景色と背景色の組み合わせで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-144">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="8b09d-145">関係のない色を混ぜないでください。また、色を反転させないでください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-145">Don't mix unrelated colors, and don't reverse colors.</span></span>

<span data-ttu-id="8b09d-146">黒の背景に白いテキストなど、特定のハイ コントラストの組み合わせが必要なユーザーは多数います。</span><span class="sxs-lookup"><span data-stu-id="8b09d-146">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="8b09d-147">それらを反転させて、白地に黒のテキストとして描画すると、前景色の上に背景色がにじみ、一部のユーザーには読みづらくなります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-147">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>

<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>

### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="8b09d-148">すべての DPI 設定によってすべての UI を正しく拡大/縮小する</span><span class="sxs-lookup"><span data-stu-id="8b09d-148">Ensure All UI Correctly Scales by Any DPI Setting</span></span>

<span data-ttu-id="8b09d-149">すべての UI が、どのような ドット/インチ (dpi) 設定でも正しく拡大縮小できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-149">Ensure that all UI can correctly scale by any dots per inch (dpi) setting.</span></span> <span data-ttu-id="8b09d-150">また、1024×768、120 ドット/インチ (dpi) の画面に UI 要素が収まるようにします。</span><span class="sxs-lookup"><span data-stu-id="8b09d-150">Also, ensure that UI elements fit in a screen of 1024 x 768 with 120 dots per inch (dpi).</span></span>

<a name="Navigation"></a>

## <a name="navigation"></a><span data-ttu-id="8b09d-151">［ナビゲーション］</span><span class="sxs-lookup"><span data-stu-id="8b09d-151">Navigation</span></span>

<span data-ttu-id="8b09d-152">このセクションのベスト プラクティスでは、ナビゲーションがコントロールとアプリケーションで対処されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-152">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>

<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>

### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="8b09d-153">すべての UI 要素にキーボード インターフェイスを指定する</span><span class="sxs-lookup"><span data-stu-id="8b09d-153">Provide Keyboard Interface for All UI Elements</span></span>

<span data-ttu-id="8b09d-154">タブ ストップは、特に慎重に計画された場合は、ユーザーが UI をナビゲートする別の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-154">Tab stops, especially when carefully planned, give users another way to navigate the UI.</span></span>

<span data-ttu-id="8b09d-155">アプリケーションは、次のキーボード インターフェイスを備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-155">Applications should provide the following keyboard interfaces:</span></span>

- <span data-ttu-id="8b09d-156">ボタン、リンク、またはリスト ボックスなど、ユーザーが操作できるすべてのコントロールのタブ ストップ</span><span class="sxs-lookup"><span data-stu-id="8b09d-156">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>
- <span data-ttu-id="8b09d-157">論理的なタブの順序</span><span class="sxs-lookup"><span data-stu-id="8b09d-157">logical tab order</span></span>

<a name="Show_the_Keyboard_Focus"></a>

### <a name="show-the-keyboard-focus"></a><span data-ttu-id="8b09d-158">キーボード フォーカスの表示</span><span class="sxs-lookup"><span data-stu-id="8b09d-158">Show the Keyboard Focus</span></span>

<span data-ttu-id="8b09d-159">ユーザーがキーストロークの効果を予測できるように、ユーザーはどのオブジェクトにキーボード フォーカスがあるかを認識しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-159">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="8b09d-160">キーボード フォーカスを強調表示するには、色、フォント、または四角形や拡大などのグラフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-160">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="8b09d-161">キーボード フォーカスを音声で強調表示するには、音量、音の高さ、または音質を変更します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-161">To audibly highlight the keyboard focus, change the volume, pitch, or tonal quality.</span></span>

<span data-ttu-id="8b09d-162">混乱を回避するには、アプリケーションはビジュアル フォーカス インジケーターをすべて非表示にし、非アクティブなウィンドウ (またはペイン) にある選択項目を暗くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-162">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>

<span data-ttu-id="8b09d-163">アプリケーションは、キーボード フォーカスで以下を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-163">Applications should do the following with keyboard focus:</span></span>

- <span data-ttu-id="8b09d-164">1 つの項目が常にキーボード フォーカスされている必要がある</span><span class="sxs-lookup"><span data-stu-id="8b09d-164">one item should always have keyboard focus</span></span>
- <span data-ttu-id="8b09d-165">キーボード フォーカスは明確に表示されている必要がある</span><span class="sxs-lookup"><span data-stu-id="8b09d-165">keyboard focus should be visible and obvious</span></span>
- <span data-ttu-id="8b09d-166">選択項目またはフォーカスされた項目は視覚的に強調表示されている必要がある</span><span class="sxs-lookup"><span data-stu-id="8b09d-166">selections and/or focused items should be visually highlighted</span></span>

<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>

### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="8b09d-167">ナビゲーションの標準と強力なナビゲーション スキームをサポートする</span><span class="sxs-lookup"><span data-stu-id="8b09d-167">Support Navigation Standards and Powerful Navigation Schemes</span></span>

<span data-ttu-id="8b09d-168">さまざまなキーボード ナビゲーションの側面で、ユーザーが UI をナビゲートするさまざまな方法が提供されています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-168">Different aspects of keyboard navigation provide different ways for users to navigate the UI.</span></span>

<span data-ttu-id="8b09d-169">アプリケーションは、次のキーボード インターフェイスを備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-169">Applications should provide the following keyboard interfaces:</span></span>

- <span data-ttu-id="8b09d-170">すべてのコマンド、メニュー、およびコントロール用のショートカット キーと下線付きのアクセス キー</span><span class="sxs-lookup"><span data-stu-id="8b09d-170">shortcut keys and underlined access keys for all commands, menus, and controls</span></span>
- <span data-ttu-id="8b09d-171">重要なリンクへのキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="8b09d-171">keyboard shortcuts to important links</span></span>
- <span data-ttu-id="8b09d-172">すべてのメニュー項目にアクセス キーがあり、すべてのボタンにアクセラレータ キーがあり、すべてのコマンドにアクセラレータ キーがある</span><span class="sxs-lookup"><span data-stu-id="8b09d-172">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>

<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>

### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="8b09d-173">マウスの位置がキーボード ナビゲーションと干渉しないようにする</span><span class="sxs-lookup"><span data-stu-id="8b09d-173">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>

<span data-ttu-id="8b09d-174">マウスの位置は、キーボードのナビゲーションと干渉しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-174">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="8b09d-175">たとえば、マウスが別の場所に位置し、ユーザーがキーボードでナビゲートする場合、マウスのクリックは、ユーザーが開始するまで発生しないようにします。</span><span class="sxs-lookup"><span data-stu-id="8b09d-175">For example, if the mouse is positioned some place and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>

<a name="Multimodal_Interface"></a>

## <a name="multimodal-interface"></a><span data-ttu-id="8b09d-176">マルチモーダル インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b09d-176">Multimodal Interface</span></span>

<span data-ttu-id="8b09d-177">このセクションのベスト プラクティスでは、アプリケーション UI にはビジュアル要素の代替案が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b09d-177">Best Practices in this section ensure that application UI includes alternatives for visual elements.</span></span>

<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>

### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="8b09d-178">テキスト以外の要素に相当する、ユーザーが選択可能な項目を提供する</span><span class="sxs-lookup"><span data-stu-id="8b09d-178">Provide User-Selectable Equivalents for Non-Text Elements</span></span>

<span data-ttu-id="8b09d-179">テキスト以外の各要素について、テキスト、チャット内容、または音声による説明 (代替テキスト、キャプション、視覚的なフィードバックなど) に相当する、ユーザーが選択可能な項目を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-179">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>

<!-- markdownlint-disable DOCSMD011 -->
<span data-ttu-id="8b09d-180">テキスト以外の要素には、幅広い範囲の UI 要素 (画像、画像マップ領域、アニメーション、アプレット、フレーム、スクリプト、グラフィカルなボタン、サウンド、スタンドアロンのオーディオ ファイル、およびビデオなど) があります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-180">Non-text elements cover a wide range of UI elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files, and video.</span></span> <span data-ttu-id="8b09d-181">テキスト以外の要素は、UI のコンテンツを理解するためにユーザーがアクセスを必要とする視覚的な情報、音声、または通常のオーディオ情報が含まれる場合は重要になります。</span><span class="sxs-lookup"><span data-stu-id="8b09d-181">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the UI.</span></span>

<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>

### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="8b09d-182">色を使用するだけでなく、色の代替手段を提供する</span><span class="sxs-lookup"><span data-stu-id="8b09d-182">Use Color but Also Provide Alternatives to Color</span></span>

<span data-ttu-id="8b09d-183">色を使用して、他の手段によって示される情報を強化、強調、または再反復処理します。ただし、色単独を使用して情報を伝達しないでください。</span><span class="sxs-lookup"><span data-stu-id="8b09d-183">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="8b09d-184">色覚に障がいがあるユーザーまたは白黒表示のディスプレイを持つユーザーには、色の代替手段が必要です。</span><span class="sxs-lookup"><span data-stu-id="8b09d-184">Users who are color blind or have a monochrome display need alternatives to color.</span></span>

<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>

### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="8b09d-185">デバイスに依存しない呼び出しで標準の入力 API を使用する</span><span class="sxs-lookup"><span data-stu-id="8b09d-185">Use Standard Input APIs with Device-Independent Calls</span></span>

<span data-ttu-id="8b09d-186">デバイスに依存しない呼び出しは、キーボードとマウスの機能が同等であることを保証する一方、支援技術に関する必要な情報を UI に提供します。</span><span class="sxs-lookup"><span data-stu-id="8b09d-186">Device-independent calls ensure keyboard and mouse feature equality, while providing assistive technology with needed information about the UI.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b09d-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b09d-187">See also</span></span>

- <xref:System.Windows.Automation.Peers>
- <span data-ttu-id="8b09d-188">[テーマと UI オートメーション サポート サンプルを使用した NumericUpDown カスタム コントロール](</previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90)>)</span><span class="sxs-lookup"><span data-stu-id="8b09d-188">[NumericUpDown Custom Control with Theme and UI Automation Support Sample](</previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90)>)</span></span>
- [<span data-ttu-id="8b09d-189">キーボード ユーザー インターフェイス設計のガイドライン</span><span class="sxs-lookup"><span data-stu-id="8b09d-189">Guidelines for Keyboard User Interface Design</span></span>](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
