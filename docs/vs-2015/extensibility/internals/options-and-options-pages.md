---
title: Opzioni e le pagine di opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 005aeceb328a24c8c90994b6b274dbddc6b874f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783273"
---
# <a name="options-and-options-pages"></a>Opzioni e pagine di opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Facendo clic su **opzioni** nel **Tools** si aprirà il menu il **opzioni** nella finestra di dialogo. Le opzioni nella finestra di dialogo vengono collettivamente le pagine di opzioni. Il controllo struttura ad albero nel riquadro di spostamento include le categorie delle opzioni e ogni categoria include le pagine di opzioni. Quando si seleziona una pagina, le relative opzioni appaiono nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un pacchetto VSPackage.  
  
## <a name="support-for-options-pages"></a>Supporto per le pagine di opzioni  
 Il <xref:Microsoft.VisualStudio.Shell.Package> classe offre supporto per la creazione di pagine di opzioni e le categorie di opzioni. Il <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.  
  
 L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> offre sue proprietà pubbliche per un utente in una griglia delle proprietà generica. È possibile personalizzare questo comportamento eseguendo l'override di metodi diversi nella pagina per creare una pagina di opzioni personalizzate con la propria interfaccia utente (UI). Per altre informazioni, vedere [creazione di una pagina di opzioni](../../extensibility/creating-an-options-page.md).  
  
 Il <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite del <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metodi rendere persistenti le modifiche alle proprietà in una sessione utente del Registro di sistema se la proprietà può essere consentita in e da una stringa.  
  
## <a name="options-page-registry-path"></a>Percorso del Registro di sistema della pagina Opzioni  
 Per impostazione predefinita, il percorso del Registro di sistema di proprietà gestite da una pagina di opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola DialogPage e il nome del tipo della classe della pagina Opzioni. Ad esempio, una classe di pagina di opzioni può essere definita come indicato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, le coppie nome / valore di proprietà sono sottochiavi del HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Il percorso del Registro di sistema della pagina di opzioni stesso è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola, ToolsOptionsPages e le opzioni categoria e il nome di pagina. Ad esempio, se la pagina di opzioni personalizzati dispone della categoria, pagine di opzioni personali e il <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la pagina di opzioni con la chiave del Registro di sistema, hkey_local_machine\software\microsoft\. VisualStudio\8.0Exp\ToolsOptionsPages\My opzione Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Layout e gli attributi della pagina di strumenti/opzioni  
 Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo determina il raggruppamento delle pagine Opzioni personalizzate in categorie nell'albero di navigazione del **opzioni** nella finestra di dialogo. Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo associa una pagina di opzioni con il pacchetto VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Questo codice dichiara che MyPackage fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nel **opzioni** vengono visualizzati di entrambe le pagine di opzioni nella finestra di dialogo nel **pagine di opzioni personali** categoria come **generali** e **personalizzato**rispettivamente.  
  
## <a name="option-attributes-and-layout"></a>Gli attributi di opzione e il Layout  
 L'interfaccia utente (UI) che fornisce la pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzate. Il layout, l'assegnazione di etichette e la descrizione delle opzioni in una pagina generica di opzioni sono determinati dagli attributi seguenti:  
  
- <xref:System.ComponentModel.CategoryAttribute> Determina la categoria dell'opzione.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Determina il nome visualizzato dell'opzione.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Determina la descrizione dell'opzione.  
  
  > [!NOTE]
  >  Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, usare le risorse stringa per la localizzazione e sono definiti nel [esempio di progetto gestito](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Si consideri il frammento di codice riportato di seguito.  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  L'opzione OptionInteger viene visualizzata nella pagina di opzioni come **l'opzione numeri interi** nel **My Options** categoria. Se l'opzione è selezionata, la descrizione **l'opzione integer**, viene visualizzato nella finestra di descrizione.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>L'accesso alle pagine di opzioni da un altro VSPackage  
 Un pacchetto VSPackage che ospita e gestisce una pagina di opzioni è possibile accedere a livello di codice da un altro VSPackage usando il modello di automazione. Nel codice seguente, ad esempio, un pacchetto VSPackage è registrato come una pagina di opzioni di hosting.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Il frammento di codice seguente ottiene il valore di OptionInteger dal MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Quando la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo registra una pagina di opzioni, la pagina viene registrata con il tasto se AutomationProperties il `SupportsAutomation` l'argomento dell'attributo è `true`. Automazione esamina questa voce del Registro di sistema per individuare il pacchetto VSPackage associati e l'automazione quindi accede alla proprietà tramite la pagina di opzioni ospitato, in questo caso, My pagina della griglia.  
  
 Il percorso del Registro di sistema di proprietà di automazione è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola, AutomationProperties e le opzioni categoria e il nome di pagina. Ad esempio, se la pagina di opzioni dispone della categoria di My Category, il nome My pagina della griglia e il <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, quindi la proprietà di automazione con la chiave del Registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\ Pagina della griglia Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
>  Il nome canonico, pagina della griglia Category.My personali, è il valore della sottochiave del nome di questa chiave.

