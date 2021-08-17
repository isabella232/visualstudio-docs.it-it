---
title: Sviluppo di test first con Generate From Usage (Genera dall'utilizzo)
description: Informazioni su come incorporare l'approccio di sviluppo Test-first tramite l'uso della funzionalità Genera dall'utilizzo.
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4cd2dd9610167197a8deaa1bdc88d4e5689636e75263785d92618eceee37f3bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398484"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Procedura dettagliata: Sviluppo di test preventivi con la funzionalità di generazione dall'utilizzo

Questo argomento illustra come usare la funzionalità [Generate From Usage](../ide/visual-csharp-intellisense.md#generate-from-usage) , che supporta lo sviluppo di test preventivi.

 Lo *sviluppo di test preventivi* è un approccio alla progettazione software in cui prima si scrivono unit test in base alle specifiche del prodotto e quindi si scrive il codice sorgente necessario per fare in modo che i test abbiano esito positivo. Visual Studio supporta lo sviluppo di test preventivi grazie alla generazione di nuovi tipi e membri nel codice sorgente quando si fa riferimento a essi per la prima volta nei test case, prima che vengano definiti.

Visual Studio genera i nuovi tipi e membri con un'interruzione minima del flusso di lavoro. È possibile creare stub per tipi, metodi, proprietà, campi o costruttori senza abbandonare la posizione corrente nel codice. Quando si apre una finestra di dialogo per specificare le opzioni per la generazione dei tipi, lo stato attivo torna immediatamente al file aperto corrente quando si chiude la finestra di dialogo.

La funzionalità di **generazione dall'uso** può essere usata con framework di test che si integrano con Visual Studio. In questo argomento viene illustrato il framework di unit test Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Creare un progetto di libreria di classi Windows e un progetto di test

1. In C# o Visual Basic creare un nuovo progetto di **Libreria di classi Windows**. Assegnare al progetto il nome `GFUDemo_VB` o `GFUDemo_CS`, a seconda del linguaggio in uso.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sull'icona in alto, scegliere **Aggiungi** > **Nuovo progetto**.

3. Creare un nuovo progetto **Progetto unit test (.NET Framework)**.

   ::: moniker range="vs-2017"

   La figura seguente illustra la finestra di dialogo **Nuovo progetto** per modelli C#.

   ![Modello Progetto unit test](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Aggiungere un riferimento al progetto di libreria di classi

1. Nel progetto di unit test in **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla voce **Riferimenti** e scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Gestione riferimenti** selezionare **Progetti** e scegliere un progetto di libreria di classi.

3. Scegliere **OK** per chiudere la finestra di dialogo **Gestione riferimenti**.

4. Salvare la soluzione. A questo punto, è possibile iniziare a scrivere test.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generare una nuova classe da uno unit test

1. Il progetto di test contiene un file denominato *UnitTest1*. Fare doppio clic su questo file **Esplora soluzioni** per aprirlo nell'editor di codice. Vengono generati una classe di test e un metodo di test.

2. Individuare la dichiarazione della classe `UnitTest1` e rinominarla in `AutomobileTest`.

   > [!NOTE]
   > IntelliSense offre ora due alternative per il completamento delle istruzioni IntelliSense: la *modalità di terminazione* e la *modalità con suggerimenti*. Usare la modalità con suggerimenti per i casi in cui classi e membri vengono usati prima di essere definiti. Quando una finestra di **IntelliSense** è aperta, è possibile premere **CTRL**+**ALT**+**BARRA SPAZIATRICE** per passare dalla modalità di terminazione alla modalità con suggerimenti e viceversa. Per altre informazioni, vedere [Usare IntelliSense](../ide/using-intellisense.md). La modalità con suggerimenti sarà utile quando si digita `Automobile` nel passaggio successivo.

3. Individuare il metodo `TestMethod1()` e rinominarlo in `DefaultAutomobileIsInitializedCorrectly()`. All'interno di questo metodo creare una nuova istanza di una classe denominata `Automobile`, come illustrato negli screenshot seguenti. Vengono visualizzate una sottolineatura ondulata che indica un errore in fase di compilazione e una lampadina di errore [Azioni rapide](../ide/quick-actions.md) nel margine a sinistra o direttamente sotto la sottolineatura a zigzag se si passa il puntatore del mouse.

    ![Azioni rapide in Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Azioni rapide in C&#35;](../ide/media/genclass_underline.png)

4. Scegliere o fare clic sulla lampadina **Azioni rapide**. Verrà visualizzato un messaggio di errore a indicare che il tipo `Automobile` non è definito. Vengono anche proposte alcune soluzioni.

5. Fare clic su **Genera nuovo tipo** per aprire la finestra di dialogo **Genera tipo**. Questa finestra di dialogo contiene alcune opzioni, tra cui la possibilità di generare il tipo in un progetto diverso.

6. Nell'elenco **Progetto** fare clic su **GFUDemo\_VB** o **GFUDemo_CS** per indicare a Visual Studio di aggiungere il file al progetto di libreria di classi invece che al progetto di test. Se non è già selezionata, scegliere l'opzione **Crea nuovo file** e denominare il file *Automobile.cs* o *Automobile.vb*.

     ![Finestra di dialogo Genera nuovo tipo](../ide/media/genotherdialog.png)

7. Fare clic su **OK** per chiudere la finestra di dialogo e creare il nuovo file.

8. In **Esplora soluzioni**, esaminare il nodo del progetto **GFUDemo_VB** o **GFUDemo_CS** per verificare che il nuovo file *Automobile.vb* o *Automobile.cs* sia presente. Nell'editor del codice lo stato attivo è ancora in `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. È quindi possibile continuare a scrivere il test con un'interruzione minima.

### <a name="generate-a-property-stub"></a>Generare uno stub per una proprietà
Si supponga che la specifica del prodotto indichi che la classe `Automobile` ha due proprietà pubbliche denominate `Model` e `TopSpeed`. Queste proprietà devono essere inizializzate con i valori predefiniti `"Not specified"` e `-1` dal costruttore predefinito. Lo unit test seguente verificherà che il costruttore predefinito imposti le proprietà sui valori predefiniti corretti.

1. Aggiungere la riga di codice seguente al metodo di test di `DefaultAutomobileIsInitializedCorrectly`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet1":::

2. Poiché il codice fa riferimento a due proprietà non definite in `Automobile`, viene visualizzata una sottolineatura ondulata sotto `Model` e `TopSpeed`. Passare il puntatore del mouse su `Model`, scegliere la lampadina di errore **Azioni rapide** e quindi l'opzione **Genera proprietà 'Automobile.Model'**.

3. Generare uno stub per la proprietà `TopSpeed` nello stesso modo.

     Nella classe `Automobile` i tipi delle nuove proprietà vengono dedotti correttamente dal contesto.

### <a name="generate-a-stub-for-a-new-constructor"></a>Generare uno stub per un nuovo costruttore
A questo punto viene creato un metodo di test che genererà uno stub per il costruttore per inizializzare le proprietà `Model` e `TopSpeed`. Successivamente, verrà aggiunto altro codice per completare il test.

1. Aggiungere l'ulteriore metodo di test seguente alla classe `AutomobileTest` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb" id="Snippet2":::

2. Fare clic sulla lampadina di errore **Azioni rapide** sotto la sottolineatura rossa a zigzag e selezionare **Genera costruttore in 'Automobile'**.

     Nel file della classe `Automobile` osservare che il nuovo costruttore ha esaminato i nomi delle variabili locali che vengono usati nella chiamata al costruttore, ha trovato le proprietà che hanno gli stessi nomi nella classe `Automobile` e ha fornito il codice nel corpo del costruttore per archiviare i valori degli argomenti nelle proprietà `Model` e `TopSpeed` .

3. Dopo aver generato il nuovo costruttore, viene visualizzata una sottolineatura ondulata sotto la chiamata al costruttore predefinito in `DefaultAutomobileIsInitializedCorrectly`. Il messaggio di errore indica che la classe `Automobile` non ha un costruttore che accetta zero argomenti. Per generare un costruttore predefinito esplicito che non ha parametri, fare clic sulla lampadina di errore **Azioni rapide** e quindi su **Genera costruttore in 'Automobile'**.

### <a name="generate-a-stub-for-a-method"></a>Generare uno stub per un metodo
Si supponga che la specifica indichi che un nuovo oggetto `Automobile` può essere impostato in uno stato `IsRunning` se le sue proprietà `Model` e `TopSpeed` sono impostate su valori diversi da quelli predefiniti.

1. Aggiungere le righe seguenti al metodo `AutomobileWithModelNameCanStart` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet3":::

2. Fare clic sulla lampadina di errore **Azioni rapide** per la chiamata al metodo `myAuto.Start` e quindi su **Genera metodo 'Automobile.Start'**.

3. Fare clic sulla lampadina **Azioni rapide** per la proprietà `IsRunning` e quindi su **Genera proprietà 'Automobile.IsRunning'**.

     La classe `Automobile` ora contiene un metodo denominato `Start()` e una proprietà denominata `IsRunning`.

### <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Esegui** > **Tutti i test**.

     Il **comando** Esegui tutti i test esegue tutti i test in tutti i framework di test scritti per la soluzione  >   corrente. In questo caso ci sono due test e hanno entrambi esito negativo, come previsto. Il test `DefaultAutomobileIsInitializedCorrectly` ha esito negativo perché la condizione `Assert.IsTrue` restituisce `False`. Il test `AutomobileWithModelNameCanStart` ha esito negativo perché il metodo `Start` nella classe `Automobile` genera un'eccezione.

     La finestra **Risultati test** è illustrata nella figura seguente.

     ![Risultati dei test non riusciti](../ide/media/testsfailed.png)

2. Nella finestra **Risultati del test** fare doppio clic su ogni riga dei risultati del test per passare alla posizione di ogni test.

### <a name="implement-the-source-code"></a>Implementare il codice sorgente

1. Aggiungere il codice seguente al costruttore predefinito in modo che le proprietà `Model`, `TopSpeed` e `IsRunning` vengano tutte inizializzate con i valori predefiniti corretti, ovvero `"Not specified"`, `-1`e `False` (o `false` per C#).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet5":::

2. Quando il metodo `Start` viene chiamato, deve impostare il flag `IsRunning` su true solo se la proprietà `Model` o `TopSpeed` è impostata su un valore diverso da quello predefinito. Rimuovere `NotImplementedException` dal corpo del metodo e aggiungere il codice seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet6":::

### <a name="run-the-tests-again"></a>Eseguire di nuovo i test

- Scegliere **Esegui** dal menu **Test** e fare clic su **Tutti i test**.

     Questa volta il test ha esito positivo. La finestra **Risultati test** è illustrata nella figura seguente.

     ![Risultati dei test riusciti](../ide/media/testspassed.png)

## <a name="see-also"></a>Vedi anche

- [Generare dall'utilizzo](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Usare IntelliSense](../ide/using-intellisense.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Azioni rapide](../ide/quick-actions.md)
