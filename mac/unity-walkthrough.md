---
title: Introduzione alla creazione di giochi con Unity
description: Introduzione all'uso di Unity e Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: 02cfb49a223d927dd8228bb961f2036fe59c050fe5492c4ee2e0e5538e86e931
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121382847"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Introduzione alla creazione di giochi con Unity in Visual Studio per Mac

Unity è un motore per giochi che consente di sviluppare giochi in C#. Questa procedura dettagliata illustra come iniziare a sviluppare giochi con Unity ed eseguirne il debug con Visual Studio per Mac e l'estensione Visual Studio for Mac Tools for Unity in parallelo con l'ambiente Unity.

Visual Studio for Mac Tools for Unity è un'estensione gratuita, installata con Visual Studio per Mac. Consente agli sviluppatori di Unity di sfruttare le funzionalità per la produttività di Visual Studio per Mac, come il supporto efficiente di IntelliSense, funzionalità di debug e altro ancora.

## <a name="objectives"></a>Obiettivi

> [!div class="checklist"]
> * Apprendere le nozioni di base per lo sviluppo di giochi Unity con Visual Studio per Mac

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio per Mac ( [https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac) )
- Unity 5.6.1 Personal Edition o versione successiva ( , richiede un [https://store.unity.com](https://store.unity.com/) account unity.com per l'esecuzione)

## <a name="intended-audience"></a>Destinatari

Questo lab è destinato agli sviluppatori che hanno familiarità con C#, anche se non è necessaria una vasta esperienza.

## <a name="task-1-creating-a-basic-unity-project"></a>Attività 1: Creazione di un progetto Unity di base

1. Avviare **Unity**. Eseguire l'accesso, se richiesto.

2. Fare clic su **Nuovo**.

    ![pulsante per la creazione di un nuovo progetto in Unity](media/unity-image1.png)

3. Impostare **Project name** (Nome progetto) su **"UnityLab"** e selezionare **3D**. Fare clic su **Crea progetto**.

    ![schermata per la creazione di nuovo progetto](media/unity-image2.png)

4. Viene visualizzata l'interfaccia predefinita di Unity. L'interfaccia visualizzata include la gerarchia della scena con gli oggetti gioco a sinistra, una vista 3D della scena vuota al centro, un riquadro dei file di progetto in basso e i riquadri di controllo e dei servizi a destra. Ovviamente sono disponibili molte altre funzionalità, ma questi sono alcuni dei componenti più importanti.

    ![interfaccia di Unity vuota](media/unity-image3.png)

5. Per gli sviluppatori che non conoscono Unity, è opportuno sottolineare che tutte le operazioni eseguite nell'app sono incluse nel contesto di una **scena**. In un singolo file di scena sono contenuti tutti i tipi di metadati relativi alle risorse usate nel progetto per la scena corrente e le relative proprietà. Quando si crea un pacchetto dell'app per una piattaforma, l'app risultante consiste in una raccolta di una o più scene, con in più l'eventuale codice dipendente dalla piattaforma aggiunto. In un progetto è possibile inserire il numero di scene desiderato.

6. La nuova scena include una videocamera e una luce di direzione. Una scena richiede una **videocamera** per rendere visibili gli oggetti e un **dispositivo di ascolto** per consentire la riproduzione dell'audio. Questi componenti sono collegati a un **GameObject**.

7. Selezionare l'oggetto **Main Camera** (Videocamera principale) dal riquadro **Hierarchy** (Gerarchia).

    ![oggetto videocamera principale evidenziato nel riquadro della gerarchia](media/unity-image4.png)

8. Selezionare il riquadro **Inspector** (Controllo) sul lato destro della finestra per visualizzare le proprietà della videocamera. Per la videocamera sono disponibili proprietà quali informazioni di trasformazione, sfondo, tipo di proiezione, campo visivo e così via. È inoltre incluso, per impostazione predefinita, un componente per l'ascolto dell'audio, che in pratica riproduce l'audio della scena da un microfono virtuale collegato alla videocamera.

    ![riquadro di controllo](media/unity-image5.png)

9. Selezionare l'oggetto **Directional Light** (Luce di direzione). Questo oggetto introduce una luce nella scena per consentire a componenti come gli shader di eseguire correttamente il rendering degli oggetti.

    ![oggetto luce di direzione evidenziato](media/unity-image6.png)

10. Usare il riquadro **Inspector** (Controllo) per verificare che includa le proprietà di illuminazione comuni tra cui tipo, colore, intensità, tipo di ombreggiatura e così via.

    ![visualizzazione delle proprietà nel riquadro di controllo](media/unity-image7.png)

11. È importante sottolineare che i progetti in Unity sono leggermente diversi dai progetti corrispondenti in Visual Studio per Mac. Nella scheda **Project** (Progetto) nella parte inferiore della schermata fare clic con il pulsante destro del mouse sulla cartella **Assets** e scegliere **Visualizza in Finder**.

    ![azione contestuale Visualizza in Finder](media/unity-image8.png)

12. Come si può notare, i progetti contengono le cartelle **Assets**, **Library**, **ProjectSettings** e **Temp**. Tuttavia, l'unica cartella visualizzata nell'interfaccia è **Assets**. La cartella **Library** è la cache locale per gli asset importati. Contiene tutti i metadati relativi agli asset. La cartella **ProjectSettings** archivia le impostazioni configurabili. La cartella **Temp** viene usata da Mono e Unity per i file temporanei durante il processo di compilazione. È anche presente un file di soluzione che è possibile aprire in Visual Studio per Mac. In questa immagine il file è denominato **UnityLab.sln**.

    ![asset nel Finder](media/unity-image9.png)

13. Chiudere la finestra **Finder** e tornare a **Unity**.

14. La **cartella Assets** contiene tutti gli asset art, il codice, l'audio e così via. È ora vuoto, ma ogni singolo file inserito nel progetto viene inserito qui. che è sempre la cartella di livello principale nell'**Editor di Unity**. È tuttavia sempre necessario aggiungere e rimuovere i file tramite l'interfaccia di Unity (o Visual Studio per Mac) e mai direttamente tramite il file system.

    ![cartella Assets in Unity](media/unity-image10.png)

15. Il **GameObject** è fondamentale per lo sviluppo in Unity poiché quasi tutto deriva da questo tipo, inclusi modelli, luci, sistemi particellari e così via. Aggiungere un nuovo oggetto **Cube** (Cubo) alla scena tramite il menu **GameObject > 3D Object > Cube** (GameObject > Oggetto 3D > Cubo).

    ![oggetto Cube nella scena](media/unity-image11.png)

16. Esaminare rapidamente le proprietà del nuovo **GameObject**. Si noterà che sono definiti un nome, un tag, un livello e una trasformazione. Queste proprietà sono comuni a tutti i **GameObject**. All'oggetto **Cube** (Cubo) sono inoltre stati collegati alcuni componenti per fornire le funzionalità necessarie, come il filtro mesh, il collider cubico e il renderer.

    ![proprietà dell'oggetto gioco](media/unity-image12.png)

17. Rinominare l'oggetto **Cube** (Cubo), che per impostazione predefinita è denominato **"Cube"**, specificando il nuovo nome **"Enemy"**. Premere **INVIO** per salvare la modifica. Questo sarà il cubo dell'avversario nel gioco semplice che si sta creando.

    ![proprietà per la ridenominazione dell'oggetto Cube](media/unity-image13.png)

18. Aggiungere nella scena un altro oggetto **Cube** (Cubo) per il giocatore con la stessa procedura illustrata in precedenza e assegnare all'oggetto il nome **"Player"**.

    ![ridenominazione del secondo oggetto Cube](media/unity-image14.png)

19. Assegnare inoltre il tag **"Player"** all'oggetto del giocatore. Vedere il controllo a discesa **Tag** sotto il campo del nome. Questo tag verrà usato nello script dell'avversario per facilitare l'identificazione dell'oggetto del giocatore.

    ![assegnazione di tag all'oggetto del giocatore](media/unity-image15.png)

20. Nella visualizzazione **Scene** (Scena) usare il mouse per allontanare l'oggetto del giocatore da quello dell'avversario lungo l'asse Z. Per spostare gli oggetti lungo l'asse Z è possibile selezionare il cubo e trascinarlo dal pannello **rosso** verso la linea **blu**. Poiché il cubo si trova nello spazio 3D, ma può solo essere trascinato in 2D ogni volta, l'asse lungo il quale viene trascinato è particolarmente importante.

    ![visualizzazione della scena con il cubo](media/unity-image16.png)

21. Spostare il cubo verso il basso a destra lungo l'asse. Per effetto di questo spostamento, la proprietà **Transform.Position** nel riquadro **Inspector** (Inspector) verrà aggiornata. Assicurarsi di trascinare il cubo in modo simile a come illustrato nell'immagine per rendere più semplici i passaggi successivi nel lab.

    ![spostamento di un cubo lungo l'asse](media/unity-image17.png)

22. A questo punto è possibile aggiungere del codice per guidare la logica dell'oggetto dell'avversario verso l'oggetto del giocatore, in modo che l'avversario insegua il giocatore. Fare clic con il pulsante **destro del mouse** sulla cartella **Assets nella Project** e scegliere Crea > **script C#.**

    ![azione contestuale per la creazione dello script C#](media/unity-image18.png)

23. Assegnare il nome **"EnemyAI"** al nuovo script C#.

    ![Script C#](media/unity-image19.png)

24. Per collegare lo script appena creato all'oggetto gioco, trascinarlo sull'oggetto **Enemy** nel riquadro **Hierarchy** (Gerarchia). A questo punto l'oggetto userà i comportamenti definiti nello script.

    ![evidenziazione che mostra l'aggiunta dello script all'oggetto gioco](media/unity-image20.png)

25. Selezionare **File > Save Scenes** (File > Salva scene) per salvare la scena corrente. Assegnare il nome **"MyScene"** alla scena.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Attività 2: Uso di Visual Studio per Mac Tools per Unity

1. Il modo migliore per modificare il codice C# è quello di usare Visual Studio per Mac. È possibile configurare Unity in modo da usare Visual Studio per Mac come gestore predefinito. Selezionare **Unity > Preferences** (Unity > Preferenze).

2. Selezionare la **scheda Strumenti** esterni. **Nell'elenco a discesa External Script Editor (Editor script** esterno) selezionare **Browse** (Sfoglia) e **selezionare Applications/Visual Studio.app**. In alternativa, se è già presente un'opzione **Visual Studio**, è sufficiente selezionare tale opzione.

    ![scheda degli strumenti esterni nelle preferenze](media/unity-image21.png)

3. Unity è ora configurato in modo da usare **Visual Studio per Mac** per la modifica dello script. Chiudere la finestra di dialogo **Unity Preferences** (Preferenze di Unity).

    ![Visual Studio selezionato nelle preferenze](media/unity-image22.png)

4. Fare doppio clic su **EnemyAI.cs** per aprirlo in **Visual Studio per Mac**.

    ![asset Enemy selezionato in Unity](media/unity-image23.png)

5. La soluzione di Visual Studio è molto semplice. Contiene una cartella **Assets** (uguale a quella nel **Finder**) e lo script **EnemyAI.cs** creato in precedenza. In progetti più sofisticati, la gerarchia avrà probabilmente un aspetto diverso rispetto a ciò che viene visualizzato in Unity.

    ![Finestra della soluzione in Visual Studio per Mac](media/unity-image24.png)

6. Il file **EnemyAI.cs** è aperto nell'editor. Lo script iniziale contiene semplicemente gli stub per i metodi **Start** e **Update**.

7. Sostituire il codice iniziale dell'avversario con il codice seguente.

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

8. Esaminare rapidamente il comportamento semplice dell'avversario definito nel codice. Nel metodo **Start** si ottiene un riferimento all'oggetto del giocatore (tramite il relativo tag) e alla relativa **trasformazione**. Nel metodo **Update**, che viene chiamato in ogni fotogramma, l'oggetto dell'avversario si sposta verso l'oggetto del giocatore. Per le parole chiave e i nomi viene usata una codifica a colori per rendere più comprensibile la codebase in Visual Studio per Mac.

9. Salvare le modifiche apportate allo script dell'avversario in **Visual Studio per Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Attività 3: Debug del progetto Unity

1. Impostare un punto di interruzione sulla prima riga di codice nel metodo **Start**. È possibile fare clic sul margine dell'editor in corrispondenza della riga di destinazione oppure posizionare il cursore sulla riga e premere **F9**.

    ![impostazione del punto di interruzione in Visual Studio per Mac](media/unity-image25.png)

2. Fare clic sul pulsante **Avvia debug** o premere **F5**. Il progetto viene compilato e collegato a Unity per il debug.

    ![Pulsante Start in Visual Studio per Mac](media/unity-image26.png)

3. Tornare a **Unity** e fare clic sul pulsante **Run** (Esegui) per avviare il gioco.

    ![pulsante per l'avvio del gioco in Unity](media/unity-image27.png)

4. Viene raggiunto il punto di interruzione ed è ora possibile usare gli strumenti per il debug di Visual Studio per Mac.

    ![Punto di interruzione raggiunto Visual Studio per Mac](media/unity-image28.png)

5. Nella finestra **Variabili locali** individuare il puntatore **this,** che fa riferimento a un **oggetto Disai.** Espandere il riferimento e notare che è possibile esplorare i membri associati, ad esempio **Speed**.

    ![Finestra Variabili locali in Visual Studio per Mac](media/unity-image29.png)

6. Rimuovere il punto di interruzione dal metodo **Start** in modo simile a come è stato aggiunto, ovvero facendo clic su di esso nel margine o selezionando la riga e premendo **F9**.

    ![Rimozione di un punto di interruzione Visual Studio per Mac facendo clic su di esso](media/unity-image30.png)

7. Premere **F10** per ignorare la prima riga di codice che trova l'oggetto gioco **Player** usando un tag come parametro.

8. Passare il puntatore del mouse sulla variabile **player** all'interno della finestra dell'editor di codice per visualizzarne i membri associati. È anche possibile espandere l'overlay per visualizzare le proprietà figlio.

    ![finestra di debug nell Visual Studio per Mac editor](media/unity-image31.png)

9. Premere **F5** o fare clic sul pulsante **Esegui** per continuare l'esecuzione. Tornare a Unity per osservare il cubo dell'avversario che si avvicina ripetutamente al cubo del giocatore. Può essere necessario modificare l'impostazione della videocamera se non è visibile.

    ![riproduzione della scena in Unity](media/unity-image32.png)

10. Tornare a **Visual Studio per Mac** e impostare un punto di interruzione sulla prima riga del metodo **Update**. Dovrebbe essere raggiunto immediatamente.

    ![Rimozione di un punto di interruzione in Visual Studio per Mac](media/unity-image33.png)

11. Si supponga che la velocità sia troppo elevata e che si voglia testare l'impatto della modifica senza riavviare l'app. Individuare la variabile **Speed** all'interno della finestra **Auto** o **Variabili locali** e quindi impostarla su **"10"** e premere **INVIO**.

    ![modifica delle variabili nella finestra Variabili locali](media/unity-image34.png)

12. Rimuovere il punto di interruzione e premere **F5** per riprendere l'esecuzione.

13. Tornare a **Unity** per visualizzare l'applicazione in esecuzione. Il cubo dell'avversario si sposta ora a una velocità pari a un quinto della velocità originale.

    ![finestra di Unity l'applicazione in esecuzione](media/unity-image35.png)

14. Arrestare l'app Unity facendo nuovamente clic sul pulsante **Play** (Riproduci).

    ![arresto dell'app Unity](media/unity-image36.png)

15. Tornare a **Visual Studio per Mac**. Arrestare la sessione di debug facendo clic sul pulsante **Arresta**.

    ![arresto della sessione di debug in Visual Studio per Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Attività 4: Esplorazione delle funzionalità di Unity in Visual Studio per Mac

1. Visual Studio per Mac consente di accedere rapidamente alla documentazione di Unity all'interno dell'editor di codice. Posizionare il cursore in un punto qualsiasi sul simbolo **Vector3** all'interno del metodo **Update** e premere **Comando ⌘+'**.

    ![selezione di un metodo nell'editor di Visual Studio per Mac](media/unity-image38.png)

2. Viene aperta una nuova finestra del browser con la documentazione relativa a **Vector3**. Dopo aver letto le informazioni desiderate, chiudere la finestra del browser.

    ![apertura della finestra del browser con la documentazione](media/unity-image39.png)

3. Visual Studio per Mac offre anche alcuni helper per creare rapidamente classi di comportamento di Unity. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Assets** e scegliere **Aggiungi > Nuovo MonoBehaviour**.

    ![azione contestuale Nuovo MonoBehaviour](media/unity-image40.png)

4. La classe appena creata fornisce gli stub per i metodi **Start** e **Update**. Dopo la parentesi graffa di chiusura del metodo **Update**, iniziare a digitare **"onmouseup"**. Durante la digitazione, si noti che la tecnologia IntelliSense di Visual Studio punta rapidamente al metodo che si prevede di implementare. Selezionarlo dall'elenco di completamento automatico visualizzato. Verrà completato automaticamente uno stub del metodo, inclusi gli eventuali parametri.

    ![IntelliSense in Visual Studio per Mac](media/unity-image41.png)

5. All'interno del metodo **OnMouseUp** digitare **"base."** per visualizzare tutti i metodi di base disponibili da chiamare. È anche possibile esplorare i diversi overload di ogni funzione usando l'opzione che consente di passare da una pagina all'altra nell'angolo in alto a destra del riquadro a comparsa IntelliSense.

    ![esplorazione di overload in Visual Studio per Mac](media/unity-image42.png)

6. Visual Studio per Mac consente inoltre di definire con facilità nuovi shader. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Assets** e scegliere **Aggiungi > Nuovo shader**.

    ![nuova azione shader in Visual Studio per Mac](media/unity-image43.png)

7. Il contenuto del file di shader è formattato con colori e un tipo di carattere che ne semplificano la lettura e la comprensione.

    ![evidenziazione della sintassi](media/unity-image44.png)

8. Tornare a **Unity**. Si noterà che, poiché Visual Studio per Mac funziona con lo stesso sistema di progetto, le modifiche apportate a uno dei programmi vengono sincronizzate automaticamente con l'altro. In questo modo, è facile usare sempre lo strumento più adatto a una specifica attività.

    ![pannello degli asset di Unity](media/unity-image45.png)

## <a name="summary"></a>Riepilogo

In questo lab si sono apprese le nozioni di base per iniziare a creare un gioco con Unity e Visual Studio per Mac. Per [https://unity3d.com/learn](https://unity3d.com/learn) altre informazioni su Unity, vedere .
