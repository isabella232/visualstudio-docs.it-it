---
title: Opzioni e pagine opzioni | Microsoft Docs
description: Informazioni sul supporto per le pagine di opzioni, che consentono di modificare i valori delle opzioni che determinano lo stato di un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8e861539470579cc10f2dc41859237393b89fdf943b30ec0033cf2f033f862e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359247"
---
# <a name="options-and-options-pages"></a>Opzioni e pagine di opzioni
Se **si fa** clic su Opzioni **dal** menu Strumenti, viene visualizzata la **finestra di** dialogo Opzioni . Le opzioni in questa finestra di dialogo vengono definite collettivamente pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include categorie di opzioni e ogni categoria include pagine di opzioni. Quando si seleziona una pagina, le relative opzioni vengono visualizzate nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un VSPackage.

## <a name="support-for-options-pages"></a>Supporto per le pagine di opzioni
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fornisce il supporto per la creazione di pagine di opzioni e categorie di opzioni. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.

 L'implementazione <xref:Microsoft.VisualStudio.Shell.DialogPage> predefinita di offre le proprietà pubbliche a un utente in una griglia generica di proprietà. È possibile personalizzare questo comportamento eseguendo l'override di vari metodi nella pagina per creare una pagina di opzioni personalizzata con una propria interfaccia utente. Per altre informazioni, vedere [Creazione di una pagina opzioni](../../extensibility/creating-an-options-page.md).

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa , che fornisce la <xref:Microsoft.VisualStudio.Shell.IProfileManager> persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite dei metodi e consentono di rendere persistenti le modifiche alle proprietà in una sezione utente del Registro di sistema se la proprietà può essere <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> convertita in e da una stringa.

## <a name="options-page-registry-path"></a>Percorso del Registro di sistema della pagina Opzioni
 Per impostazione predefinita, il percorso del Registro di sistema delle proprietà gestite da una pagina delle opzioni è determinato dalla combinazione di , la parola DialogPage e il nome del tipo della classe <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> della pagina delle opzioni. Ad esempio, una classe di pagina delle opzioni può essere definita come segue.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 Se è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, le coppie nome proprietà e valore <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> sono sottochiavi di HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Il percorso del Registro di sistema della pagina delle opzioni stessa è determinato dalla combinazione di , la parola ToolsOptionsPages e la categoria e il nome della <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> pagina delle opzioni. Ad esempio, se la pagina Opzioni personalizzate ha la categoria Pagine delle opzioni e è HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la pagina delle opzioni include la chiave del Registro di <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Attributi e layout della pagina Strumenti/Opzioni
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>L'attributo determina il raggruppamento di pagine di opzioni personalizzate in categorie nell'albero di spostamento della **finestra di dialogo** Opzioni. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>L'attributo associa una pagina di opzioni al pacchetto VSPackage che fornisce l'interfaccia . Si consideri il frammento di codice riportato di seguito.

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Viene dichiarato che MyPackage fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nella finestra **di** dialogo Opzioni entrambe le pagine delle opzioni vengono visualizzate rispettivamente nella categoria **Pagine** delle opzioni personalizzate come **Generale** **e** Personalizzato.

## <a name="option-attributes-and-layout"></a>Attributi e layout delle opzioni
 L'interfaccia utente fornita dalla pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzata. Il layout, l'etichettatura e la descrizione delle opzioni in una pagina di opzioni generiche sono determinati dagli attributi seguenti:

- <xref:System.ComponentModel.CategoryAttribute> determina la categoria dell'opzione.

- <xref:System.ComponentModel.DisplayNameAttribute> determina il nome visualizzato dell'opzione.

- <xref:System.ComponentModel.DescriptionAttribute> determina la descrizione dell'opzione.

  > [!NOTE]
  > Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano risorse stringa per la localizzazione e sono definiti [nell'esempio di progetto gestito](/azure/devops/integrate/index).

  Si consideri il frammento di codice riportato di seguito.

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  L'opzione OptionInteger viene visualizzata nella pagina delle opzioni **come Opzione Integer** nella categoria **Opzioni.** Se l'opzione è selezionata, nella casella della descrizione viene visualizzata **la descrizione, l'opzione Numero intero.**

## <a name="accessing-options-pages-from-another-vspackage"></a>Accesso alle pagine delle opzioni da un altro VSPackage
 È possibile accedere a un VSPackage che ospita e gestisce una pagina di opzioni a livello di codice da un altro VSPackage usando il modello di automazione. Nel codice seguente, ad esempio, un vspackage viene registrato come pagina di hosting di un'opzione.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 Il frammento di codice seguente ottiene il valore di OptionInteger da MyOptionPage:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Quando l'attributo registra una pagina di opzioni, la pagina viene registrata nella chiave <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> AutomationProperties se l'argomento `SupportsAutomation` dell'attributo è `true` . Automazione esamina questa voce del Registro di sistema per trovare il pacchetto VSPackage associato e quindi accede alla proprietà tramite la pagina delle opzioni ospitata, in questo caso My Grid Page.

 Il percorso del Registro di sistema della proprietà di automazione è determinato dalla combinazione di , la parola AutomationProperties e la categoria e il nome <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> della pagina delle opzioni. Ad esempio, se la pagina delle opzioni ha la categoria Categoria, il nome della pagina Griglia e , HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la proprietà di automazione ha la chiave del Registro di <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Il nome canonico My Category.My Grid Page è il valore della sottochiave Name di questa chiave.
