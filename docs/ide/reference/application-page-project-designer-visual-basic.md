---
title: Pagina Applicazione delle proprietà del progetto VB
description: Informazioni su come usare la pagina Applicazione di progettazione Visual Basic Project per specificare le impostazioni e le proprietà dell'applicazione del progetto.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 245bb2642a73e1b995841dd06a821a7e9b127020
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094282"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)

Usare la pagina **Applicazione** di Creazione progetti per specificare le impostazioni e le proprietà dell'applicazione del progetto.

Per accedere alla pagina **Applicazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Scegliere quindi **Project**  >  **proprietà** nella barra dei menu. Quando si apre **Creazione progetti**, selezionare la scheda **Applicazione**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Impostazioni generali dell'applicazione

Le opzioni seguenti consentono di configurare le impostazioni generali per un'applicazione.

### <a name="assembly-name"></a>Nome assembly

Specifica il nome del file di output che conterrà il manifesto dell'assembly. Se si modifica questa proprietà, viene modificata anche la proprietà **Nome output**.

È anche possibile specificare il nome del file di output da un prompt dei comandi usando l'opzione del compilatore [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out).

Per informazioni su come accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Spazio dei nomi radice

Specifica lo spazio dei nomi di base per tutti i file nel progetto. Ad esempio, se si imposta lo **Spazio dei nomi radice** su `Project1` e nel codice è presente una `Class1` all'esterno di qualsiasi spazio dei nomi, lo spazio dei nomi di questa sarà `Project1.Class1`. Se nel codice una `Class2` fosse presente in uno spazio dei nomi `Order`, lo spazio dei nomi sarebbe `Project1.Order.Class2`.

Se si deseleziona **Spazio dei nomi radice**, è possibile specificare nel codice la struttura dello spazio dei nomi del progetto.

> [!NOTE]
> Se si usa la parola chiave `Global` in un'[istruzione Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), è possibile definire uno spazio dei nomi esterno allo spazio dei nomi radice del progetto. Se si deseleziona spazio dei **nomi radice**, diventa lo spazio dei nomi di primo livello, che elimina la necessità della parola chiave `Global` in `Global` `Namespace` un'istruzione . Per altre informazioni, vedere "Global Keyword in Namespace Statements" (Parola chiave Global nelle istruzioni Namespace) in [Namespaces in Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces) (Spazi dei nomi in Visual Basic).

Per informazioni su come creare spazi dei nomi nel codice, vedere [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement) (Istruzione Namespace).

