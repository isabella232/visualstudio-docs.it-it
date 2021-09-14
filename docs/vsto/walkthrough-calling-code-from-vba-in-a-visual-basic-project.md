---
title: 'Procedura dettagliata: Chiamare codice da VBA in un progetto Visual Basic codice'
description: Informazioni su come chiamare un metodo in una personalizzazione a livello di documento Microsoft Word codice Visual Basic, Applications Edition (VBA) nel documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 631511ba470b42d07878d175c953bb7047914fc2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633788"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Procedura dettagliata: Chiamare codice da VBA in un progetto Visual Basic codice
  Questa procedura dettagliata illustra come chiamare un metodo in una personalizzazione a livello di documento di Microsoft Office Word da codice Visual Basic, Applications Edition (VBA) contenuto nel documento. La procedura comporta tre passaggi di base: aggiungere un metodo alla classe dell'elemento host `ThisDocument` , esporre il metodo al codice VBA e quindi chiamare il metodo dal codice VBA contenuto nel documento.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Nonostante in questa procedura dettagliata venga usato Word in modo specifico, i concetti illustrati sono applicabili anche ai progetti a livello di documento di Excel.

 Vengono illustrate le attività seguenti:

- Creazione di un documento contenente codice VBA.

- Concessione dell'attendibilità al percorso del documento con il Centro protezione di Word.

- Aggiunta di un metodo alla classe dell'elemento host `ThisDocument` .

- Esposizione del metodo al codice VBA.

- Chiamata del metodo dal codice VBA.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Creare un documento contenente codice VBA
 Il primo passaggio consiste nel creare un documento con attivazione macro contenente una macro VBA semplice. Per poter creare un progetto di Visual Studio basato su un determinato documento è necessario che quest'ultimo contenga un progetto VBA. In caso contrario, Visual Studio non può modificare il progetto VBA per consentire al codice VBA di eseguire chiamate nell'assembly di personalizzazione.

 Per usare un documento contenente codice VBA già esistente, è possibile ignorare questo passaggio.

### <a name="to-create-a-document-that-contains-vba-code"></a>Per creare un documento contenente codice VBA

1. Avviare Word.

2. Salvare il documento attivo come documento di Word con attivazione **macro \* (docm)** con il nome **DocumentWithVBA**. Salvarla in un percorso a propria scelta, ad esempio, il desktop.

3. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. Nel gruppo **Codice** , selezionare **Visual Basic**.

     Viene aperto Microsoft Visual Basic Editor.

5. Nella finestra, **Progetto** , fare doppio clic su **ThisDocument**.

     Viene aperto il file di codice relativo all'oggetto `ThisDocument` .

6. Aggiungere il codice VBA seguente al file di codice. Questo codice definisce una funzione semplice che non esegue alcuna operazione. L'unico scopo di questa funzione è garantire l'esistenza di un progetto VBA nel documento. Tale requisito dovrà essere soddisfatto in alcuni passaggi successivi di questa procedura dettagliata.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Salvare il documento e uscire da Word.

## <a name="create-the-project"></a>Creare il progetto
 A questo punto è possibile creare un progetto a livello di documento di Word che usa il documento con attivazione macro appena creato.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**. Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual Basic, scegliere **Nuovo progetto** dal menu **File**.

3. Nel riquadro Modelli espandere, **Visual Basic** quindi espandere **Office/SharePoint**.

4. Selezionare il nodo **Componenti aggiuntivi di Office** .

5. Nell'elenco di modelli di progetto, selezionare il progetto **Documento Word 2010** o **Documento di Word 2013** .

6. Nella casella **Nome** digitare **CallingCodeFromVBA**.

7. Fare clic su **OK**.

     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

8. Selezionare **Copia un documento esistente** e, nella casella **Percorso completo del documento esistente** , specificare il percorso del documento **DocumentWithVBA** creato in precedenza. Se si ha già un documento con attivazione macro che si vuole usare, specificare invece il percorso di questo documento.

9. Fare clic su **Fine**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il **documento DocumentWithVBA** nella finestra di progettazione e aggiunge il **progetto CallingCodeFromVBA** **Esplora soluzioni**.

## <a name="trust-the-location-of-the-document"></a>Considerare attendibile il percorso del documento
 Per poter esporre il codice contenuto nella soluzione al codice VBA contenuto nel documento è necessario che quest'ultimo sia impostato come attendibile per l'esecuzione. L'operazione può essere eseguita in vari modi. Questa procedura dettagliata prevede la concessione dell'attendibilità al percorso del documento con il **Centro protezione** di Word.

### <a name="to-trust-the-location-of-the-document"></a>Per concedere l'attendibilità al percorso del documento

1. Avviare Word.

2. Scegliere la scheda **File** .

3. Fare clic sul pulsante **Opzioni Word** .

4. Nel riquadro delle categorie fare clic su **Centro protezione**.

5. Nel riquadro dei dettagli fare clic su Impostazioni **Centro protezione**.

