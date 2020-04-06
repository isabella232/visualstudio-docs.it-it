---
title: Pagine delle opzioni e delle opzioni Documenti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706831"
---
# <a name="options-and-options-pages"></a>Opzioni e pagine di opzioni
Facendo clic su **Opzioni** nel menu **Strumenti** si apre la finestra di dialogo **Opzioni.** Le opzioni di questa finestra di dialogo sono collettivamente denominate pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include categorie di opzioni e ogni categoria dispone di pagine di opzioni. Quando si seleziona una pagina, le relative opzioni vengono visualizzate nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un pacchetto VSPackage.

## <a name="support-for-options-pages"></a>Supporto per le pagine delle opzioni
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fornisce supporto per la creazione di pagine di opzioni e categorie di opzioni. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.

 L'implementazione <xref:Microsoft.VisualStudio.Shell.DialogPage> predefinita di offre le proprietà pubbliche a un utente in una griglia generica di proprietà. È possibile personalizzare questo comportamento eseguendo l'override di vari metodi nella pagina per creare una pagina di opzioni personalizzate con la propria interfaccia utente (UI). Per ulteriori informazioni, consultate Creazione di una [pagina Opzioni.](../../extensibility/creating-an-options-page.md)

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe <xref:Microsoft.VisualStudio.Shell.IProfileManager>implementa , che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> dei metodi e mantengono le modifiche delle proprietà in una sezione utente del Registro di sistema se la proprietà può essere convertita in e da una stringa.

## <a name="options-page-registry-path"></a>Posizione del Registro di sistema della pagina Opzioni
 Per impostazione predefinita, il percorso del Registro di <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>sistema delle proprietà gestite da una pagina delle opzioni viene determinato combinando , la parola DialogPage e il nome del tipo della classe della pagina delle opzioni. Ad esempio, una classe di pagina di opzioni potrebbe essere definita come segue.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Se <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> il valore è HKEY_CURRENT_USER Software, Microsoft VisualStudio, 8.0Exp, le coppie nome proprietà e valore sono sottochiavi di HKEY_CURRENT_USER .

 Il percorso del Registro di sistema <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>della pagina delle opzioni stessa viene determinato combinando , la parola , ToolsOptionsPages e la categoria e il nome della pagina di opzioni. Se, ad esempio, nella pagina delle opzioni personalizzate <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è disponibile la categoria Pagine opzioni personali e la categoria è HKEY_LOCAL_MACHINE, SOFTWARE e Microsoft VisualStudio, ovvero 8.0Exp, la pagina delle opzioni include la chiave del Registro di sistema, HKEY_LOCAL_MACHINE SOFTWARE.

## <a name="toolsoptions-page-attributes-and-layout"></a>Attributi e layout della pagina Strumenti/Opzioni
 L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> determina il raggruppamento delle pagine delle opzioni personalizzate in categorie nell'albero di navigazione della finestra di dialogo **Opzioni.** L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associa una pagina di opzioni con il pacchetto VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 In questo modo viene dichiarato che MyPackage fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom.This declares that MyPackage provides two options pages, OptionsPageGeneral and OptionsPageCustom. Nella finestra di dialogo **Opzioni,** entrambe le pagine delle opzioni vengono visualizzate nella categoria **Pagine opzioni personali** rispettivamente Come **Generale** e **Personalizzato.**

## <a name="option-attributes-and-layout"></a>Attributi e layout delle opzioni
 L'interfaccia utente (UI) fornita dalla pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzate. Il layout, l'etichettatura e la descrizione delle opzioni in una pagina di opzioni generiche sono determinati dai seguenti attributi:

- <xref:System.ComponentModel.CategoryAttribute>determina la categoria dell'opzione.

- <xref:System.ComponentModel.DisplayNameAttribute>determina il nome visualizzato dell'opzione.

- <xref:System.ComponentModel.DescriptionAttribute>determina la descrizione dell'opzione.

  > [!NOTE]
  > Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzano risorse stringa per la localizzazione e sono definiti nell'esempio di [progetto gestito](/azure/devops/integrate/index).

  Si consideri il frammento di codice riportato di seguito.

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  L'opzione OptionInteger viene visualizzata nella pagina delle opzioni come **Opzione intera** nella categoria **Opzioni personali.** Se l'opzione è selezionata, nella casella Descrizione viene visualizzata la descrizione **Opzione Numero intero**personale.

## <a name="accessing-options-pages-from-another-vspackage"></a>Accesso alle pagine di opzioni da un altro VSPackageAccessing Options Pages from Another VSPackage
 Un pacchetto VSPackage che ospita e gestisce una pagina di opzioni è possibile accedere a livello di codice da un altro VSPackage utilizzando il modello di automazione. Ad esempio, nel codice seguente un VSPackage viene registrato come hosting di una pagina di opzioni.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 The following code fragment gets the value of OptionInteger from MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Quando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> l'attributo registra una pagina di opzioni, la `SupportsAutomation` pagina viene registrata `true`nella chiave AutomationProperties se l'argomento dell'attributo è . Automazione esamina questa voce del Registro di sistema per trovare il VSPackage associato e l'automazione quindi accede alla proprietà tramite la pagina di opzioni ospitate, in questo caso, My Grid Page.

 Il percorso del Registro di <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>sistema della proprietà di automazione viene determinato combinando , la parola, AutomationProperties, e la categoria e il nome della pagina di opzioni. Se, ad esempio, la pagina delle opzioni dispone della categoria <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>Categoria personale, del nome della pagina Griglia personale e della HKEY_LOCAL_MACHINE SOFTWARE, ovvero HKEY_LOCAL_MACHINE SOFTWARE, microsoft VisualStudio, 8.0Exp, la proprietà di automazione dispone della chiave del Registro di sistema, HKEY_LOCAL_MACHINE SOFTWARE.

> [!NOTE]
> Il nome canonico, My Category.My Grid Page, è il valore della sottochiave Name di questa chiave.
