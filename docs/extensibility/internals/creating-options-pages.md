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
ms.openlocfilehash: d2724a8ce237f238c75e5f63f1621a5ae548f36d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124685"
---
# <a name="create-options-pages"></a>Creare pagine di opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework del pacchetto gestito le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage> estendono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE aggiungendo le pagine **Opzioni** nel menu Strumenti. 

 Un oggetto che implementa una determinata **pagina Tools Option** è associato a vspackage specifici dall'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

 Poiché l'ambiente crea un'istanza dell'oggetto che implementa una **determinata** pagina Opzioni degli strumenti quando tale pagina specifica viene visualizzata dall'IDE:

- Una **pagina Opzioni** degli strumenti deve essere implementata nel proprio oggetto e non nell'oggetto che implementa un VSPackage.

- Un oggetto non può implementare più **pagine Opzioni** degli strumenti.

## <a name="register-as-a-tools-options-page-provider"></a>Eseguire la registrazione come provider di pagine Opzioni degli strumenti
 Un pacchetto VSPackage che  supporta la configurazione utente  tramite le pagine Opzioni degli strumenti indica gli oggetti che forniscono queste pagine Opzioni degli strumenti applicando istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicate <xref:Microsoft.VisualStudio.Shell.Package> all'implementazione.

 Deve essere presente un'istanza <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> di per ogni tipo <xref:Microsoft.VisualStudio.Shell.DialogPage> derivato da che implementa una pagina Opzioni **degli** strumenti.

 Ogni istanza di usa il tipo che implementa la pagina Opzioni degli strumenti, le stringhe che contengono la categoria e la sottocategore usata per identificare una pagina Opzioni degli strumenti e le informazioni sulle risorse per registrare il tipo come pagina Opzioni degli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> strumenti.   

## <a name="persist-tools-options-page-state"></a>Stato della pagina Persist Tools Options
 Se **l'implementazione di una** pagina Opzioni degli strumenti è registrata con il supporto dell'automazione abilitato, l'IDE rende persistente lo stato della pagina insieme a tutte le altre **pagine Opzioni** degli strumenti.

 Un VSPackage può gestire la propria persistenza usando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . È necessario usare solo uno o l'altro metodo di persistenza.

## <a name="implement-dialogpage-class"></a>Implementare la classe DialogPage
 Un oggetto che fornisce l'implementazione di un vspackage di un tipo derivato da <xref:Microsoft.VisualStudio.Shell.DialogPage> può sfruttare le funzionalità ereditate seguenti:

- Finestra dell'interfaccia utente predefinita.

- Meccanismo di persistenza predefinito disponibile se viene applicato alla classe o se la proprietà è impostata su per l'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> applicato alla classe `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .

- Supporto dell'automazione.

  Il requisito minimo per un oggetto che implementa una **pagina Opzioni** degli strumenti tramite <xref:Microsoft.VisualStudio.Shell.DialogPage> è l'aggiunta di proprietà pubbliche.

  Se la classe è  registrata correttamente come provider di pagine  Opzioni degli strumenti, le relative proprietà pubbliche sono disponibili nella sezione Opzioni del **menu** Strumenti sotto forma di griglia delle proprietà.

  Tutte queste funzionalità predefinite possono essere sostituite. Ad esempio, per creare un'interfaccia utente più sofisticata è necessario eseguire solo l'override dell'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Esempio
 Di seguito è illustrata una semplice implementazione "Hello world" di una pagina delle opzioni. Aggiungendo il codice seguente a un progetto predefinito creato dal modello Visual Studio pacchetto con l'opzione Comando di **menu** selezionata verrà illustrata in modo adeguato la funzionalità della pagina delle opzioni.

### <a name="description"></a>Descrizione
 La classe seguente definisce una pagina di opzioni "Hello world" minima. Quando viene aperto, l'utente può impostare la `HelloWorld` proprietà pubblica in una griglia delle proprietà.

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs" id="Snippet11":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb" id="Snippet11":::

### <a name="description"></a>Descrizione
 L'applicazione dell'attributo seguente alla classe del pacchetto rende disponibile la pagina delle opzioni al caricamento del pacchetto. I numeri sono ID risorsa arbitrari per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet07":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet07":::

### <a name="description"></a>Descrizione
 Il gestore eventi seguente visualizza un risultato a seconda del valore del set di proprietà nella pagina delle opzioni. Usa il metodo con il cast esplicito del risultato nel tipo di pagina dell'opzione personalizzata <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per accedere alle proprietà esposte dalla pagina.

 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dalla funzione per associarla al comando `MenuItemCallback` predefinito aggiunto al menu Strumenti. 

### <a name="code"></a>Codice
:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs" id="Snippet08":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb" id="Snippet08":::

## <a name="see-also"></a>Vedi anche
- [Estendere le impostazioni utente e le opzioni](../../extensibility/extending-user-settings-and-options.md)
- [Supporto dell'automazione per le pagine delle opzioni](../../extensibility/internals/automation-support-for-options-pages.md)
