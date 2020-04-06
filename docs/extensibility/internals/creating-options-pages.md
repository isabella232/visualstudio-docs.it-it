---
title: Creazione di pagine di opzioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709155"
---
# <a name="create-options-pages"></a>Creare pagine di opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework del pacchetto gestito, le classi derivate dall'estensione <xref:Microsoft.VisualStudio.Shell.DialogPage> dell'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aggiungendo le pagine **Opzioni** nel menu **Strumenti.**

 Un oggetto che implementa una determinata pagina **dell'opzione degli** strumenti è associato a VSPackage specifici dall'oggetto. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>

 Poiché l'ambiente crea un'istanza dell'oggetto che implementa una determinata pagina **Opzioni degli strumenti** quando la pagina specifica viene visualizzata dall'IDE:Because the environment instantiates the object implementing a particular Tools Options page when that particular page is displayed by the IDE:

- Una pagina **di opzione degli strumenti** deve essere implementata sul proprio oggetto e non sull'oggetto che implementa un pacchetto VSPackage.A Tools Option page should be implemented on its own object, and not on the object implementing a VSPackage.

- Un oggetto non può implementare più pagine **Opzioni degli** strumenti.

## <a name="register-as-a-tools-options-page-provider"></a>Registrarsi come provider di pagine Opzioni degli strumenti
 Un VSPackage che supporta la configurazione utente tramite le pagine **Opzioni degli** strumenti <xref:Microsoft.VisualStudio.Shell.Package> indica gli oggetti che forniscono queste pagine opzioni **degli** strumenti applicando istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicate all'implementazione.

 Deve essere presente <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> un'istanza di per ogni <xref:Microsoft.VisualStudio.Shell.DialogPage>tipo derivato che implementa una pagina Opzioni degli **strumenti.**

 Ogni istanza <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> di utilizza il tipo che implementa la pagina **Opzioni degli** strumenti, le stringhe che contengono la categoria e la sottocategoria utilizzate per identificare una pagina **Opzioni degli** strumenti e le informazioni sulle risorse per registrare il tipo come se forniscano una pagina Opzioni **degli strumenti.**

## <a name="persist-tools-options-page-state"></a>Rendere persistenti lo stato della pagina Opzioni degli strumentiPersist Tools Options page state
 Se un **Tools Options** implementazione della pagina è registrata con il supporto di automazione abilitato, l'IDE mantiene lo stato della pagina insieme a tutte le altre opzioni degli **strumenti pagine.**

 Un pacchetto VSPackage può gestire <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>la propria persistenza utilizzando . È necessario utilizzare solo uno o l'altro metodo di persistenza.

## <a name="implement-dialogpage-class"></a>Implementare la classe DialogPageImplement DialogPage class
 Un oggetto che fornisce l'implementazione di un VSPackage di un <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivato tipo può sfruttare le seguenti funzionalità ereditate:An object providing a VSPackage's implementation of a -derived type can take advantage of the following inherited features:

- Una finestra predefinita dell'interfaccia utente.

- Meccanismo di persistenza <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> predefinito disponibile se viene <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> applicato alla `true` classe <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> o se la proprietà è impostata su per l'oggetto applicato alla classe .

- Supporto per l'automazione.

  Il requisito minimo per un oggetto <xref:Microsoft.VisualStudio.Shell.DialogPage> che implementa una pagina Opzioni **degli** strumenti utilizzando l'aggiunta di proprietà pubbliche.

  Se la classe è registrata correttamente come provider di pagine **Opzioni degli** strumenti, le relative proprietà pubbliche sono disponibili nella sezione **Opzioni** del menu **Strumenti** sotto forma di griglia delle proprietà.

  Tutte queste funzionalità predefinite possono essere sostituite. Ad esempio, per creare un'interfaccia utente più sofisticata è necessario solo eseguire l'override dell'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.

## <a name="example"></a>Esempio
 Quello che segue è una semplice implementazione "Hello world" di una pagina di opzioni. L'aggiunta del codice seguente a un progetto predefinito creato dal modello di pacchetto di Visual Studio con l'opzione **Comando** di menu selezionata dimostrerà in modo adeguato la funzionalità della pagina delle opzioni.

### <a name="description"></a>Descrizione
 La classe seguente definisce una pagina minima delle opzioni "Hello world". Quando viene aperto, l'utente può impostare la proprietà pubblica `HelloWorld` in una griglia delle proprietà.

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Descrizione
 L'applicazione dell'attributo seguente alla classe del pacchetto rende disponibile la pagina delle opzioni al caricamento del pacchetto. I numeri sono ID di risorsa arbitrari per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Descrizione
 Il gestore eventi seguente visualizza un risultato in base al valore del set di proprietà nella pagina delle opzioni. Viene utilizzato <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> il metodo con il risultato in modo esplicito cast nel tipo di pagina dell'opzione personalizzata per accedere alle proprietà esposte dalla pagina.

 Nel caso di un progetto generato dal modello di `MenuItemCallback` pacchetto, chiamare questa funzione dalla funzione per associarla al comando predefinito aggiunto al menu **Strumenti.**

### <a name="code"></a>Codice
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Vedere anche
- [Estendere le impostazioni e le opzioni utente](../../extensibility/extending-user-settings-and-options.md)
- [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)
