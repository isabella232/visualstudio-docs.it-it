---
title: 'Procedura dettagliata: debug di un Windows Form | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a553f77e352b16ba1a0709e13e8893cf0f57a43d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704905"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procedura dettagliata: Debug di un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Form è una delle più comuni applicazioni gestite. Un Windows Form crea un'applicazione Windows standard. È possibile completare questa procedura dettagliata utilizzando Visual Basic, C# o C++.  
  
 Prima di tutto, è necessario chiudere tutte le soluzioni aperte.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Operazioni preliminari per la procedura dettagliata  
  
- Se è già aperta una soluzione aperta, chiuderla. Scegliere **Chiudi soluzione**dal menu **file** .  
  
## <a name="create-a-new-windows-form"></a>Creare un nuovo Windows Form  
 Successivamente, verrà creato un nuovo Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Per creare il Windows Form per questa procedura dettagliata  
  
1. Scegliere **nuovo** dal menu **file** e fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2. Nel riquadro Tipi progetto aprire il nodo **Visual Basic**, **Visual C#** o **Visual C++** , quindi  
  
    1. Per Visual Basic o Visual C#, selezionare il nodo **Windows** , quindi selezionare **applicazione Windows Form** nel riquadro **modelli** .  
  
    2. Per Visual C++, selezionare il nodo **CLR** , quindi selezionare **applicazione Windows Form** nel riquadro **modelli** .  
  
3. Nel riquadro **Modelli** selezionare **Applicazione Windows**.  
  
4. Nella casella **nome** assegnare al progetto un nome univoco, ad esempio Walkthrough_SimpleDebug.  
  
5. Fare clic su **OK**.  
  
     Visual Studio crea un nuovo progetto e visualizza un nuovo modulo nella finestra di progettazione Windows Forms. Per ulteriori informazioni, vedere [Progettazione Windows Form](https://msdn.microsoft.com/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6. Scegliere **casella degli strumenti**dal menu **Visualizza** .  
  
     Verrà visualizzata la casella degli strumenti. Per altre informazioni, vedere [Casella degli strumenti](../ide/reference/toolbox.md).  
  
7. Nella casella degli strumenti fare clic sul controllo **Button** e trascinare il controllo nell'area di progettazione del form. Rilasciare il pulsante nel form.  
  
8. Nella casella degli strumenti fare clic sul controllo **TextBox** e trascinare il controllo nell'area di progettazione del form. Rilasciare la **casella di testo** nel form.  
  
9. Nell'area di progettazione del form fare doppio clic sul pulsante.  
  
     Verrà quindi riportata la tabella codici. Il cursore deve essere in `button1_Click` .  
  
10. Nella funzione `button1_Click`. aggiungere il codice seguente:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il progetto dovrebbe essere compilato senza errori.  
  
## <a name="debug-your-form"></a>Eseguire il debug del modulo  
 A questo punto si è pronti per iniziare il debug.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Per eseguire il debug del Windows Form creato per questa procedura dettagliata  
  
1. Nella finestra di origine fare clic sul margine sinistro sulla stessa riga del testo aggiunto:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso. Il punto di colore rosso rappresenta un punto di interruzione. Per altre informazioni, vedere [Punti di interruzione](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta. Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug.  
  
    > [!NOTE]
    > È anche possibile fare clic con il pulsante destro del mouse su una qualsiasi riga di codice, scegliere punto di **interruzione**, quindi fare clic su Inserisci punto di **interruzione** per aggiungere un punto di interruzione nella riga.  
  
2. Scegliere **Avvia**dal menu **debug** .  
  
     Viene avviata l'esecuzione di Windows Form.  
  
3. In Windows Form fare clic sul pulsante aggiunto.  
  
     In Visual Studio si passa alla riga in cui è stato impostato il punto di interruzione nella tabella codici. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. È stata arrestata l'esecuzione dell'applicazione, in attesa di un'azione da te.  
  
4. Scegliere **finestre**dal menu **debug** , quindi **guardare**e fare clic su **controllo1**.  
  
5. Nella finestra **controllo1** fare clic su una riga vuota. Nella colonna **nome** Digitare `textBox1.Text` (se si utilizza Visual Basic, Visual C# o J#) o `textBox1->Text` (se si utilizza C++), quindi premere INVIO.  
  
     La finestra **controllo1** Mostra il valore di questa variabile tra virgolette come:  
  
    ```  
    ""  
    ```  
  
6. Scegliere **Esegui istruzione** dal menu **Debug**.  
  
     Il valore di textBox1. Text viene modificato nella finestra **controllo1** per:  
  
    ```  
    Button was clicked!  
    ```  
  
7. Scegliere **continua** dal menu **debug** per riprendere il debug del programma.  
  
8. Nel Windows Form, fare di nuovo clic sul pulsante.  
  
     Visual Studio interrompe di nuovo l'esecuzione.  
  
9. Fare clic sul punto rosso che rappresenta il punto di interruzione.  
  
     Il punto di interruzione verrà rimosso dal codice.  
  
10. Scegliere **Termina debug** dal menu **Debug**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Connetti all'applicazione Windows Form per il debug  
 È possibile connettere il debugger di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] a un processo in esecuzione. Se si usa un'edizione Express, questa funzionalità non è supportata.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Per connettersi all'applicazione Windows Form per il debug  
  
1. Nel progetto creato in precedenza, fare clic sul margine sinistro per impostare un punto di interruzione in corrispondenza della riga aggiunta:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2. Scegliere **Avvia senza eseguire debug** dal menu **Debug**.  
  
     Windows Form viene avviato in Windows, come se fosse stato fatto doppio clic sul relativo eseguibile. Il debugger non è collegato.  
  
3. Scegliere **Connetti a processo**dal menu **debug** . (Questo comando è disponibile anche nel menu **strumenti** ).  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo** .  
  
4. Nel riquadro **processi disponibili** trovare il nome del processo (Walkthrough_SimpleDebug.exe) nella colonna **processo** e fare clic su di esso.  
  
5. Fare clic sul pulsante **Connetti** .  
  
6. In Windows Form fare clic sul pulsante unico e solo.  
  
     Il debugger interrompe l'esecuzione di Windows Form in corrispondenza del punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)
