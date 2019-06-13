---
title: Recupero di iniziare a compilare giochi con Unity in Visual Studio per Mac
description: Introduzione a Unity e Visual Studio per Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: 8f14d21468336dba220a76ad8978f136d50f96f1
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836160"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Recupero di iniziare a compilare giochi con Unity in Visual Studio per Mac 

Unity è un motore di gioco che abilita lo sviluppo di giochi in C#. Questa procedura dettagliata illustra come iniziare a usare lo sviluppo e debug di giochi Unity con Visual Studio per Mac e Visual Studio per Mac Tools per l'estensione di Unity con l'ambiente di Unity.

Visual Studio per Mac Tools per Unity è un'estensione gratuita, installata con Visual Studio per Mac. Consente agli sviluppatori di Unity di sfruttare le funzionalità di produttività di Visual Studio per Mac, incluso un supporto eccellente IntelliSense, debug, funzionalità e altro ancora.

## <a name="objectives"></a>Obiettivi

> [!div class="checklist"]
> * Informazioni sullo sviluppo di Unity con Visual Studio per Mac

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio per Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition o versione successiva ([https://store.unity.com](https://store.unity.com/), richiede un account unity.com per eseguire)

## <a name="intended-audience"></a>Destinatari

Questa esercitazione è destinata agli sviluppatori che hanno familiari con C#, anche se non è necessaria una vasta esperienza.

## <a name="task-1-creating-a-basic-unity-project"></a>Attività 1: Creazione di un progetto Unity base

1. Avvio veloce **Unity**. L'accesso se richiesto.

2. Fare clic su **Nuovo**.

    ![Pulsante nuovo in unity](media/unity-image1.png)

3. Impostare il **nome progetto** al **"UnityLab"** e selezionare **3D**. Fare clic su **Crea progetto**.

    ![Crea nuova schermata di progetto](media/unity-image2.png)

4. A questo punto stanno usando l'interfaccia di Unity predefinita. Ha la gerarchia della scena con gli oggetti gioco a sinistra, una vista 3D della scena vuota visualizzata al centro, un riquadro del file di progetto sulla parte inferiore e controllo e i servizi sul lato destro. Ovviamente è molto più a esso, ma questi sono alcuni dei componenti più importanti.

    ![interfaccia vuota unity](media/unity-image3.png)

5. Per gli sviluppatori di nuovi a Unity, tutto ciò che viene eseguito nell'app sarà presente all'interno del contesto di un **scena**. Un file della scena è un singolo file che contiene tutti i tipi di metadati sulle risorse utilizzato nel progetto per la scena corrente e le relative proprietà. Quando si crea un pacchetto dell'app per una piattaforma, finirà in corso una raccolta di uno o più scene, oltre a qualsiasi codice dipendente dalla piattaforma che si aggiunge l'app risultante. È possibile avere tanti scene come desiderato in un progetto.

6. La nuova scena include solo una fotocamera e una luce direzionale in esso. Una scena richiede un **fotocamera** per qualsiasi elemento sia visibile e un **Audio Listener** per tutti gli elementi a essere attivo. Questi componenti collegati a un **GameObject**.

7. Selezionare il **Main Camera** dell'oggetto dalle **gerarchia** riquadro.

    ![oggetto della fotocamera principale evidenziato nel riquadro di gerarchia](media/unity-image4.png)

8. Selezionare il **Inspector** riquadro a destra della finestra per visualizzare le relative proprietà. Proprietà della videocamera includono le informazioni di trasformazione, sfondo, tipo di proiezione, campo di visualizzazione e così via. Un componente Listener Audio è stato anche aggiunto per impostazione predefinita, che essenzialmente viene eseguito il rendering audio scena dal microfono virtuale collegato alla fotocamera.

    ![riquadro di controllo](media/unity-image5.png)

9. Selezionare il **Directional Light** oggetto. In questo modo la luce nella scena in modo che i componenti come gli shader sapere come eseguire il rendering di oggetti.

    ![Oggetto luce direzione evidenziato](media/unity-image6.png)

10. Usare la **Inspector** per vedere che include le proprietà di illuminazione comuni tra cui tipo di colore, intensità, tipo di ombreggiatura e così via.

    ![esaminano le proprietà nel riquadro di controllo](media/unity-image7.png)

11. È importante sottolineare che i progetti in Unity sono leggermente diversi da loro Visual Studio per le controparti Mac. Nel **Project** scheda nella parte inferiore destro del mouse sul **asset** cartella e selezionare **Visualizza in Finder**.

    ![Visualizza in azione contesto finder](media/unity-image8.png)

12. I progetti contengono **Assets**, **libreria**, **ProjectSettings**, e **Temp** cartelle come si possono vedere. Tuttavia, l'unico che viene visualizzato nell'interfaccia è il **asset** cartella. Il **libreria** cartella è la cache locale per le risorse importate; contiene tutti i metadati per gli asset. Il **ProjectSettings** cartella archivia le impostazioni configurabili. Il **Temp** cartella viene usata per i file temporanei da Mono e Unity durante il processo di compilazione. È anche presente un file di soluzione che è possibile aprire in Visual Studio per Mac (**UnityLab.sln** qui).

    ![Asset in finder](media/unity-image9.png)

13. Chiudi il **Finder** finestra e tornare alla **Unity**.

14. Il **asset** cartella contiene tutte le aggiornati gli asset di codice, audio, e così via. È vuoto a questo punto, ma spazio per ogni singolo file inseriti in al progetto. Questo valore è sempre la cartella di livello principale le **Editor di Unity**. Ma sempre aggiungere e rimuovere i file tramite l'interfaccia di Unity (o Visual Studio per Mac) e mai tramite il file system direttamente.

    ![cartella Assets in unity](media/unity-image10.png)

15. Il **GameObject** è fondamentale per lo sviluppo in Unity come quasi tutto ciò che deriva da tale tipo, inclusi modelli, luci, sistemi particellari e così via. Aggiungere un nuovo **cubo** oggetto alla scena tramite il **GameObject > oggetto 3D > cubo** menu.

    ![oggetto del cubo nella scena](media/unity-image11.png)

16. Esaminare rapidamente le proprietà della nuova **GameObject** e in cui è presente un nome, tag, livello e trasformazione. Queste proprietà sono comuni a tutti **Gameobject**. Inoltre, sono stati collegati diversi componenti per il **cubo** fornire necessarie funzionalità, compresi mesh filtro collider casella e renderer.

    ![proprietà dell'oggetto gioco](media/unity-image12.png)

17. Rinominare il **cubo** object, che contiene il nome **"Cube"** per impostazione predefinita, alla **"Nemico"** . Assicurarsi di premere **invio** per salvare le modifiche. Questo sarà il cubo avversario nel nostro semplice gioco.

    ![proprietà di ridenominazione dell'oggetto cubo](media/unity-image13.png)

18. Aggiungere un'altra **cubo** oggetti nella scena con lo stesso processo come illustrato in precedenza e denominare il presente **"Player"** .

    ![rinominare l'oggetto cubo secondo](media/unity-image14.png)

19. Contrassegnare l'oggetto player **"Player"** nonché (vedere **Tag** controllo elenco a discesa sotto il campo nome). Useremo nello script avversario in modo da individuare l'oggetto gioco Windows Media player.

    ![l'oggetto player l'assegnazione di tag](media/unity-image15.png)

20. Nel **scena** visualizzare, spostare l'oggetto player lontano dall'avversario oggetto lungo l'asse Z usando il mouse. È possibile spostare lungo l'asse Z selezionando e trascinando il cubo dal relativo **rossa** pannello verso il **blu** riga. Poiché il cubo si trova nello spazio 3D, ma può solo essere trascinato in 2D ogni volta, l'asse in cui si trascina è particolarmente importante.

    ![cubo di che Mostra visualizzazione scena](media/unity-image16.png)

21. Spostare il cubo verso il basso e a destra lungo l'asse. Questo modo viene aggiornato il **Position** proprietà nel **Inspector**. Assicurarsi di trascinare in una posizione in modo analogo a ciò che è illustrato di seguito per semplificare i passaggi successivi nel lab.

    ![lo spostamento di un cubo lungo l'asse](media/unity-image17.png)

22. A questo punto è possibile aggiungere codice per guidare l'avversario per la logica in modo che essa attuate Windows Media player. Fare doppio clic sul **asset** cartella nel **Project** riempire e scegliere **Crea > C# Script**.

    ![C#azione contesto script](media/unity-image18.png)

23. Denominare il nuovo C# script **"EnemyAI"** .

    ![Negli script c#](media/unity-image19.png)

24. Per collegare gli script per gli oggetti gioco trascinare lo script appena creato nel **nemico** dell'oggetto nel **gerarchia** riquadro. Tale oggetto verrà ora usare comportamenti da questo script.

    ![evidenziazione dei risultati che mostra l'aggiunta di script per oggetto gioco](media/unity-image20.png)

25. Selezionare **File > Salva scene** salvare nella scena corrente. Denominarlo **"MyScene"** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Attività 2: Uso di Visual Studio per Mac Tools per Unity

1. Il modo migliore per modificare C# codice consiste nell'usare Visual Studio per Mac. È possibile configurare Unity per usare Visual Studio per Mac come il gestore predefinito. Selezionare **Unity > Preferenze**.

2. Selezionare il **strumenti esterni** scheda. Dal **External Script Editor** elenco a discesa, seleziona **Sfoglia** e selezionare **/Applications applicazioni/Visual**. In alternativa, se è già presente una **Visual Studio** opzione, selezionarla semplicemente.

    ![scheda Strumenti esterni nelle preferenze](media/unity-image21.png)

3. Unity è ora configurato per utilizzare **Visual Studio per Mac** per la modifica dello script. Chiudi il **Unity Preferences** finestra di dialogo.

    ![Visual Studio selezionata nelle preferenze](media/unity-image22.png)

4. Fare doppio clic su **EnemyAI.cs** per aprirlo nella **Visual Studio per Mac**.

    ![Avversario asset selezionati in unity](media/unity-image23.png)

5. La soluzione di Visual Studio è semplice. Contiene un' **Assets** cartella (uguale a quello da **Finder**) e il **EnemyAI.cs** script creato in precedenza. Nei progetti più sofisticati, la gerarchia avrà probabilmente un aspetto diversa rispetto a ciò che viene visualizzato in Unity.

    ![Riquadro della soluzione in Visual Studio per Mac](media/unity-image24.png)

6. **EnemyAI.cs** viene aperto nell'editor. Lo script iniziale contiene solo gli stub per il **avviare** e **Update** metodi.

7. Sostituire il codice di avversario iniziale con il codice seguente.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;
        
        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Esaminare rapidamente il comportamento di avversario semplice che viene definito qui. Nel **avviare** metodo, si ottiene un riferimento all'oggetto player (in base al tag), e i relativi **trasformare**. Nel **Update** metodo, che viene chiamato per ogni fotogramma, il vostro nemico verrà spostata verso l'oggetto player. Le parole chiave e i nomi di usano una codifica a colori per renderlo più facile da comprendere la codebase in Visual Studio per Mac.

9. Salvare le modifiche allo script avversario **Visual Studio per Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Attività 3: Debug del progetto Unity

1. Impostare un punto di interruzione sulla prima riga di codice nel **avviare** (metodo). È possibile scegliere il margine dell'editor in corrispondenza del cursore di riga o posizione di destinazione sulla riga e premere **F9**.

    ![impostazione punto di interruzione in visual studio per mac](media/unity-image25.png)

2. Scegliere il **Avvia debug** o preme **F5**. Verrà compilare il progetto e collegarlo a Unity per eseguire il debug.

    ![pulsante di avvio in visual studio per mac](media/unity-image26.png)

3. Tornare alla **Unity** e fare clic sui **eseguire** per avviare il gioco.

    ![pulsante Esegui in unity](media/unity-image27.png)

4. Il punto di interruzione verrà raggiunto ed è ora possibile usare Visual Studio per Mac tools debug.

    ![punto di interruzione raggiunto in visual studio per mac](media/unity-image28.png)

5. Dal **variabili locali** riempimento, individuare il **ciò** puntatore, che fa riferimento a un **EnemyAI** oggetto. Espandere il riferimento e vedere che è possibile esplorare i membri associati, ad esempio **velocità**.

    ![variabili locali debug pad in visual studio per mac](media/unity-image29.png)

6. Rimuovere il punto di interruzione dal **avviare** metodo simile a quello è stato aggiunto-da clic su di esso nel margine o selezionare la riga e premere **F9**.

    ![punto di interruzione raggiunto in visual studio per mac](media/unity-image30.png)

7. Premere **F10** per passare alla prima riga di codice che consente di trovare il **Player** oggetto gioco usando un tag come parametro.

8. Spostare il cursore del mouse sul **player** variabile all'interno della finestra dell'editor di codice e visualizzarne i membri associati. È anche possibile espandere la sovrimpressione per visualizzare le proprietà figlio.

    ![finestra di debug in visual studio per l'editor di mac](media/unity-image31.png)

9. Premere **F5** oppure premere la **eseguire** pulsante per continuare l'esecuzione. Tornare a Unity per visualizzare il cubo avversario approccio ripetutamente il cubo di Windows Media player. Potrebbe essere necessario modificare l'impostazione della fotocamera se non è visibile.

    ![scena assegnatario in unity](media/unity-image32.png)

10. Tornare alla **Visual Studio per Mac** e impostare un punto di interruzione sulla prima riga del **Update** (metodo). Che deve essere raggiunto immediatamente.

    ![l'impostazione di un punto di interruzione in visual studio per mac](media/unity-image33.png)

11. Si supponga che la velocità è troppo veloce e si vuole testare l'impatto della modifica senza riavviare l'app. Individuare il **velocità** variabile all'interno di **Auto** o **variabili locali** finestra e quindi modificarlo come segue **"10"** e premere **invio** .

    ![Modifica le variabili nella finestra variabili locali](media/unity-image34.png)

12. Rimuovere il punto di interruzione e premere **F5** per riprendere l'esecuzione.

13. Tornare alla **Unity** per visualizzare l'applicazione in esecuzione. Il cubo avversario sta trasferendo a un quinto della velocità originale.

    ![finestra di Unity con l'esecuzione dell'applicazione](media/unity-image35.png)

14. Arrestare l'app Unity facendo il **riprodurre** nuovamente clic sul pulsante.

    ![l'arresto dell'app unity](media/unity-image36.png)

15. Tornare alla **Visual Studio per Mac**. Arrestare la sessione di debug facendo il **arrestare** pulsante.

    ![arrestare la sessione di debug in Visual Studio per Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Attività 4: Esplorazione delle funzionalità di Unity in Visual Studio per Mac

1. Visual Studio per Mac consente di accedere rapidamente alla documentazione di Unity all'interno dell'editor di codice. Posizionare il cursore in un punto nel **Vector3** simbolo all'interno del **Update** metodo e premere **⌘ comando + '** .

    ![Selezione metodo di visual Studio per l'editor di mac](media/unity-image38.png)

2. Una nuova finestra del browser si apre la documentazione per **Vector3**. Chiudere la finestra del browser quando è soddisfatta.

    ![verrà visualizzata la finestra del browser alla documentazione](media/unity-image39.png)

3. Visual Studio per Mac offre anche alcuni helper per creare rapidamente le classi di comportamento di Unity. Dal **Esplora soluzioni**, fare doppio clic su **Assets** e selezionare **Aggiungi > Nuovo MonoBehaviour**.

    ![nuova azione di contesto monobehaviour](media/unity-image40.png)

4. La classe appena creata fornisce gli stub per il **avviare** e **Update** metodi. Dopo la parentesi graffa di chiusura del **Update** metodo, iniziare a digitare **"onmouseup"** . Durante la digitazione, si noti che IntelliSense di Visual Studio zeri rapidamente in sul metodo che si intende implementare. Selezionarlo dall'elenco di completamento automatico fornito. Compileranno uno stub del metodo per l'utente, inclusi gli eventuali parametri.

    ![IntelliSense in visual studio per mac](media/unity-image41.png)

5. All'interno di **OnMouseUp** metodo, tipo **"base".** Per visualizzare tutti i metodi di base disponibili da chiamare. È anche possibile esplorare i diversi overload di ogni funzione utilizzando l'opzione di paging nell'angolo in alto a destra del riquadro a comparsa IntelliSense.

    ![esplorazione di overload in visual studio per mac](media/unity-image42.png)

6. Visual Studio per Mac consente inoltre di definire con facilità nuovo shader. Dal **Esplora soluzioni**, fare doppio clic su **Assets** e selezionare **Aggiungi > Nuovo Shader**.

    ![nuova azione di shader in visual studio per mac](media/unity-image43.png)

7. Il formato del file shader Ottiene tutti i colori e il trattamento di tipo di carattere per renderne più semplice da leggere e comprendere.

    ![L'evidenziazione della sintassi](media/unity-image44.png)

8. Tornare alla **Unity**. Si noterà che poiché Visual Studio per Mac funziona con lo stesso sistema di progetto, le modifiche apportate in entrambe le posizioni vengono sincronizzate automaticamente con l'altro. Ora è facile da utilizzare sempre lo strumento migliore per l'attività.

    ![Pannello asset Unity](media/unity-image45.png)

## <a name="summary"></a>Riepilogo

In questo laboratorio, si è appreso come iniziare a creare un gioco con Unity e Visual Studio per Mac. Visualizzare [ https://unity3d.com/learn ](https://unity3d.com/learn) per altre informazioni su Unity.
