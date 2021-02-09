---
title: 'Procedura: esporre il codice a VBA in un progetto Visual Basic'
description: Informazioni su come esporre il codice in un progetto Visual Basic al codice Visual Basic, Applications Edition (VBA) se si desidera che i due tipi di codice interagiscano tra loro.
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
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913488"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Procedura: esporre il codice a VBA in un progetto Visual Basic
  È possibile esporre il codice in un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto al codice Visual Basic, Applications Edition (VBA) se si desidera che i due tipi di codice interagiranno tra loro.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Il processo Visual Basic è diverso dal processo di Visual C#. Per altre informazioni, vedere [procedura: esporre il codice a VBA in un progetto Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Il processo è diverso per il codice in una classe di elementi host rispetto a quello per il codice in altre classi:

- [Esporre il codice in una classe di elementi host](#HostItemCode)

- [Esporre codice non presente in una classe di elementi host](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Esporre il codice in una classe di elementi host
 Per consentire al codice VBA di chiamare Visual Basic codice in una classe di elementi host, impostare la proprietà **EnableVbaCallers** dell'elemento host su **true**.

 Per una procedura dettagliata che illustra come esporre un metodo di una classe dell'elemento host e quindi chiamarlo da VBA, vedere [procedura dettagliata: chiamare il codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Per ulteriori informazioni sugli elementi host, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Per esporre il codice in un elemento host a VBA

1. Aprire o creare un progetto a livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta le macro e che già contiene codice VBA.

     Per ulteriori informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Verificare che il codice VBA nel documento possa essere eseguito senza richiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere la proprietà, il metodo o l'evento che si desidera esporre a VBA a una delle classi di elementi host nel progetto e dichiarare il nuovo membro come **public**. Il nome della classe dipende dall'applicazione:

    - In un progetto di Word, la classe dell'elemento host è denominata `ThisDocument` per impostazione predefinita.

    - In un progetto di Excel, le classi dell'elemento host sono denominate `ThisWorkbook` ,, `Sheet1` `Sheet2` e `Sheet3` per impostazione predefinita.

4. Impostare la proprietà **EnableVbaCallers** per l'elemento host su **true**. Questa proprietà è disponibile nella finestra **Proprietà** quando l'elemento host è aperto nella finestra di progettazione.

     Dopo aver impostato questa proprietà, Visual Studio imposta automaticamente la proprietà **ReferenceAssemblyFromVbaProject** su **true**.

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **EnableVbaCallers** su **true**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

5. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento durante l'esecuzione del progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , il codice VBA verrà perso alla successiva compilazione del progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA possa chiamare nell'assembly. In Visual Studio viene inoltre aggiunta una proprietà denominata `CallVSTOAssembly` al `ThisDocument` `ThisWorkbook` modulo,, `Sheet1` , `Sheet2` o `Sheet3` nel progetto VBA. È possibile usare questa proprietà per accedere ai membri pubblici della classe esposta a VBA.

6. Compilare il progetto.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Esporre codice non presente in una classe di elementi host
 Per consentire al codice VBA di chiamare Visual Basic codice che non si trova in una classe di elementi host, modificare il codice in modo che sia visibile a VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Per esporre il codice che non si trova in una classe dell'elemento host a VBA

1. Aprire o creare un progetto a livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta le macro e che già contiene codice VBA.

     Per ulteriori informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Verificare che il codice VBA nel documento possa essere eseguito senza richiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.

4. Applicare gli <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributi e seguenti <xref:Microsoft.VisualBasic.ComClassAttribute> alla classe che si sta esponendo a VBA. Questi attributi rendono visibile la classe a VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA. Nell'esempio di codice seguente si presuppone l'esposizione di una classe denominata `DocumentUtilities` a VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Aprire la finestra di progettazione del documento (per Word) o del foglio di lavoro (per Excel) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **true**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

8. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento durante l'esecuzione del progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , il codice VBA verrà perso alla successiva compilazione del progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA possa chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.

9. Compilare il progetto.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Procedura dettagliata: chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Procedura: esporre il codice a VBA in un progetto Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