6. Nel riquadro delle categorie fare clic su **Percorsi attendibili**.

7. Nel riquadro dei dettagli fare clic su **Aggiungi nuovo percorso**.

8. Nella finestra di dialogo **Percorso attendibile di Microsoft Office** passare alla cartella contenente il progetto **CallingCodeFromVBA** .

9. Selezionare **Considera attendibili anche le sottocartelle di questo percorso**.

10. Nella finestra di dialogo **Percorso attendibile di Microsoft Office** fare clic su **OK**.

11. Scegliere **OK** nella finestra di dialogo **Centro protezione**.

12. Scegliere **OK** nella finestra di dialogo **Opzioni Word**.

13. Uscire da Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Aggiungere un metodo alla classe ThisDocument
 Ora che il progetto VBA è configurato, aggiungere un metodo alla classe dell'elemento host `ThisDocument` che è possibile chiamare dal codice VBA.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>Per aggiungere un metodo alla classe ThisDocument

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.vb**, quindi scegliere **Visualizza codice**.

     Il file **ThisDocument.vb** verrà aperto nell'editor di codice.

2. Aggiungi alla classe `ThisDocument` il metodo seguente. Questo metodo crea una tabella con due righe e due colonne all'inizio del documento. I parametri specificano il testo visualizzato nella prima riga. Più avanti nella procedura dettagliata questo metodo verrà chiamato dal codice VBA contenuto nel documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb" id="Snippet1":::

3. Compilare il progetto.

## <a name="expose-the-method-to-vba-code"></a>Esporre il metodo al codice VBA
 Per esporre il metodo `CreateTable` al codice VBA contenuto nel documento, impostare la proprietà **EnableVbaCallers** dell'elemento host `ThisDocument` su **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Per esporre il metodo al codice VBA

1. In **Esplora soluzioni** fare doppio clic su **ThisDocument.vb**.

     Il file **DocumentWithVBA** verrà aperto nella finestra di progettazione.

2. Nella finestra **Proprietà** , selezionare la proprietà **EnableVbaCallers** e modificarne il valore impostandola su **True**.

3. Fare clic su **OK** nel messaggio visualizzato.

4. Compilare il progetto.

## <a name="call-the-method-from-vba-code"></a>Chiamare il metodo dal codice VBA
 A questo punto è possibile chiamare il metodo `CreateTable` dal codice VBA contenuto nel documento.

> [!NOTE]
> Questa procedura dettagliata prevede l'aggiunta di codice VBA al documento durante l'esecuzione del debug del progetto. Se si ricompila il progetto, il codice VBA aggiunto a questo documento verrà sovrascritto. Infatti, Visual Studio sostituisce il documento contenuto nella cartella dell'output di compilazione con una copia del documento contenuto nella cartella del progetto principale. Se si vuole salvare il codice VBA è possibile copiarlo nel documento contenuto nella cartella del progetto. Per altre informazioni, vedere [Combinare vba e personalizzazioni a livello di documento.](../vsto/combining-vba-and-document-level-customizations.md)

### <a name="to-call-the-method-from-vba-code"></a>Per chiamare il metodo dal codice VBA

1. Premere **F5** per eseguire il progetto.

2. Nella scheda **Sviluppatore** fare clic su **Visual Basic** nel gruppo **Codice**.

     Viene aperto Microsoft Visual Basic Editor.

3. Scegliere **Modulo** dal menu **Inserisci**.

4. Aggiungere al nuovo modulo il codice seguente.

     Questo codice chiama il metodo `CreateTable` nell'assembly di personalizzazione. Per accedere a tale metodo, la macro usa la proprietà `CallVSTOAssembly` dell'oggetto `ThisDocument` . Questa proprietà è stata generata automaticamente nel passaggio precedente della procedura dettagliata in cui è stata impostata la proprietà **EnableVbaCallers** .

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Premere **F5**.

6. Verificare che nel documento sia stata aggiunta una nuova tabella.

7. Uscire da Word senza salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi
 Altre informazioni su come chiamare elementi di codice in soluzioni Office da VBA sono disponibili negli argomenti seguenti:

- Chiamata di codice da VBA in una personalizzazione di Visual C#. Questo processo è diverso dal processo usato per Visual Basic. Per altre informazioni, vedere [Procedura dettagliata: Chiamare codice da VBA in un progetto Visual C&#35; visuale.](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)

- Chiamare codice in un componente aggiuntivo VSTO da VBA. Per altre informazioni, vedere [Procedura dettagliata: Chiamare codice in un VSTO componente aggiuntivo da VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

## <a name="see-also"></a>Vedi anche
- [Combinare le personalizzazioni VBA e a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Procedura: Esporre codice a VBA in un progetto Visual Basic codice](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Procedura: Esporre il codice a VBA in un progetto Visual C&#35; visual c](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Procedura dettagliata: Chiamare codice da VBA in un progetto visual c&#35; visual c](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
