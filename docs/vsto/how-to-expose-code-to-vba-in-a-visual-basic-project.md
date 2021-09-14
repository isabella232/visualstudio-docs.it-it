---
title: 'Procedura: Esporre codice a VBA in un progetto Visual Basic codice'
description: Informazioni su come esporre il codice in un progetto Visual Basic al codice Visual Basic, Applications Edition (VBA) se si vuole che i due tipi di codice interagiscano tra loro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a943688945ab7134742ff85ec63e7fad5a4f11c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710083"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Procedura: Esporre codice a VBA in un progetto Visual Basic codice
  È possibile esporre il codice in un progetto Visual Basic, Applications Edition (VBA) se si vuole che i due tipi di codice [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] interagiscano tra loro.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Il Visual Basic processo è diverso dal processo di Visual C#. Per altre informazioni, vedere [Procedura: Esporre codice a VBA in un progetto Visual C&#35; .](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)

 Il processo è diverso per il codice in una classe di elemento host rispetto al codice in altre classi:

- [Esporre il codice in una classe di elemento host](#HostItemCode)

- [Esporre il codice che non si trova in una classe di elemento host](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Esporre il codice in una classe di elemento host
 Per consentire al codice VBA di chiamare Visual Basic codice in una classe di elemento host, impostare la **proprietà EnableVbaCallers** dell'elemento host su **True.**

 Per una procedura dettagliata che illustra come esporre un metodo di una classe di elemento host e quindi chiamarlo da VBA, vedere [Procedura dettagliata:](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)Chiamare codice da VBA in un Visual Basic progetto . Per altre informazioni sugli elementi host, vedere [Panoramica di elementi host e controlli host](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Per esporre il codice in un elemento host a VBA

1. Aprire o creare un progetto a livello di documento basato su un documento di Word, una cartella di lavoro Excel o un modello Excel che supporta le macro e che contiene già codice [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA.

     Per altre informazioni sui formati di file di documento che supportano le macro, vedere [Combinare VBA e personalizzazioni a livello di documento.](../vsto/combining-vba-and-document-level-customizations.md)

    > [!NOTE]
    > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Assicurarsi che al codice VBA nel documento sia consentita l'esecuzione senza chiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere la proprietà, il metodo o l'evento che si vuole esporre a VBA a una delle classi di elementi host nel progetto e dichiarare il nuovo membro come **Public**. Il nome della classe dipende dall'applicazione:

    - In un progetto Word la classe dell'elemento host è denominata `ThisDocument` per impostazione predefinita.

    - In un Excel, le classi di elementi host sono denominate `ThisWorkbook` , , e per impostazione `Sheet1` `Sheet2` `Sheet3` predefinita.

4. Impostare la **proprietà EnableVbaCallers** per l'elemento host su **True.** Questa proprietà è disponibile nella finestra **Proprietà** quando l'elemento host è aperto nella finestra di progettazione.

     Dopo aver impostato questa proprietà, Visual Studio imposta automaticamente la **proprietà ReferenceAssemblyFromVbaProject** su **True.**

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **EnableVbaCallers** su **True.** Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

5. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si esegue il progetto da , il codice VBA andrà perso alla successiva compilazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio il progetto in modo che il progetto VBA possa chiamare nell'assembly. Visual Studio aggiunge anche una proprietà denominata al modulo `CallVSTOAssembly` , , , o nel progetto `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` `Sheet3` VBA. È possibile usare questa proprietà per accedere ai membri pubblici della classe esposta a VBA.

6. Compilare il progetto.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Esporre il codice che non si trova in una classe di elemento host
 Per consentire al codice VBA di Visual Basic codice che non si trova in una classe di elemento host, modificare il codice in modo che sia visibile a VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Per esporre il codice che non si trova in una classe di elemento host a VBA

1. Aprire o creare un progetto a livello di documento basato su un documento di Word, una cartella di lavoro Excel o un modello Excel che supporta le macro e che contiene già codice [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA.

     Per altre informazioni sui formati di file di documento che supportano le macro, vedere [Combinare VBA e personalizzazioni a livello di documento.](../vsto/combining-vba-and-document-level-customizations.md)

    > [!NOTE]
    > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Assicurarsi che al codice VBA nel documento sia consentita l'esecuzione senza chiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere il membro che si vuole esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.

4. Applicare gli <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributi e seguenti alla classe che si sta <xref:Microsoft.VisualBasic.ComClassAttribute> esponendo a VBA. Questi attributi rendono la classe visibile a VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA. Nell'esempio di codice seguente si presuppone che si esponga una classe denominata `DocumentUtilities` a VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Aprire la finestra di progettazione del documento (per Word) o del foglio di lavoro (Excel) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

8. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si esegue il progetto da , il codice VBA andrà perso alla successiva compilazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio il progetto in modo che il progetto VBA possa chiamare nell'assembly. Visual Studio aggiunge anche un metodo `GetManagedClass` denominato al progetto VBA. È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.

9. Compilare il progetto.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Progettare e creare Office personalizzate](../vsto/designing-and-creating-office-solutions.md)
- [Combinare le personalizzazioni VBA e a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Procedura dettagliata: Chiamare codice da VBA in un progetto Visual Basic codice](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Procedura: Esporre codice a VBA in un progetto Visual C&#35; codice](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
