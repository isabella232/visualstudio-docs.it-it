---
title: Creazione di pagine di opzioni | Microsoft Docs
description: Informazioni su come creare una pagina Opzioni nel menu Strumenti in Visual Studio implementando una classe DialogPage dal framework del pacchetto gestito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3f236d38a4bde8a13bb49e6cbc8700811fac9d846962ace7c47ef2ede4047919
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448221"
---
# <a name="create-options-pages"></a>Creare pagine di opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework del pacchetto gestito le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage> estendono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE aggiungendo pagine **Opzioni** nel menu Strumenti. 

 Un oggetto che implementa una determinata **pagina Di** opzioni degli strumenti è associato a pacchetti VSPackage specifici dall'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

 Poiché l'ambiente crea un'istanza dell'oggetto che implementa una **particolare** pagina Opzioni degli strumenti quando tale pagina viene visualizzata dall'IDE:

- Una **pagina Tools Option** (Opzioni strumenti) deve essere implementata nel proprio oggetto e non nell'oggetto che implementa un VSPackage.

- Un oggetto non può implementare più **pagine Opzioni degli** strumenti.

## <a name="register-as-a-tools-options-page-provider"></a>Registra come provider di pagine Opzioni degli strumenti
 Un PACCHETTO VSPackage che  supporta la configurazione utente  tramite le pagine Opzioni degli strumenti indica gli oggetti che forniscono queste pagine Opzioni degli strumenti applicando istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicate <xref:Microsoft.VisualStudio.Shell.Package> all'implementazione.

 Deve essere presente un'istanza <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> di per ogni tipo <xref:Microsoft.VisualStudio.Shell.DialogPage> derivato da che implementa una pagina Opzioni **degli** strumenti.

 Ogni istanza di usa il tipo che implementa la pagina Opzioni degli strumenti , le stringhe contenenti la categoria e la sottocategoma usate per identificare una pagina Opzioni strumenti e le informazioni sulle risorse per registrare il tipo come pagina Opzioni strumenti <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .   

## <a name="persist-tools-options-page-state"></a>Rendere persistente lo stato della pagina Opzioni strumenti
 Se **l'implementazione di una** pagina Opzioni degli strumenti è registrata con il supporto dell'automazione abilitato, l'IDE rende persistente lo stato della pagina insieme a tutte le **altre pagine Opzioni degli** strumenti.

 Un VSPackage può gestire la propria persistenza usando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . È necessario usare solo uno o l'altro metodo di persistenza.

## <a name="implement-dialogpage-class"></a>Implementare la classe DialogPage
 Un oggetto che fornisce l'implementazione di un vspackage di un tipo derivato da può <xref:Microsoft.VisualStudio.Shell.DialogPage> sfruttare le funzionalità ereditate seguenti:

- Finestra dell'interfaccia utente predefinita.

- Meccanismo di persistenza predefinito disponibile se viene applicato alla classe o se la proprietà è impostata su per l'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> applicato alla classe `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

- Supporto dell'automazione.

  Il requisito minimo per un oggetto che implementa una **pagina Opzioni** degli strumenti tramite <xref:Microsoft.VisualStudio.Shell.DialogPage> è l'aggiunta di proprietà pubbliche.

  Se la classe è  registrata correttamente come provider di pagine  Opzioni degli strumenti, le relative proprietà pubbliche sono disponibili nella sezione Opzioni del **menu** Strumenti sotto forma di griglia delle proprietà.

  È possibile eseguire l'override di tutte queste funzionalità predefinite. Ad esempio, per creare un'interfaccia utente più sofisticata, è necessario eseguire solo l'override dell'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Esempio
 Di seguito è illustrata una semplice implementazione "Hello world" di una pagina di opzioni. L'aggiunta del codice seguente a un progetto predefinito creato dal modello di pacchetto Visual Studio con l'opzione **Comando** di menu selezionata illustra adeguatamente la funzionalità della pagina delle opzioni.

### <a name="description"></a>Descrizione
 La classe seguente definisce una pagina di opzioni "Hello world" minima. Quando viene aperto, l'utente può impostare la proprietà `HelloWorld` pubblica in una griglia delle proprietà.

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs" id="Snippet11":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb" id="Snippet11":::

### <a name="description"></a>Descrizione
 L'applicazione dell'attributo seguente alla classe del pacchetto rende disponibile la pagina delle opzioni quando il pacchetto viene caricato. I numeri sono ID risorsa arbitrari per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet07":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet07":::

### <a name="description"></a>Descrizione
 Il gestore eventi seguente visualizza un risultato a seconda del valore della proprietà impostata nella pagina delle opzioni. Usa il metodo con il cast esplicito del risultato nel tipo di pagina dell'opzione personalizzata <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per accedere alle proprietà esposte dalla pagina.

 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dalla funzione per collegarla al comando `MenuItemCallback` predefinito aggiunto al menu Strumenti. 

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet08":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet08":::

## <a name="see-also"></a>Vedi anche
- [Estendere le impostazioni utente e le opzioni](../../extensibility/extending-user-settings-and-options.md)
- [Supporto dell'automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)
