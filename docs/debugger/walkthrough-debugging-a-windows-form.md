---
title: Debug di un Windows form | Microsoft Docs
description: Seguire una procedura dettagliata per vedere come creare ed eseguire il debug di Windows form, un'applicazione gestita comune. È possibile usare C#, Visual Basic, C++ o F#.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6790cd24bb6b4f927029ab7749e35acd1d756c24
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051794"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procedura dettagliata: Debug di un Windows Form
Un Windows form è una delle applicazioni gestite più comuni. Un form Windows crea un'applicazione Windows standard. È possibile completare questa procedura dettagliata usando Visual Basic, C# o C++.

 Prima di tutto, è necessario chiudere tutte le soluzioni aperte.

### <a name="to-prepare-for-this-walkthrough"></a>Operazioni preliminari per la procedura dettagliata

- Se è già aperta una soluzione aperta, chiuderla. Scegliere Chiudi soluzione dal menu **File.**

## <a name="create-a-new-windows-form"></a>Creare un nuovo Windows Form
 Successivamente, si creerà un nuovo Windows form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Per creare il modulo Windows per questa procedura dettagliata

1. Scegliere **Nuovo** dal menu File **e fare** clic su **Project**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Nel riquadro Project tipi aprire il **Visual Basic**, **Visual C#** **o Visual C++,** quindi

    1. Per Visual Basic o Visual C#, selezionare **Windows Desktop**  >  **Windows Form App**.

    2. Per Visual C++, selezionare **Windows Desktop.**

3. Nella casella **Nome** assegnare al progetto un nome univoco, ad esempio Walkthrough_SimpleDebug.

4. Fare clic su **OK**.

     Visual Studio crea un nuovo progetto e visualizza un nuovo form nella finestra di progettazione Windows Form. Per altre informazioni, vedere Windows [Forms Designer](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. Scegliere **Casella degli** **strumenti** dal menu Visualizza .

     Verrà visualizzata la casella degli strumenti. Per altre informazioni, vedere [Casella degli strumenti](../ide/reference/toolbox.md).

6. Nella casella degli strumenti fare clic sul **controllo Pulsante** e trascinare il controllo nell'area di progettazione Form. Rilasciare il pulsante nel form.

7. Nella casella degli strumenti fare clic sul **controllo TextBox** e trascinare il controllo nell'area di progettazione Form. Rilasciare **il controllo TextBox** nel form.

8. Nell'area di progettazione del form fare doppio clic sul pulsante.

     Verrà visualizzata la tabella codici. Il cursore deve essere in `button1_Click` .

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
 A questo punto, è possibile iniziare il debug.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Per eseguire il debug Windows form creato per questa procedura dettagliata

1. Nella finestra di origine fare clic sul margine sinistro nella stessa riga del testo aggiunto:

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
    > È anche possibile fare clic con il pulsante destro  del mouse su qualsiasi riga di codice, scegliere Punto di interruzione **e** quindi fare clic su Inserisci punto di interruzione per aggiungere un punto di interruzione in tale riga.

2. Scegliere **Avvia** dal menu **Debug.**

     Viene avviata Windows form di avvio.

3. Nel modulo Windows fare clic sul pulsante aggiunto.

     In Visual Studio viene visualizzata la riga in cui è stato impostato il punto di interruzione nella tabella codici. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. L'esecuzione dell'applicazione è stata interrotta, in attesa di un'azione da parte dell'utente.

4. Nel menu **Debug** scegliere Windows **,** quindi Espressioni di **controllo** e fare clic su Espressioni **di controllo1**.

5. Nella finestra **Espressioni di controllo1** fare clic su una riga vuota. Nella **colonna Nome** digitare (se si usa Visual Basic o Visual C#) o (se si usa `textBox1.Text` `textBox1->Text` C++), quindi premere INVIO.

     La **finestra Espressioni di controllo1** mostra il valore di questa variabile tra virgolette come segue:

    `""`

6. Scegliere **Esegui istruzione** dal menu **Debug**.

     Il valore di textBox1.Text cambia nella **finestra Watch1** in:

    `Button was clicked!`

7. Scegliere **Continua dal** menu Debug **per** riprendere il debug del programma.

8. Nel modulo Windows fare di nuovo clic sul pulsante.

     Visual Studio interrompe nuovamente l'esecuzione.

9. Fare clic sul punto rosso che rappresenta il punto di interruzione.

     Il punto di interruzione viene rimosso dal codice.

10. Scegliere **Termina debug** dal menu **Debug**.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Connettersi all'applicazione Windows form per il debug
 È possibile connettere il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] a un processo in esecuzione. Se si usa un'edizione Express, questa funzionalità non è supportata.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Per connettersi all'applicazione Windows form per il debug

1. Nel progetto creato in precedenza fare clic sul margine sinistro per impostare ancora una volta un punto di interruzione nella riga aggiunta:

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

     Il Windows form viene avviato in Windows, come se si fosse fatto doppio clic sul relativo eseguibile. Il debugger non è collegato.

3. Scegliere **Associa** a processo dal menu **Debug**. Questo comando è disponibile anche **nel** menu Strumenti.

     Verrà visualizzata la finestra di dialogo **Connetti a processo** .

4. Nel riquadro **Processi disponibili individuare** il nome del processo (Walkthrough_SimpleDebug.exe) nella colonna **Processo** e fare clic su di esso.

5. Fare clic **sul pulsante** Collega.

6. Nel modulo Windows fare clic sull'unico pulsante.

     Il debugger interrompe l'esecuzione del form Windows in corrispondenza del punto di interruzione.

## <a name="see-also"></a>Vedi anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)