Per altre informazioni sulla proprietà rootnamespace, vedere [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Per informazioni su come accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Framework di destinazione (tutte le configurazioni)

Specifica la versione di .NET a cui è destinata l'applicazione. Questa opzione può avere valori diversi a seconda delle versioni di .NET installate nel computer in uso.

Per i progetti .NET Framework, il valore predefinito corrisponde al framework di destinazione specificato al momento della creazione del progetto.

> [!NOTE]
> I pacchetti prerequisiti elencati nella [finestra di dialogo Prerequisiti](../../ide/reference/prerequisites-dialog-box.md) vengono installati automaticamente alla prima apertura della finestra di dialogo. In caso di modifiche successive al framework di destinazione del progetto, sarà necessario specificare manualmente i prerequisiti in modo che vi sia corrispondenza.

Per altre informazioni, vedere [Panoramica sull'impostazione dei framework di destinazione](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Tipo di applicazione

Specifica il tipo di applicazione da compilare. I valori sono diversi a seconda del tipo di progetto. Ad esempio, per un progetto **App Windows Forms** è possibile specificare **Applicazione Windows Form**, **Libreria di classi**, **Applicazione console**, **Servizio Windows** o **Libreria di controlli Web**.

Per il progetto di un'applicazione Web è necessario specificare **Libreria di classi**.

Per altre informazioni sulla proprietà **Tipo di applicazione**, vedere [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Per informazioni su come accedere a tale proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Genera automaticamente reindirizzamenti di binding

I reindirizzamenti di binding vengono aggiunti al progetto se l'app o i relativi componenti fanno riferimento a più di una versione dello stesso assembly. Se si vuole definire manualmente i reindirizzamenti di binding nel file di progetto, deselezionare **Genera automaticamente reindirizzamenti di binding**.

Per altre informazioni sul reindirizzamento, vedere [Reindirizzamento delle versioni di assembly](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Form di avvio/oggetto di avvio/URI di avvio

Consente di specificare il modulo di avvio o il punto di ingresso dell'applicazione.

Se l'opzione **Abilita framework applicazione** è selezionata (impostazione predefinita), questo elenco ha come intestazione **Modulo di avvio** e mostra solo moduli, poiché il framework applicazione supporta solo moduli di avvio, non oggetti.

Se il progetto è un'applicazione browser WPF, questo elenco ha come intestazione **URI di avvio** e il valore predefinito è **Page1.xaml**. L'elenco **URI di avvio** consente di specificare la risorsa interfaccia utente (un elemento XAML) che l'applicazione visualizza all'avvio dell'applicazione. Per altre informazioni, vedere <xref:System.Windows.Application.StartupUri%2A>.

Se l'opzione **Abilita framework applicazione** è deselezionata, questo elenco diventa **Oggetto di avvio** e mostra sia moduli e classi o moduli con `Sub Main`.

**Oggetto di avvio** definisce il punto di ingresso da chiamare durante il caricamento dell'applicazione. In genere è impostato sul modulo principale dell'applicazione o sulla procedura `Sub Main` da eseguire all'avvio dell'applicazione. Poiché le librerie di classi non hanno un punto di ingresso, l'unica opzione disponibile per questa proprietà è **(Nessuno)**. Per altre informazioni, vedere [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Icona

Consente di impostare il file con estensione ico che si vuole usare come icona di programma. Selezionare **\<Browse...>** questa opzione per cercare un elemento grafico esistente. Per altre informazioni, vedere [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) o [/win32icon (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) (/win32icon (opzioni del compilatore C#)). Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Informazioni assembly

Fare clic su questo pulsante per visualizzare la [finestra di dialogo Informazioni assembly](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Abilita framework applicazione

Consente di specifica se un progetto deve usare il framework dell'applicazione. L'impostazione di questa opzione influisce sulle opzioni disponibili in **Oggetto di avvio modulo** di / **avvio**.

Se questa casella di controllo è selezionata, l'applicazione usa la procedura `Sub Main` standard. Se si seleziona questa casella di controllo, vengono abilitate le funzionalità della sezione **Proprietà framework applicazione Windows** ed è anche necessario selezionare un modulo di avvio.

Se questa casella di controllo è deselezionata, l'applicazione userà la procedura `Sub Main` personalizzata specificata in **Modulo di avvio**. In questo caso è possibile specificare un oggetto di avvio (una procedura `Sub Main` personalizzata in un metodo o in una classe) o un modulo. Le opzioni della sezione **Proprietà framework applicazione Windows**, poi, non sono più disponibili.

### <a name="view-windows-settings"></a>Visualizza impostazioni di Windows

Fare clic su questo pulsante per generare e aprire il file *app.manifest.* Visual Studio usa questo file per generare i dati del manifesto per l'applicazione. Impostare quindi il livello di esecuzione richiesto di Controllo dell'account utente modificando il `<requestedExecutionLevel>` tag in *app.manifest* come indicato di seguito:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce funziona con un livello di `asInvoker` o in modalità virtualizzata (senza generazione del manifesto). Per specificare la modalità virtualizzata, rimuovere l'intero tag da app.manifest.

Per altre informazioni sulla generazione del manifesto, vedere [ClickOnce Deployment on Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md) (Distribuzione ClickOnce in Windows Vista).

## <a name="windows-application-framework-properties"></a>Proprietà framework applicazione Windows

Le impostazioni seguenti sono disponibili nella sezione **Proprietà framework applicazione Windows**. Queste opzioni sono disponibili solo se la casella di controllo **Abilita framework applicazione** è selezionata.

> [!TIP]
> Nella sezione successiva sono descritte le impostazioni **Proprietà framework applicazione Windows** specifiche per le app WPF (Windows Presentation Foundation).

### <a name="enable-xp-visual-styles"></a>Attiva stili di visualizzazione XP

Consente di abilitare o disabilitare gli stili di visualizzazione di Windows XP, noti anche come *temi di Windows XP*. Gli stili di visualizzazione di Windows XP consentono, ad esempio, i controlli con angoli arrotondati e colori dinamici. Il valore predefinito è Attivato.

### <a name="make-single-instance-application"></a>Rendi a istanza singola

Selezionare questa casella di controllo per impedire agli utenti di eseguire più istanze dell'applicazione. L'impostazione predefinita per questa casella di controllo è *deselezionata*, per consentire l'esecuzione di più istanze dell'applicazione. Per altre informazioni, vedere l'evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

### <a name="save-mysettings-on-shutdown"></a>Salva My.Settings alla chiusura

Selezionare questa casella di controllo per specificare che le impostazioni `My.Settings` dell'applicazione devono essere salvate quando l'utente arresta il computer. Per impostazione predefinita questa opzione è abilitata. Se questa opzione è disabilitata, è possibile salvare manualmente le impostazioni dell'applicazione chiamando `My.Settings.Save`.

### <a name="authentication-mode"></a>Modalità di autenticazione

Selezionare **Windows** (impostazione predefinita) per specificare l'uso dell'autenticazione di Windows per identificare l'utente connesso. È possibile recuperare queste informazioni in fase di esecuzione tramite l'oggetto `My.User`. Selezionare **Definita dall'applicazione** se si intende fornire codice personalizzato per autenticare gli utenti anziché usare i metodi di autenticazione predefiniti di Windows.

### <a name="shutdown-mode"></a>Modalità di arresto

Selezionare **Alla chiusura del form di avvio** (impostazione predefinita) per specificare che l'applicazione deve terminare quando si chiude il modulo impostato come modulo di avvio, anche se sono aperti altri moduli. Selezionare **Alla chiusura dell'ultimo form** per specificare che l'applicazione deve terminare quando si chiude l'ultimo modulo o quando viene chiamata esplicitamente l'istruzione `My.Application.Exit` o `End`.

Selezionare **Alla chiusura esplicita** per specificare che l'applicazione deve terminare quando si chiama in modo esplicito `Shutdown`.

Selezionare **Alla chiusura dell'ultima finestra** per specificare che l'applicazione deve terminare quando viene chiusa l'ultima finestra o quando si chiama in modo esplicito `Shutdown`. Si tratta dell'impostazione predefinita.

Selezionare **Alla chiusura della finestra principale** per specificare che l'applicazione deve terminare quando viene chiusa la finestra principale o quando si chiama in modo esplicito `Shutdown`.

### <a name="splash-screen"></a>Schermata iniziale

Selezionare il modulo che si vuole usare come schermata iniziale. È necessario avere creato precedentemente una schermata iniziale tramite un modulo o un modello. Il valore predefinito **è (None).**

### <a name="view-application-events"></a>Visualizza eventi applicazione

Fare clic su questo pulsante per visualizzare un file di codice di eventi in cui è possibile scrivere gli eventi per `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` e `NetworkAvailabilityChanged` del framework applicazione . È anche possibile eseguire l'override di alcuni metodi del framework applicazione. Ad esempio, è possibile modificare il comportamento di visualizzazione della schermata iniziale eseguendo l'override di `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Proprietà framework applicazione Windows per app WPF (Windows Presentation Foundation)

Queste impostazioni sono disponibili nella sezione **Proprietà framework applicazione Windows** quando il progetto è un'app WPF (Windows Presentation Foundation). Queste opzioni sono disponibili solo se la casella di controllo **Abilita framework applicazione** è selezionata. Le opzioni elencate in questa tabella sono disponibili solo per le applicazioni WPF o browser WPF. Non sono disponibili per le librerie di controlli utente o di controlli personalizzati WPF.

### <a name="shutdown-mode"></a>Modalità di arresto

Questa proprietà è valida solo per le applicazioni WPF (Windows Presentation Foundation).

Selezionare **Alla chiusura esplicita** per specificare che l'applicazione deve terminare quando si chiama in modo esplicito <xref:System.Windows.Application.Shutdown%2A>.

Selezionare **Alla chiusura dell'ultima finestra** per specificare che l'applicazione deve terminare quando viene chiusa l'ultima finestra o quando si chiama in modo esplicito <xref:System.Windows.Application.Shutdown%2A>. Si tratta dell'impostazione predefinita.

Selezionare **Alla chiusura della finestra principale** per specificare che l'applicazione deve terminare quando viene chiusa la finestra principale o quando si chiama in modo esplicito <xref:System.Windows.Application.Shutdown%2A>.

Per altre informazioni sull'uso di questa impostazione, vedere <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Modifica XAML

Questo pulsante apre il file di definizione dell'applicazione (Application.xaml) nell'editor XAML. Quando si fa clic su questo pulsante, *Application.xaml* viene aperto in corrispondenza del nodo di definizione dell'applicazione. Potrebbe essere necessario modificare questo file per eseguire determinate attività, ad esempio la definizione delle risorse. Se il file di definizione dell'applicazione non esiste, Creazione progetti ne crea uno.

### <a name="view-application-events"></a>Visualizza eventi applicazione

Questo pulsante apre il file di classe `Application` (*Application.xaml.vb*) in un editor di codice. Se il file non esiste, Creazione progetti ne crea uno con il nome della classe e dello spazio dei nomi appropriati.

L'oggetto <xref:System.Windows.Application> genera eventi quando si verificano determinate modifiche di stato dell'applicazione (ad esempio, all'avvio o all'arresto dell'applicazione). Per un elenco completo degli eventi esposti da questa classe, vedere <xref:System.Windows.Application>. Questi eventi vengono gestiti nella sezione del codice utente della classe parziale `Application`.
