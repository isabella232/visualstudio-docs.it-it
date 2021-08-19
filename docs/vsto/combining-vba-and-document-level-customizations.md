---
title: Combinare le personalizzazioni VBA e a livello di documento
description: Informazioni su come usare Visual Basic, Applications Edition (VBA) in un documento che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c29399119ffaff26be670a6fee88d8de3c92368c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053950"
---
# <a name="combine-vba-and-document-level-customizations"></a>Combinare le personalizzazioni VBA e a livello di documento
  È possibile usare il codice Visual Basic, Applications Edition (VBA) in un documento incluso in una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel. È possibile chiamare codice VBA nel documento dall'assembly di personalizzazione oppure configurare il progetto in modo da consentire al codice VBA nel documento di chiamare il codice nell'assembly di personalizzazione.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Comportamento del codice VBA in una personalizzazione a livello di documento
 Quando si apre il progetto in Visual Studio, il documento viene aperto in modalità progettazione. In tale modalità, il codice VBA non viene eseguito, quindi è possibile lavorare con il documento e il codice senza eseguire il codice VBA.

 Quando si esegue la soluzione, i gestori eventi in VBA e nell'assembly di personalizzazione selezionano eventi generati nel documento e vengono eseguiti entrambi i set di codice. È impossibile stabilire in anticipo quale dei due codici verrà eseguito per primo. Per ottenere questa informazione è necessario verificare ogni singolo caso. Se i due gruppi di codice non vengono coordinati e testati attentamente, il risultato potrebbe non essere quello previsto.

## <a name="call-vba-code-from-the-customization-assembly"></a>Chiamare il codice VBA dall'assembly di personalizzazione
 È possibile chiamare macro nei documenti di Word nonché macro e funzioni nelle cartelle di lavoro di Excel. A tale scopo, adottare uno dei metodi seguenti:

- Per Word, chiamare <xref:Microsoft.Office.Interop.Word._Application.Run%2A> il metodo della classe <xref:Microsoft.Office.Interop.Word.Application> .

- Per Excel, chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> della classe <xref:Microsoft.Office.Interop.Excel.Application> .

  Per ogni metodo, il primo parametro identifica il nome della macro o della funzione da chiamare e i parametri facoltativi rimanenti specificano i parametri da passare alla macro o alla funzione. Il primo parametro può avere formati diversi per Word ed Excel:

- Per Word, il primo parametro è una stringa che può essere qualsiasi combinazione di nome di modello, modulo e macro. Se si specifica il nome del documento, il codice può eseguire le macro solo nei documenti relativi al contesto corrente, non qualsiasi macro in qualsiasi documento.

- Per Excel, il primo parametro può essere una stringa che specifica il nome della macro, un <xref:Microsoft.Office.Interop.Excel.Range> che indica dove si trova la funzione o un identificatore di registro per una funzione DLL (XLL) registrata. La stringa, se passata, verrà valutata nel contesto del foglio attivo.

  Nell'esempio di codice seguente viene illustrato come chiamare una macro denominata `MyMacro` da un progetto a livello di documento per Excel. In questo esempio si presuppone che `MyMacro` sia definito in `Sheet1`.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Per informazioni sull'uso della `missing` variabile globale al posto dei parametri facoltativi in Visual C#, vedere Scrivere codice in Office [soluzioni](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Chiamare il codice nelle personalizzazioni a livello di documento da VBA
 È possibile configurare un progetto a livello di documento per Word o Excel in modo che il codice Visual Basic, Applications Edition (VBA) del documento sia in grado di chiamare il codice nell'assembly di personalizzazione. Questa operazione è utile negli scenari seguenti:

- Si desidera estendere il codice VBA esistente di un documento usando le funzionalità di una personalizzazione a livello di documento associata allo stesso documento.

