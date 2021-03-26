---
title: Creazione di pagine di opzioni | Microsoft Docs
description: Informazioni su come creare una pagina di opzioni nel menu strumenti di Visual Studio implementando una classe DialogPage dal framework di pacchetto gestito.
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
ms.workload:
- vssdk
ms.openlocfilehash: 2e7513617ab4ee4a051dd48cd110ecb2c5e22495
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056836"
---
# <a name="create-options-pages"></a>Crea pagine opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Framework di pacchetto gestito, le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage> estendono l'IDE aggiungendo le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pagine **Opzioni** nel menu **strumenti** .

 Un oggetto che implementa una pagina delle **Opzioni degli strumenti** specificata è associato a VSPackage specifici dall' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> oggetto.

 Poiché l'ambiente crea un'istanza dell'oggetto che implementa una particolare pagina di **Opzioni degli strumenti** quando tale pagina viene visualizzata dall'IDE:

- Una pagina di **Opzioni degli strumenti** deve essere implementata nel relativo oggetto e non nell'oggetto che implementa un pacchetto VSPackage.

- Un oggetto non può implementare più pagine **Opzioni di strumenti** .

## <a name="register-as-a-tools-options-page-provider"></a>Registra come provider di pagine Opzioni strumenti
 Un pacchetto VSPackage che supporta la configurazione utente tramite le pagine **Opzioni degli strumenti** indica gli oggetti che forniscono queste pagine di **Opzioni degli strumenti** applicando le istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicate all' <xref:Microsoft.VisualStudio.Shell.Package> implementazione.

 Deve essere presente un'istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> per ogni <xref:Microsoft.VisualStudio.Shell.DialogPage> tipo derivato da che implementa una pagina di **Opzioni degli strumenti** .

 In ogni istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> viene utilizzato il tipo che implementa la pagina **Opzioni strumenti** , le stringhe che contengono la categoria e la sottocategoria utilizzata per identificare una pagina di **Opzioni degli strumenti** e le informazioni sulle risorse per registrare il tipo come offerta una pagina di **Opzioni degli strumenti** .

## <a name="persist-tools-options-page-state"></a>Stato della pagina Opzioni degli strumenti di salvataggio permanente
 Se un'implementazione della pagina **Opzioni degli strumenti** è registrata con il supporto di automazione abilitato, l'IDE rende permanente lo stato della pagina insieme a tutte le altre pagine **Opzioni di strumenti** .

 Un pacchetto VSPackage può gestire la propria persistenza tramite <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . È necessario usare solo uno o l'altro metodo di persistenza.

## <a name="implement-dialogpage-class"></a>Implementare la classe DialogPage
 Un oggetto che fornisce un'implementazione di VSPackage di un <xref:Microsoft.VisualStudio.Shell.DialogPage> tipo derivato da può sfruttare le funzionalità ereditate seguenti:

- Finestra predefinita dell'interfaccia utente.

- Meccanismo di persistenza predefinito disponibile se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> viene applicato alla classe o se la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> proprietà è impostata su `true` per l'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicato alla classe.

- Supporto per l'automazione.

  Il requisito minimo per un oggetto che implementa una pagina di **Opzioni degli strumenti** tramite <xref:Microsoft.VisualStudio.Shell.DialogPage> è l'aggiunta di proprietà pubbliche.

  Se la classe è stata registrata correttamente come provider di pagine **Opzioni strumenti** , le relative proprietà pubbliche saranno disponibili nella sezione **Opzioni** del menu **strumenti** sotto forma di griglia delle proprietà.

  È possibile eseguire l'override di tutte queste funzionalità predefinite. Ad esempio, per creare un'interfaccia utente più sofisticata è necessario eseguire l'override dell'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Esempio
 Di seguito è riportata una semplice implementazione "Hello World" di una pagina di opzioni. Aggiungendo il codice seguente a un progetto predefinito creato dal modello di pacchetto di Visual Studio con l'opzione del **comando di menu** selezionata, viene illustrata in modo adeguato la funzionalità della pagina di opzioni.

### <a name="description"></a>Descrizione
 La classe seguente definisce una pagina di opzioni "Hello World" minima. Quando viene aperto, l'utente può impostare la `HelloWorld` proprietà Public in una griglia delle proprietà.

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Descrizione
 L'applicazione dell'attributo seguente alla classe del pacchetto rende disponibile la pagina opzioni quando il pacchetto viene caricato. I numeri sono ID di risorsa arbitrari per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Descrizione
 Il gestore eventi seguente visualizza un risultato a seconda del valore della proprietà impostata nella pagina Opzioni. Usa il <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metodo con il risultato eseguito il cast in modo esplicito nel tipo di pagina delle opzioni personalizzate per accedere alle proprietà esposte dalla pagina.

 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dalla `MenuItemCallback` funzione per collegarla al comando predefinito aggiunto al menu **strumenti** .

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Vedi anche
- [Estendi impostazioni utente e opzioni](../../extensibility/extending-user-settings-and-options.md)
- [Supporto di automazione per le pagine opzioni](../../extensibility/internals/automation-support-for-options-pages.md)
