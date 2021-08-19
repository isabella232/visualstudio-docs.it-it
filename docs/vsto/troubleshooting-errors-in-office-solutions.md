---
title: Risolvere gli errori nelle Office soluzioni
description: Informazioni su come risolvere gli errori che possono verificarsi durante lo sviluppo Microsoft Office soluzioni in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d5959df0d24db2807bead8331d04befb7f769ae8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099490"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Risolvere gli errori nelle Office soluzioni
  Questi problemi possono verificarsi quando si eseguono le attività seguenti durante lo sviluppo di soluzioni Office in Visual Studio:

- [Creare, aggiornare e aprire progetti](#creating)

- [Usare le finestre di progettazione](#designers)

- [Scrittura di codice](#code)

- [Compilare progetti](#building)

- [Eseguire il debug di progetti](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a> Creare, aggiornare e aprire progetti
 Gli errori seguenti possono verificarsi quando si creano o si aprono progetti di Office.

### <a name="the-project-cannot-be-created"></a>Non è possibile creare il progetto
 Si è verificato un errore durante un tentativo di creare o aprire un progetto di Office, ma Visual Studio non dispone di informazioni sufficienti per determinare la causa. Provare a chiudere il progetto, uscire da Visual Studio e avviarlo di nuovo.

 Se si sta cercando di creare un progetto a livello di documento, è possibile che un altro documento con lo stesso nome di quello nel nuovo progetto sia già aperto in Excel o Word. Assicurarsi che tutte le altre istanze di Excel o Word siano chiuse.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Le proprietà del controllo vengono perse quando si crea un nuovo progetto basato su un documento da un progetto esistente
 Se si crea un nuovo progetto di Office basato su un documento da un progetto esistente, le proprietà dei controlli presenti nel documento non vengono copiate nel nuovo progetto. È necessario reimpostare manualmente le proprietà per tutti i controlli preesistenti. In alternativa, è possibile mantenere le proprietà dei controlli creando una copia del progetto esistente anziché creare un nuovo progetto oppure caricando il progetto esistente nella nuova soluzione (nella finestra di progettazione) e copiando e incollando i controlli dal documento esistente al nuovo documento.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Errori quando si crea un progetto Excel cartella di lavoro basata su una cartella di lavoro esistente
 Se si crea un nuovo progetto Excel cartella di lavoro basata su una cartella di lavoro esistente, è possibile che venga visualizzata una combinazione degli errori seguenti.

 Da Excel: "Avviso per la privacy: questo documento contiene macro, controlli ActiveX, informazioni del pacchetto di espansione XML o componenti Web. Potrebbero essere presenti informazioni personali che non possono essere rimosse tramite Controllo documento."

 Da Visual Studio: "Impossibile caricare correttamente la finestra di progettazione."

 Questi errori possono verificarsi quando si cerca di creare un progetto basato su una cartella di lavoro in cui le informazioni personali sono state rimosse tramite Controllo documento. Per evitare questo errore, eseguire la procedura seguente prima di creare il progetto.

1. Aprire la cartella di lavoro in Excel.

2. In Excel aprire il Centro protezione.

3. Nella scheda **Opzioni privacy deselezionare** la casella di controllo **Rimuovi informazioni personali dalle proprietà** del file al salvataggio .

4. Salvare la cartella di lavoro e chiudere Excel.

### <a name="cannot-open-a-project-after-migration"></a>Impossibile aprire un progetto dopo la migrazione
 Dopo la migrazione di una soluzione Office a Microsoft Office 2010, non è possibile aprire il progetto in un computer di sviluppo in cui è installato solo Microsoft Office System 2007. Potrebbero venire visualizzati gli errori seguenti.

 "Uno o più progetti della soluzione non sono stati caricati correttamente. Per dettagli, vedere la finestra di output".

 "Impossibile creare il progetto perché l'applicazione associata al tipo di progetto non è installata nel computer. È necessario installare l'applicazione di Microsoft Office associata al tipo di progetto corrente."

 Per risolvere questo problema, modificare il file *con estensione vbproj* *o csproj.* Per un progetto di Word, sostituire HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" con HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Per un progetto di Excel, sostituire HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" con HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}". Per un progetto di Outlook, sostituire HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" con HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".

 In alternativa, assicurarsi che i progetti migrati vengano aperti solo nei computer di sviluppo in cui è già installato Microsoft Office 2010.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Errori nei progetti Office 2003 a livello di documento contenenti Windows form
 Se si aggiorna un progetto Microsoft Office 2003 a livello di documento e il documento contiene controlli form Windows, il progetto aggiornato potrebbe avere errori di compilazione o di runtime. Per evitare questo problema, installare Visual Studio 2005 Tools per Office Second Edition Runtime nel computer di sviluppo prima di aggiornare il progetto. Questa versione del runtime è disponibile come pacchetto ridistribuibile dall'Area download Microsoft in [Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

 Dopo aver completato l'aggiornamento del progetto, è possibile disinstallare Visual Studio 2005 Tools per Office Second Edition Runtime dal computer di sviluppo se non viene usato da altre soluzioni Office.

## <a name="use-the-designers"></a><a name="designers"></a> Usare le finestre di progettazione
 Gli errori seguenti possono verificarsi quando si lavora con la finestra di progettazione di documenti, cartelle di lavoro o fogli di lavoro nei progetti a livello di documento.

### <a name="designer-failed-to-load-correctly"></a>La finestra di progettazione non è stata caricata correttamente
 Visual Studio non può aprire la finestra di progettazione nei casi seguenti:

- Excel o Word è già aperto ed è visualizzata una finestra di dialogo modale. Per aprire la finestra di progettazione, verificare se in Excel o in Word è aperta una finestra di dialogo modale e chiudere eventuali finestre di dialogo modali aperte. Se non ci sono finestre di dialogo modali aperte, potrebbe essere necessario eseguire altre azioni affinché Excel o Word risponda.

- Il progetto corrente è in fase di debug. Per aprire la finestra di progettazione, interrompere o terminare il debug.

- Un componente aggiuntivo VSTO di Excel installato nel computer di sviluppo provoca la visualizzazione di una finestra di dialogo all'avvio di Excel. Per creare un progetto a livello di documento di Excel, è prima necessario disabilitare il componente aggiuntivo VSTO.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>I controlli vengono visualizzati come rettangoli neri nel documento o nel foglio di lavoro
 Se si raggruppano i controlli in un documento o in un foglio di lavoro, Visual Studio non li riconosce più. I controlli raggruppati non sono accessibili nella **finestra** Proprietà e vengono visualizzati come rettangoli neri nel documento o nel foglio di lavoro. Per ripristinare le relative funzionalità, è necessario separare i controlli.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>I controlli in un modello di Word non sono visibili in Visual Studio
 Se si apre un modello di Word nella finestra di progettazione di Visual Studio, i controlli del modello che non sono in linea con il testo potrebbero non essere visibili. Questo perché Visual Studio i modelli di Word nella **visualizzazione** normale. Per visualizzare i controlli, fare **clic** sul menu Visualizza , scegliere **Microsoft Office Word View** e quindi fare clic su Layout di **stampa**.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Il comando Inserisci ClipArt non esegue alcuna operazione nella finestra Visual Studio progettazione
 Quando Excel o Word è aperto nella finestra di progettazione di Visual Studio,  facendo clic sul pulsante **ClipArt** nella scheda Illustrazioni della barra multifunzione non viene aperto il riquadro **attività ClipArt.** Per aggiungere ClipArt, è necessario aprire la copia della cartella di lavoro o del documento che si trova nella cartella principale del progetto (non nella cartella *\bin)* all'esterno di Visual Studio, aggiungere la ClipArt e quindi salvare la cartella di lavoro o il documento.

## <a name="write-code"></a><a name="code"></a> Scrivere codice
 Gli errori seguenti possono verificarsi quando si scrive codice nei progetti di Office.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Alcuni eventi di Office oggetti non sono accessibili quando si usa C\#
 In alcuni casi, potrebbe venire visualizzato un errore del compilatore simile al seguente quando si tenta di accedere a un evento specifico di un'istanza di un tipo di assembly di interoperabilità primario di Office in un progetto Visual C#.

 "Ambiguità tra 'Microsoft.Office.Interop.Excel._Application.NewWorkbook' e 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook'"

 Questo errore indica che si sta tentando di accedere a un evento che ha lo stesso nome di un'altra proprietà o un altro metodo dell'oggetto. Per accedere all'evento, è necessario eseguire il cast dell'oggetto alla relativa *interfaccia eventi*.

 I tipi di assembly di interoperabilità primari di Office che dispongono di eventi implementano due interfacce: un'interfaccia principale con tutte le proprietà e i metodi e un'interfaccia eventi che contiene gli eventi esposti dall'oggetto. Queste interfacce di evento usano la convenzione di *denominazione objectname* Events *n _Event,* ad esempio <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> e <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Se non è possibile accedere a un evento che si prevede di trovare in un oggetto, eseguire il cast dell'oggetto alla relativa interfaccia eventi.

 Ad esempio, gli oggetti <xref:Microsoft.Office.Interop.Excel.Application> dispongono di un evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> e una proprietà <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>. Per gestire l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>, eseguire il cast di <xref:Microsoft.Office.Interop.Excel.Application> all'interfaccia <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>. L'esempio di codice seguente illustra come eseguire questa operazione in un progetto a livello di documento per Excel.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs" id="Snippet1":::

 Per altre informazioni sulle interfacce evento negli assembly di interoperabilità Office, vedere Panoramica di classi e interfacce nel Office assembly di [interoperabilità primari.](/previous-versions/office/office-12//ms247299(v=office.12))

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Non è possibile Office classi PIA nei progetti che hanno come destinazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] il codice che fa riferimento a una classe definita in un assembly di interoperabilità primario di Office non verrà compilato per impostazione predefinita. Le classi negli pias usano la convenzione di denominazione *objectname* Class, ad esempio <xref:Microsoft.Office.Interop.Word.DocumentClass> e <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . Ad esempio, il codice seguente di un progetto di componente aggiuntivo VSTO di Word non verrà compilato.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Questo codice genera gli errori di compilazione seguenti:

- Visual Basic: "Il riferimento alla classe 'DocumentClass' non è consentito quando il relativo assembly è collegato usando la modalità No-PIA".

- Visual C#: "Il tipo di interoperabilità 'Microsoft.Office.Interop.Word.DocumentClass' non può essere incorporato. Utilizzare l'interfaccia applicabile."

  Per risolvere l'errore, modificare il codice in modo che faccia riferimento all'interfaccia corrispondente. Ad esempio, anziché fare riferimento a un oggetto <xref:Microsoft.Office.Interop.Word.DocumentClass>, fare riferimento a un'istanza dell'interfaccia <xref:Microsoft.Office.Interop.Word.Document>.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] incorporano automaticamente per impostazione predefinita tutti i tipi di interoperabilità dagli assembly di interoperabilità primari di Office. Questo errore di compilazione si verifica perché la funzionalità dei tipi di interoperabilità incorporati funziona solo con le interfacce e non con le classi. Per altre informazioni sulle interfacce e le classi negli assembly di interoperabilità Office, vedere Panoramica di classi e interfacce nel Office assembly di [interoperabilità primari.](/previous-versions/office/office-12/ms247299(v=office.12)) Per altre informazioni sulla funzionalità dei tipi di interoperabilità incorporati nei Office, vedere Progettare e [creare Office di interoperabilità.](../vsto/designing-and-creating-office-solutions.md)

### <a name="references-to-office-classes-are-not-recognized"></a>I riferimenti Office classi non vengono riconosciuti
 Alcuni nomi di classe, ad esempio Application, sono in più spazi dei nomi, ad esempio <xref:Microsoft.Office.Interop.Word> e <xref:System.Windows.Forms> . Per questo motivo, **l'istruzione imports** using all'inizio dei modelli di progetto include una costante di qualifica abbreviata, /  ad esempio:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet2":::

 Questo utilizzo **dell'istruzione imports** using richiede la differenziazione dei riferimenti alle classi Office con il qualificatore /  word o Excel, ad esempio:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet3":::

 Se si usa una dichiarazione non qualificata, vengono generati errori, ad esempio:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet4":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet4":::

 Anche se è stato importato lo spazio dei nomi Word o Excel e si ha accesso a tutte le classi al suo interno, è necessario qualificare tutti i tipi con Word o Excel per rimuovere l'ambiguità dello spazio dei nomi.

## <a name="build-projects"></a><a name="building"></a> Compilare i progetti
 Gli errori seguenti possono verificarsi quando si compilano progetti di Office.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Impossibile compilare un progetto a livello di documento basato su un documento con autorizzazioni limitate
 Visual Studio non può compilare progetti a livello di documento se il documento ha autorizzazioni limitate. Se il progetto contiene un documento con autorizzazioni limitate, il progetto non verrà compilato e nella finestra Elenco errori verrà visualizzato **il messaggio** seguente.

 "Impossibile aggiungere la personalizzazione."

 Se si vuole includere un documento con autorizzazioni limitate, usare un documento senza restrizioni quando si sviluppa e si compila la soluzione. Applicare quindi le autorizzazioni limitate al documento nel percorso di pubblicazione, dopo aver pubblicato la soluzione.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Gli errori del compilatore si verificano dopo l'eliminazione di un controllo NamedRange
 Se si elimina un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> da un foglio di lavoro che non è il foglio di lavoro attivo nella finestra di progettazione, il codice generato automaticamente potrebbe non venire rimosso dal progetto e potrebbero verificarsi errori del compilatore. Per assicurarsi che il codice venga rimosso, è consigliabile selezionare sempre il foglio di lavoro contenente il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per renderlo attivo prima di eliminare il controllo. Se il codice generato automaticamente non viene eliminato quando si elimina il controllo, è possibile fare in modo che venga eliminato dalla finestra di progettazione attivando il foglio di lavoro e apportando una modifica, in modo che il foglio di lavoro venga contrassegnato come modificato. Quando si ricompila il progetto, il codice viene rimosso.

## <a name="debug-projects"></a><a name="debugging"></a> Eseguire il debug di progetti
 Gli errori seguenti possono verificarsi quando si esegue il debug di progetti di Office.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>La richiesta di disinstallazione viene visualizzata quando si pubblica e si installa una soluzione nel computer di sviluppo
 Quando si esegue il debug di una soluzione Office, è possibile che venga visualizzato il messaggio di errore seguente.

 "Impossibile installare la personalizzazione perché ne è installata un'altra versione che non può essere aggiornata da questo percorso."

 Questo errore indica che la soluzione Office è stata pubblicata e installata in precedenza nel computer di sviluppo. Per impedire la visualizzazione del messaggio, disinstallare la soluzione dall'elenco dei programmi installati nel computer prima di eseguire il debug della soluzione. In alternativa, è possibile creare un altro account utente nel computer di sviluppo per testare l'installazione della soluzione pubblicata.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>I progetti a livello di documento creati in percorsi di rete UNC non vengono eseguiti da Visual Studio
 Se si crea un progetto a livello di documento per Excel o Word in un percorso di rete UNC, è necessario aggiungere il percorso del documento all'elenco di percorsi attendibili in Excel o Word. In caso contrario, la personalizzazione non verrà caricata quando si tenta di eseguire il progetto o il relativo debug in Visual Studio. Per altre informazioni sui percorsi attendibili, vedere [Concedere l'attendibilità ai documenti.](../vsto/granting-trust-to-documents.md)

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>I thread non vengono arrestati correttamente dopo il debug
 I progetti di Office in Visual Studio seguono una convenzione di denominazione dei thread che consente al debugger di chiudere correttamente il programma. Se si creano thread nella soluzione, è necessario denominare ogni thread con il prefisso VSTA_ per garantire che questi thread vengano gestiti correttamente quando si arresta il debug. Ad esempio, è possibile impostare la proprietà di un thread che attende che un evento `Name` di rete VSTA_NetworkListener . 

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Impossibile eseguire o eseguire il debug Office soluzione nel computer di sviluppo
 Se non è possibile eseguire o sviluppare un progetto di Office nel computer di sviluppo, potrebbe venire visualizzato il messaggio di errore seguente.

 "Impossibile creare il dominio applicazione. Personalizzazione non caricata."

 Visual Studio usa Fusion, il caricatore di assembly .NET Framework, per memorizzare nella cache gli assembly prima di caricare le soluzioni Office. Assicurarsi che Visual Studio possa scrivere nella cache Fusion e riprovare. Per altre informazioni, vedere [Assembly di copie shadow.](/dotnet/framework/app-domains/shadow-copy-assemblies)

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Errore durante l'arresto del debugger in un progetto a livello di documento dopo l'uso di Modifica e continuazione
 Se si  usa  Modifica e continuazione per apportare modifiche al codice in un progetto a livello di documento per Excel o Word mentre il progetto è in modalità di interruzione, è possibile che venga visualizzata una finestra di dialogo con il messaggio di errore seguente se successivamente si arresta il debugger.

 "L'interruzione del processo nello stato corrente può causare effetti indesiderati, incluse la perdita dei dati e l'instabilità del sistema."

 Se si fa **clic su Sì** o **No** nella finestra di dialogo, Visual Studio termina il Excel o il processo di Word e arresta il debugger. Per interrompere il debug del progetto senza visualizzare questa finestra di dialogo, uscire da Excel o Word direttamente anziché arrestare il debugger in Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Risolvere i problemi Office soluzioni](../vsto/troubleshooting-office-solutions.md)
- [Risolvere i Office della soluzione](../vsto/troubleshooting-office-solution-security.md)
- [Risolvere i problemi Office distribuzione della soluzione](../vsto/troubleshooting-office-solution-deployment.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