- Si desidera rendere i servizi sviluppati in una personalizzazione a livello di documento, disponibili per gli utenti finali in grado di accedere a tali servizi scrivendo codice VBA nel documento.

  Gli Office di sviluppo in Visual Studio offrono una funzionalità simile per VSTO componenti aggiuntivi. Se si sviluppa un componente VSTO, è possibile chiamare il codice nel componente aggiuntivo VSTO da altre soluzioni Microsoft Office. Per altre informazioni, vedere [Chiamare il codice VSTO componenti aggiuntivi da altre soluzioni Office .](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

> [!NOTE]
> Questa funzionalità non può essere usata nei progetti Modello di Word, ma solo nei progetti Documento di Word, Cartella di lavoro di Excel o Modello di Excel.

## <a name="requirements"></a>Requisiti
 Per consentire al codice VBA di eseguire chiamate nell'assembly di personalizzazione, il progetto deve soddisfare i requisiti seguenti:

- Il documento deve avere una delle estensioni di file seguenti:

  - Per Word: *.docm* o *.doc*

  - Ad Excel: *xlsm*, *xlstm*, *.xls* o *xlt*

- Il documento deve già contenere un progetto VBA che include il codice VBA.

- Il codice VBA del documento deve poter essere eseguito senza che venga richiesto all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

- Il progetto di Office deve includere almeno una classe pubblica che contenga uno o più membri pubblici da esporre a VBA.

     È possibile esporre metodi, proprietà ed eventi a VBA. La classe esposta può essere una classe dell'elemento host (ad esempio `ThisDocument` per Word o `ThisWorkbook` e `Sheet1` per Excel) o un'altra classe definita nel progetto. Per altre informazioni sugli elementi host, vedere [Panoramica degli elementi host e dei controlli host.](../vsto/host-items-and-host-controls-overview.md)

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Abilitare il codice VBA per chiamare nell'assembly di personalizzazione
 Esistono due modalità diverse per esporre i membri di un assembly di personalizzazione al codice VBA del documento:

- È possibile esporre a VBA i membri di una classe dell'elemento host di un progetto [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . A tale scopo, impostare la proprietà **EnableVbaCallers** dell'elemento host su **True** nella finestra **Proprietà** mentre l'elemento host (ovvero il documento, il foglio di lavoro o la cartella di lavoro) è aperto nella finestra di progettazione. Visual Studio esegue automaticamente tutte le operazioni necessarie per consentire al codice VBA di chiamare i membri della classe.

- È possibile esporre a VBA i membri di qualsiasi classe pubblica di un progetto Visual C# o i membri di una classe di elementi non host di un progetto [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] . Questa opzione offre una maggiore libertà di scelta delle classi da esporre a VBA ma richiede più passaggi manuali.

   A tale scopo, è necessario eseguire la procedura principale seguente:

  1. Esporre la classe a COM.

  2. Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA.

  3. Impostare la proprietà **ReferenceAssemblyFromVbaProject** di una qualsiasi classe di elementi host nel progetto su **True**. In questo modo, la libreria dei tipi dell'assembly di personalizzazione viene incorporata nell'assembly e viene aggiunto un riferimento alla libreria dei tipi al progetto VBA nel documento.

  Per istruzioni dettagliate, vedere [Procedura:](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) Esporre il codice a VBA in un progetto Visual Basic e [Procedura: Esporre](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)codice a VBA in un progetto Visual C&#35; .

  Le proprietà **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** sono disponibili nella finestra **Proprietà** solo in fase di progettazione; non possono essere usate in fase di esecuzione. Per visualizzare le proprietà, aprire la finestra di progettazione per un elemento host in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni sulle attività specifiche eseguite Visual Studio quando si impostano queste proprietà, vedere Attività eseguite dalle [proprietà dell'elemento host.](#PropertyTasks)

> [!NOTE]
> Se la cartella di lavoro o il documento non contiene già il codice VBA o se il codice VBA del documento non è considerato attendibile per l'esecuzione, si riceve un messaggio di errore quando si imposta la proprietà **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** su **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Usare i membri nel codice VBA per chiamare nell'assembly di personalizzazione
 Dopo avere configurato il progetto per consentire al codice VBA di eseguire chiamate nell'assembly di personalizzazione, in Visual Studio vengono aggiunti i membri seguenti al progetto VBA nel documento:

- Per tutti i progetti, in Visual Studio viene aggiunto un metodo globale denominato `GetManagedClass`.

- Per i progetti in cui si espongono i membri di una classe di elementi host usando la proprietà [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **EnableVbaCallers,** Visual Studio aggiunge anche una proprietà denominata al modulo , , , o nel progetto `CallVSTOAssembly` `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` `Sheet3` VBA.

  È possibile usare la proprietà `CallVSTOAssembly` o il metodo `GetManagedClass` per accedere ai membri pubblici della classe esposta al codice VBA nel progetto.

> [!NOTE]
> Durante lo sviluppo e la distribuzione della soluzione esistono alcune copie diverse del documento in cui è possibile aggiungere il codice VBA. Per altre informazioni, vedere [Linee guida per l'aggiunta di codice VBA al documento](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Usare la proprietà CallVSTOAssembly in un Visual Basic progetto
 Usare la proprietà `CallVSTOAssembly` per accedere ai membri pubblici aggiunti alla classe di elementi host. Ad esempio, la macro VBA seguente chiama un metodo denominato `MyVSTOMethod` , definito nella classe `Sheet1` in un progetto di cartella di lavoro di Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Questa proprietà rappresenta un modo più pratico per effettuare chiamate nell'assembly di personalizzazione rispetto all'utilizzo diretto del metodo `GetManagedClass` . `CallVSTOAssembly` restituisce un oggetto che rappresenta la classe di elementi host esposta a VBA. I membri e i parametri del metodo dell'oggetto restituito sono visualizzati in IntelliSense.

 La proprietà `CallVSTOAssembly` dispone di una dichiarazione che è simile al codice seguente. Tale codice presuppone che sia stata esposta a VBA la classe di elementi host `Sheet1` in un progetto di cartella di lavoro di Excel denominato `ExcelWorkbook1` .

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Usare il metodo GetManagedClass
 Per usare il metodo globale `GetManagedClass` , passare l'oggetto VBA corrispondente alla classe di elementi host contenente l'override del metodo **GetAutomationObject** . Quindi, usare l'oggetto restituito per accedere alla classe esposta a VBA.

 Ad esempio, la macro VBA seguente chiama un metodo denominato `MyVSTOMethod` , definito nella classe di elementi host `Sheet1` in un progetto di cartella di lavoro di Excel denominato `ExcelWorkbook1`.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 Il metodo `GetManagedClass` presenta in genere la dichiarazione seguente:

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Questo metodo restituisce un oggetto che rappresenta la classe esposta a VBA. I membri e i parametri del metodo dell'oggetto restituito sono visualizzati in IntelliSense.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Linee guida per l'aggiunta di codice VBA al documento
 Esistono alcune copie diverse del documento in cui è possibile aggiungere il codice VBA che effettua chiamate nella personalizzazione a livello di documento.

 Durante lo sviluppo e la verifica della soluzione è possibile scrivere il codice VBA nel documento che si apre mentre si esegue il debug o il progetto in Visual Studio (ovvero, il documento nella cartella dell'output della compilazione). Tuttavia, il codice VBA aggiunto a questo documento verrà sovrascritto alla successiva compilazione del progetto. Infatti, Visual Studio sostituisce il documento contenuto nella cartella dell'output della compilazione con una copia del documento contenuta nella cartella del progetto principale.

 Se si desidera salvare il codice VBA aggiunto al documento durante l'esecuzione del debug o della soluzione, copiare il codice VBA nel documento nella cartella del progetto. Per altre informazioni sul processo di compilazione, vedere Creare [soluzioni Office.](../vsto/building-office-solutions.md)

 Quando si è pronti per distribuire la soluzione, sono disponibili tre percorsi principali del documento nei quali è possibile aggiungere il codice VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>Nella cartella del progetto nel computer di sviluppo
 Questo percorso è utile se si ha un controllo completo sul codice VBA del documento e sul codice di personalizzazione. Poiché il documento si trova nel computer di sviluppo, è possibile modificare facilmente il codice VBA qualora si modifichi il codice della personalizzazione. Il codice VBA aggiunto a questa copia del documento rimane nel documento quando si compila, si sottopone a debug e si pubblica la soluzione.

 Non è possibile aggiungere il codice VBA al documento mentre è aperto nella finestra di progettazione. Prima è necessario chiudere il documento nella finestra di progettazione e quindi aprire direttamente il documento in Word o Excel.

> [!CAUTION]
> Se si aggiunge codice VBA in esecuzione quando il documento è aperto, in rari casi può accadere che tale codice danneggi il documento o ne impedisca l'apertura nella finestra di progettazione.

### <a name="in-the-publish-or-installation-folder"></a>Nella cartella publish o installation
 In alcuni casi potrebbe essere utile aggiungere il codice VBA al documento nella cartella di pubblicazione o di installazione. Ad esempio, è possibile scegliere questa opzione se il codice VBA è scritto e testato da uno sviluppatore diverso in un computer in cui non è installato Visual Studio.

 Se gli utenti installano la soluzione direttamente dalla cartella di pubblicazione, è necessario aggiungere il codice VBA al documento ogni volta che si pubblica la soluzione. Visual Studio sovrascrive il documento nel percorso di pubblicazione quando si pubblica la soluzione.

 Se gli utenti installano la soluzione da una cartella di installazione diversa dalla cartella di pubblicazione, è possibile evitare di aggiungere il codice VBA al documento ogni volta che si pubblica la soluzione. Quando un aggiornamento della pubblicazione è pronto per essere spostato dalla cartella di pubblicazione alla cartella di installazione, copiare tutti i file nella cartella di installazione tranne il documento.

### <a name="on-the-end-user-computer"></a>Nel computer dell'utente finale
 Se gli utenti finali sono sviluppatori VBA che effettuano chiamate nei servizi forniti nella personalizzazione a livello di documento, è possibile specificare come chiamare il codice usando la proprietà `CallVSTOAssembly` o il metodo `GetManagedClass` nelle copie del documento. Quando si pubblicano aggiornamenti nella soluzione, il codice VBA nel documento nel computer dell'utente finale non verrà sovrascritto, perché il documento non viene modificato dagli aggiornamenti di pubblicazione.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Attività eseguite dalle proprietà dell'elemento host
 Quando si usano le proprietà **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** , in Visual Studio vengono eseguite serie diverse di attività.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Quando si imposta la proprietà **EnableVbaCallers** di un elemento host su **True** in un progetto Visual Basic, in Visual Studio vengono eseguite le attività seguenti:

1. Vengono aggiunti gli attributi <xref:Microsoft.VisualBasic.ComClassAttribute> e <xref:System.Runtime.InteropServices.ComVisibleAttribute> alla classe di elementi host.

2. Viene eseguito l'override del metodo **GetAutomationObject** della classe di elementi host.

3. Viene impostata la proprietà **ReferenceAssemblyFromVbaProject** dell'elemento host su **True**.

   Quando si imposta la proprietà **EnableVbaCallers** di nuovo su **False**, in Visual Studio vengono eseguite le attività seguenti:

4. Vengono rimossi gli attributi <xref:Microsoft.VisualBasic.ComClassAttribute> e <xref:System.Runtime.InteropServices.ComVisibleAttribute> dalla classe `ThisDocument` .

5. Viene rimosso il metodo **GetAutomationObject** dalla classe di elementi host.

   > [!NOTE]
   > In Visual Studio la proprietà **ReferenceAssemblyFromVbaProject** non viene impostata automaticamente di nuovo su **False**. È possibile impostare questa proprietà manualmente su **False** usando la finestra **Proprietà** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Quando la proprietà **ReferenceAssemblyFromVbaProject** di qualsiasi elemento host in un progetto di Visual Basic o Visual C# viene impostata su **True**, in Visual Studio vengono eseguite le attività seguenti:

1. Viene generata una libreria dei tipi per l'assembly di personalizzazione e la incorpora nell'assembly.

2. Viene aggiunto un riferimento alle librerie dei tipi seguenti nel progetto VBA nel documento:

   - Libreria dei tipi per l'assembly di personalizzazione.

   - Microsoft Visual Studio Tools per la libreria dei tipi Office Execution Engine 9.0. Questa libreria di tipi è inclusa in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

   Quando la proprietà **ReferenceAssemblyFromVbaProject** è impostata di nuovo su **False**, in Visual Studio vengono eseguite le attività seguenti:

3. Vengono rimossi i riferimenti alla libreria dei tipi dal progetto VBA nel documento.

4. Viene rimossa la libreria dei tipi incorporata dall'assembly.

## <a name="troubleshoot"></a>Risolvere problemi
 Nella tabella seguente sono elencati alcuni errori comuni e i suggerimenti per correggerli.

|Errore|Suggerimento|
|-----------|----------------|
|Dopo aver impostato la proprietà **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un messaggio di errore indica che il documento non contiene un progetto VBA o che non si dispone delle autorizzazioni per accedere al progetto VBA nel documento.|Assicurarsi che il documento nel progetto contenga almeno una macro VBA, che il progetto VBA sia sufficientemente attendibile per essere eseguito e che non sia protetto da una password.|
|Dopo aver impostato la proprietà **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un messaggio di errore indica che la dichiarazione <xref:System.Runtime.InteropServices.GuidAttribute> manca o è danneggiata.|Assicurarsi che la dichiarazione si trovi nel <xref:System.Runtime.InteropServices.GuidAttribute> file *AssemblyInfo.cs* o *AssemblyInfo.vb* nel progetto e che questo attributo sia impostato su un GUID valido.|
|Dopo aver impostato la proprietà **EnableVbaCallers** o **ReferenceAssemblyFromVbaProject** , un messaggio di errore indica che il numero di versione specificato da <xref:System.Reflection.AssemblyVersionAttribute> non è valido.|Assicurarsi che la <xref:System.Reflection.AssemblyVersionAttribute> dichiarazione nel file *AssemblyInfo.cs* o *AssemblyInfo.vb* nel progetto sia impostata su un numero di versione dell'assembly valido. Per informazioni sui numeri di versione di assembly validi, vedere la classe <xref:System.Reflection.AssemblyVersionAttribute> .|
|Dopo avere rinominato l'assembly di personalizzazione, il codice VBA che effettua chiamate nell'assembly di personalizzazione smette di funzionare.|Se si modifica il nome dell'assembly di personalizzazione dopo averlo esposto al codice VBA, il collegamento tra il progetto VBA nel documento e l'assembly di personalizzazione viene interrotto. Per correggere questo problema, impostare la proprietà **ReferenceFromVbaAssembly** nel progetto su **False** e poi di nuovo su **True**, quindi sostituire qualsiasi riferimento al nome dell'assembly precedente nel codice VBA con il nome del nuovo assembly.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Esporre il codice a VBA in un Visual Basic progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Procedura: Esporre codice a VBA in un progetto Visual C&#35; visuale](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Procedura dettagliata: Chiamare codice da VBA in un Visual Basic progetto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Procedura dettagliata: Chiamare codice da VBA in un progetto visual c&#35; visual c](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Confronto tra soluzioni VBA e Office in Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
