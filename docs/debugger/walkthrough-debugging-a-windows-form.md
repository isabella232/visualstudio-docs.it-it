---
title: Debug di un Windows Form | Microsoft Docs
description: "Seguire una procedura dettagliata per vedere come creare ed eseguire il debug di un Windows Form, un'applicazione gestita comune. È possibile utilizzare C#, Visual Basic, C++ o F #."
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c1bc9e65eb63877d8f8a42902d8ec47a61fd22
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148093"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procedura dettagliata: Debug di un Windows Form
Windows Form è una delle più comuni applicazioni gestite. Un Windows Form crea un'applicazione Windows standard. È possibile completare questa procedura dettagliata utilizzando Visual Basic, C# o C++.

 Prima di tutto, è necessario chiudere tutte le soluzioni aperte.

### <a name="to-prepare-for-this-walkthrough"></a>Operazioni preliminari per la procedura dettagliata

- Se è già aperta una soluzione aperta, chiuderla. Scegliere **Chiudi soluzione** dal menu **file** .

## <a name="create-a-new-windows-form"></a>Creare un nuovo Windows Form
 Successivamente, verrà creato un nuovo Windows Form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Per creare il Windows Form per questa procedura dettagliata

1. Scegliere **nuovo** dal menu **file** e fare clic su **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Nel riquadro Tipi progetto aprire il nodo **Visual Basic**, **Visual C#** o **Visual C++** , quindi

    1. Per Visual Basic o Visual C#, selezionare   >  **app Windows Form** per desktop Windows.

    2. Per Visual C++ selezionare **applicazione desktop di Windows**.

3. Nella casella **nome** assegnare al progetto un nome univoco, ad esempio Walkthrough_SimpleDebug.

4. Fare clic su **OK**.

     Visual Studio crea un nuovo progetto e visualizza un nuovo modulo nella finestra di progettazione Windows Forms. Per ulteriori informazioni, vedere [Progettazione Windows Form](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. Scegliere **casella degli strumenti** dal menu **Visualizza** .

     Verrà visualizzata la casella degli strumenti. Per altre informazioni, vedere [Casella degli strumenti](../ide/reference/toolbox.md).

6. Nella casella degli strumenti fare clic sul controllo **Button** e trascinare il controllo nell'area di progettazione del form. Rilasciare il pulsante nel form.

7. Nella casella degli strumenti fare clic sul controllo **TextBox** e trascinare il controllo nell'area di progettazione del form. Rilasciare la **casella di testo** nel form.

8. Nell'area di progettazione del form fare doppio clic sul pulsante.

     Verrà quindi riportata la tabella codici. Il cursore deve essere in `button1_Click` .

10. Nella funzione `button1_Click`. aggiungere il codice seguente:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. Scegliere **Compila soluzione** dal menu **Compila**.

     Il progetto dovrebbe essere compilato senza errori.

## <a name="debug-your-form"></a>Eseguire il debug del modulo
 A questo punto si è pronti per iniziare il debug.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Per eseguire il debug del Windows Form creato per questa procedura dettagliata

1. Nella finestra di origine fare clic sul margine sinistro sulla stessa riga del testo aggiunto:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso. Il punto di colore rosso rappresenta un punto di interruzione. Per altre informazioni, vedere [Punti di interruzione](/previous-versions/ktf38f66(v=vs.100)). Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta. Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug.

    > [!NOTE]
    > È anche possibile fare clic con il pulsante destro del mouse su una qualsiasi riga di codice, scegliere punto di **interruzione**, quindi fare clic su Inserisci punto di **interruzione** per aggiungere un punto di interruzione nella riga.

2. Scegliere **Avvia** dal menu **debug** .

     Viene avviata l'esecuzione di Windows Form.

3. In Windows Form fare clic sul pulsante aggiunto.

     In Visual Studio si passa alla riga in cui è stato impostato il punto di interruzione nella tabella codici. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. È stata arrestata l'esecuzione dell'applicazione, in attesa di un'azione da te.

4. Scegliere **finestre** dal menu **debug** , quindi **guardare** e fare clic su **controllo1**.

5. Nella finestra **controllo1** fare clic su una riga vuota. Nella colonna **nome** Digitare `textBox1.Text` (se si utilizza Visual Basic o Visual C#) o `textBox1->Text` (se si utilizza C++), quindi premere INVIO.

     La finestra **controllo1** Mostra il valore di questa variabile tra virgolette come:

    `""`

6. Scegliere **Esegui istruzione** dal menu **Debug**.

     Il valore di textBox1. Text viene modificato nella finestra **controllo1** per:

    `Button was clicked!`

7. Scegliere **continua** dal menu **debug** per riprendere il debug del programma.

8. Nel Windows Form, fare di nuovo clic sul pulsante.

     Visual Studio interrompe di nuovo l'esecuzione.

9. Fare clic sul punto rosso che rappresenta il punto di interruzione.

     Il punto di interruzione verrà rimosso dal codice.

10. Scegliere **Termina debug** dal menu **Debug**.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Connetti all'applicazione Windows Form per il debug
 È possibile connettere il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] a un processo in esecuzione. Se si usa un'edizione Express, questa funzionalità non è supportata.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Per connettersi all'applicazione Windows Form per il debug

1. Nel progetto creato in precedenza, fare clic sul margine sinistro per impostare un punto di interruzione in corrispondenza della riga aggiunta:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. Scegliere **Avvia senza eseguire debug** dal menu **Debug**.

     Windows Form viene avviato in Windows, come se fosse stato fatto doppio clic sul relativo eseguibile. Il debugger non è collegato.

3. Scegliere **Connetti a processo** dal menu **debug** . (Questo comando è disponibile anche nel menu **strumenti** ).

     Verrà visualizzata la finestra di dialogo **Connetti a processo** .

4. Nel riquadro **processi disponibili** trovare il nome del processo (Walkthrough_SimpleDebug.exe) nella colonna **processo** e fare clic su di esso.

5. Fare clic sul pulsante **Connetti** .

6. In Windows Form fare clic sul pulsante unico e solo.

     Il debugger interrompe l'esecuzione di Windows Form in corrispondenza del punto di interruzione.

## <a name="see-also"></a>Vedere anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)