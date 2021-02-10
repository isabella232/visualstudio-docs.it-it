---
title: Pagine opzioni e opzioni | Microsoft Docs
description: Informazioni sul supporto per le pagine opzioni che consentono di modificare i valori delle opzioni che determinano lo stato di un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dac6c6898a8a8766d073cb5cd2f3bd330e7e2658
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954576"
---
# <a name="options-and-options-pages"></a>Opzioni e pagine di opzioni
Fare clic su **Opzioni** nel menu **strumenti** per aprire la finestra di dialogo **Opzioni** . Le opzioni di questa finestra di dialogo sono collettivamente denominate pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include le categorie di opzioni e ogni categoria dispone di pagine opzioni. Quando si seleziona una pagina, le relative opzioni vengono visualizzate nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un pacchetto VSPackage.

## <a name="support-for-options-pages"></a>Supporto per le pagine opzioni
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fornisce supporto per la creazione di pagine di opzioni e categorie di opzioni. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.

 L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> offre le proprietà pubbliche a un utente in una griglia generica di proprietà. È possibile personalizzare questo comportamento eseguendo l'override di diversi metodi della pagina per creare una pagina di opzioni personalizzate con una propria interfaccia utente (UI). Per ulteriori informazioni, vedere [la pagina relativa alla creazione di una pagina di opzioni](../../extensibility/creating-an-options-page.md).

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> , che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite dei metodi e mantengono le <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> modifiche delle proprietà in una sezione utente del registro di sistema se la proprietà può essere convertita in e da una stringa.

## <a name="options-page-registry-path"></a>Percorso del registro di sistema della pagina Opzioni
 Per impostazione predefinita, il percorso del registro di sistema delle proprietà gestite da una pagina di opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , la parola DialogPage e il nome del tipo della classe di pagina Opzioni. È ad esempio possibile definire una classe di pagine di opzioni come indicato di seguito.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Se <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, le coppie nome e valore della proprietà sono sottochiavi di HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Il percorso del registro di sistema della pagina Opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , la parola, ToolsOptionsPages e la categoria e il nome della pagina Opzioni. Ad esempio, se la pagina Opzioni personalizzate contiene la categoria, le pagine opzioni personali e il <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la pagina opzioni avrà la chiave del registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Layout e attributi della pagina strumenti/opzioni
 L' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo determina il raggruppamento di pagine di opzioni personalizzate in categorie nell'albero di navigazione della finestra di dialogo **Opzioni** . L' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo associa una pagina di opzioni al pacchetto VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Questo dichiara che il pacchetto fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nella finestra di dialogo **Opzioni** , entrambe le pagine opzioni vengono visualizzate nella categoria **pagine opzioni personali** rispettivamente come **generale** e **personalizzato**.

## <a name="option-attributes-and-layout"></a>Attributi e layout delle opzioni
 L'interfaccia utente (UI) fornita dalla pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzata. Il layout, l'assegnazione di etichette e la descrizione delle opzioni in una pagina di opzioni generiche sono determinati dagli attributi seguenti:

- <xref:System.ComponentModel.CategoryAttribute> determina la categoria dell'opzione.

- <xref:System.ComponentModel.DisplayNameAttribute> determina il nome visualizzato dell'opzione.

- <xref:System.ComponentModel.DescriptionAttribute> determina la descrizione dell'opzione.

  > [!NOTE]
  > Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse di stringa per la localizzazione e sono definiti nell' [esempio di progetto gestito](/azure/devops/integrate/index).

  Si consideri il frammento di codice riportato di seguito.

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  L'opzione OptionInteger viene visualizzata nella pagina opzioni come **opzione Integer** nella categoria **Opzioni personali** . Se l'opzione è selezionata, l'opzione descrizione, **valore intero** viene visualizzata nella casella Descrizione.

## <a name="accessing-options-pages-from-another-vspackage"></a>Accesso alle pagine di opzioni da un altro pacchetto VSPackage
 È possibile accedere a livello di codice a un VSPackage che ospita e gestisce una pagina di opzioni da un altro pacchetto VSPackage usando il modello di automazione. Nel codice seguente, ad esempio, un pacchetto VSPackage viene registrato come hosting di una pagina di opzioni.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Il seguente frammento di codice ottiene il valore di OptionInteger da MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Quando l' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo registra una pagina di opzioni, la pagina viene registrata sotto la chiave AutomationProperties se l' `SupportsAutomation` argomento dell'attributo è `true` . Automazione esamina questa voce del registro di sistema per trovare il pacchetto VSPackage associato e l'automazione accede quindi alla proprietà tramite la pagina Opzioni ospitate, in questo caso la pagina della griglia.

 Il percorso del registro di sistema della proprietà di automazione viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , la parola, AutomationProperties e la categoria e il nome della pagina di opzioni. Se, ad esempio, nella pagina Opzioni è presente la categoria categoria, il nome della pagina della griglia e il <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la proprietà di automazione avrà la chiave del registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Il nome canonico, pagina della griglia Category.My, è il valore della sottochiave Name della chiave.
