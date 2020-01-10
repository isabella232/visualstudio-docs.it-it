---
title: Pagine opzioni e opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4512867f636e2362aa28d52c5af28bf8eb9697f9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851155"
---
# <a name="options-and-options-pages"></a>Opzioni e pagine di opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fare clic su **Opzioni** nel menu **strumenti** per aprire la finestra di dialogo **Opzioni** . Le opzioni di questa finestra di dialogo sono collettivamente denominate pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include le categorie di opzioni e ogni categoria dispone di pagine opzioni. Quando si seleziona una pagina, le relative opzioni vengono visualizzate nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un pacchetto VSPackage.  
  
## <a name="support-for-options-pages"></a>Supporto per le pagine opzioni  
 La classe <xref:Microsoft.VisualStudio.Shell.Package> fornisce supporto per la creazione di pagine di opzioni e categorie di opzioni. La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa una pagina di opzioni.  
  
 L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> offre le proprietà pubbliche a un utente in una griglia generica di proprietà. È possibile personalizzare questo comportamento eseguendo l'override di diversi metodi della pagina per creare una pagina di opzioni personalizzate con una propria interfaccia utente (UI). Per ulteriori informazioni, vedere [la pagina relativa alla creazione di una pagina di opzioni](../../extensibility/creating-an-options-page.md).  
  
 La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite dei metodi <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> mantengono le modifiche delle proprietà in una sezione utente del registro di sistema se la proprietà può essere convertita in e da una stringa.  
  
## <a name="options-page-registry-path"></a>Percorso del registro di sistema della pagina Opzioni  
 Per impostazione predefinita, il percorso del registro di sistema delle proprietà gestite da una pagina di opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola DialogPage e il nome del tipo della classe di pagina Opzioni. È ad esempio possibile definire una classe di pagine di opzioni come indicato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Se la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> è HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, le coppie nome e valore della proprietà sono sottochiavi di HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.  
  
 Il percorso del registro di sistema della pagina Opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola, ToolsOptionsPages e la categoria e il nome della pagina di opzioni. Ad esempio, se la pagina Opzioni personalizzate include la categoria, le pagine delle opzioni personali e la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, la pagina opzioni avrà la chiave del registro di sistema HKEY_LOCAL_MACHINE opzione \SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Layout e attributi della pagina strumenti/opzioni  
 L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> determina il raggruppamento di pagine di opzioni personalizzate in categorie nell'albero di navigazione della finestra di dialogo **Opzioni** . L'attributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associa una pagina di opzioni al pacchetto VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Questo dichiara che il pacchetto fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nella finestra di dialogo **Opzioni** , entrambe le pagine opzioni vengono visualizzate nella categoria **pagine opzioni personali** rispettivamente come **generale** e **personalizzato**.  
  
## <a name="option-attributes-and-layout"></a>Attributi e layout delle opzioni  
 L'interfaccia utente (UI) fornita dalla pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzata. Il layout, l'assegnazione di etichette e la descrizione delle opzioni in una pagina di opzioni generiche sono determinati dagli attributi seguenti:  
  
- <xref:System.ComponentModel.CategoryAttribute> determina la categoria dell'opzione.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> determina il nome visualizzato dell'opzione.  
  
- <xref:System.ComponentModel.DescriptionAttribute> determina la descrizione dell'opzione.  
  
  > [!NOTE]
  > Gli attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usano le risorse di stringa per la localizzazione e sono definiti nell' [esempio di progetto gestito](https://msdn.com/vsx).  
  
  Si consideri il frammento di codice riportato di seguito.  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  L'opzione OptionInteger viene visualizzata nella pagina opzioni come **opzione Integer** nella categoria **Opzioni personali** . Se l'opzione è selezionata, l'opzione descrizione, **valore intero**viene visualizzata nella casella Descrizione.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Accesso alle pagine di opzioni da un altro pacchetto VSPackage  
 È possibile accedere a livello di codice a un VSPackage che ospita e gestisce una pagina di opzioni da un altro pacchetto VSPackage usando il modello di automazione. Nel codice seguente, ad esempio, un pacchetto VSPackage viene registrato come hosting di una pagina di opzioni.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Il seguente frammento di codice ottiene il valore di OptionInteger da MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Quando l'attributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> registra una pagina di opzioni, la pagina viene registrata sotto la chiave AutomationProperties se l'argomento `SupportsAutomation` dell'attributo è `true`. Automazione esamina questa voce del registro di sistema per trovare il pacchetto VSPackage associato e l'automazione accede quindi alla proprietà tramite la pagina Opzioni ospitate, in questo caso la pagina della griglia.  
  
 Il percorso del registro di sistema della proprietà di automazione è determinato dalla combinazione di <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, parola, AutomationProperties e nome e categoria della pagina Opzioni. Se, ad esempio, nella pagina Opzioni è presente la categoria categoria, il nome della pagina della griglia e la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, la proprietà automazione avrà la chiave del registro di sistema HKEY_LOCAL_MACHINE pagina della griglia \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My.  
  
> [!NOTE]
> Il nome canonico, pagina della griglia Category.My, è il valore della sottochiave Name della chiave.
