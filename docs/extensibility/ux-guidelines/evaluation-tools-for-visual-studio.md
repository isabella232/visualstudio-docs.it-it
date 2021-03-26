---
title: Strumenti di valutazione per Visual Studio | Microsoft Docs
description: Usare questo elenco di controllo per valutare la qualità dell'esperienza utente per i dettagli visivi e di interazione per le nuove funzionalità progettate per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6f23521763e73ef65b9c5a2f17acb54b85b71d63
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089888"
---
# <a name="evaluation-tools-for-visual-studio"></a>Strumenti di valutazione per Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Elenco di controllo dell'artigianato per Visual Studio
 Usare questo elenco di controllo per valutare la qualità dell'esperienza utente per i dettagli visivi e di interazione.

### <a name="overview"></a>Panoramica

- Verificare che tutti i comandi comportino un feedback che indica agli utenti che sono stati eseguiti i comandi.

- Verificare che tutti i controlli e gli elementi dell'interfaccia utente siano visibili in tutti i temi e in modalità Contrasto elevato.

- Verificare che la selezione inattiva e attiva sia sempre differenziata, in modalità standard e Contrasto elevato.

- Verificare che lo stato attivo sia sempre visibile ed evidente.

### <a name="performance"></a>Prestazioni

- Verificare che venga visualizzato un tipo di indicatore "occupato" Se il completamento di un comando richiede più di un secondo.

- Verificare che se un comando richiede più di 10 secondi per il completamento, viene visualizzato un indicatore di stato esplicito, determinato (preferito) o indeterminato.

### <a name="ui-text"></a>Testo dell'interfaccia utente

- Verificare che tutte le etichette siano maiuscole o minuscole e che nessun testo sia interamente minuscolo.

    ||Risposta esatta.|Non corretto|
    |-|-------------|---------------|
    |**Testo del comando (tutti)**|Caso frase:<br /><br /> **Nome directory:**|Nome directory:|
    |**Testo del pulsante (client)**|Maiuscole/minuscole:<br /><br /> **[Impostazione predefinita]**|IMPOSTA COME PREDEFINITO|
    |**Testo pulsante (online)**|Caso frase:<br /><br /> **[Impostazione predefinita]**||

- Verificare che tutte le etichette, eccetto le intestazioni e i pulsanti di gruppo, terminino con i due punti e precedono il controllo con cui sono abbinati.

- Verificare che i pulsanti, i comandi e i collegamenti ai comandi che avviano l'interfaccia utente per acquisire la fine dell'input utente nei puntini di sospensione **[...]**.

  Esempi:

  - Un pulsante **[Advanced...]** in una finestra di dialogo.

  - Le opzioni del comando nel menu Strumenti (**strumenti > opzioni**) non devono ottenere i puntini di sospensione perché l'avvio della finestra di dialogo è lo scopo del comando.

- Verificare che l'interfaccia utente non contenga abbreviazioni, ad eccezione dei termini standard del settore. Ad esempio, né HTML né TCP/IP devono essere digitati, anche se non è necessario che sia presente memoria insufficiente e informazioni personali (informazioni personali).

### <a name="keyboard-access"></a>Accesso da tastiera

- Verificare che sia disponibile un modo per eseguire ogni attività con la tastiera. Questa operazione viene in genere eseguita tramite l'accesso tramite tastiera per ogni controllo, ma per alcune aree estremamente visive è accettabile una soluzione alternativa come la visualizzazione del codice.

- Verificare che sia possibile tabulare i controlli in un ordine logico (da sinistra a destra e dall'alto verso il basso). Sebbene questa sia una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Verificare, ad esempio, che i controlli pulsante di opzione si trovino in un gruppo con una sola tabulazione.

- Verificare che tutti i controlli dispongano di etichette e che ogni etichetta disponga di un tasto di scelta (le eccezioni includono alcuni controlli senza etichetta che potrebbero seguire un controllo con etichetta nella scheda).

- Verificare che non siano presenti conflitti di tasto di scelta.

### <a name="fonts"></a>Tipi di carattere

- Verificare che tutti i tipi di carattere (Face, Size, Color) vengano usati in modo coerente e mantengano la gerarchia.

- Verificare che tutti gli elementi dell'interfaccia utente usino il servizio tipo di carattere ambiente. (Vedere [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Per verificare se il servizio è in uso, passare a **strumenti > opzioni > tipi di carattere e colori**. Nell'elenco a discesa Impostazioni scegliere tipo di carattere ambiente e modificare il tipo di carattere in un elemento stilisticamente diverso (ad esempio, Harrington o San comico) e impostare le dimensioni su 12 PT. Fare quindi clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente cambierà immediatamente. Le aree che non prelevano la modifica del tipo di carattere anche al riavvio non usano il tipo di carattere ambiente.

- Verificare che i tipi di carattere derivati dal servizio (ad esempio testo in grassetto o ingrandito) mantengano la dimensione e la formattazione in relazione al testo normale quando vengono modificate le dimensioni del carattere dell'ambiente.

- Verificare che non siano presenti bug di ritaglio a causa di tipi di carattere ingranditi. I tipi di carattere che vengono ritagliati sono probabilmente il risultato di controlli a altezza fissa o di contenitori a altezza fissa.

### <a name="dialogs"></a>Finestre di dialogo

- Verificare che il titolo della finestra di dialogo corrisponda al comando che lo ha avviato.

- Verificare che tutti i controlli standard siano coerenti con il sistema operativo: il colore di sfondo è standard e nessun controllo deve avere uno speciale stile ribasato su modelli che li rende più diversi dai controlli standard.

- Verificare che i margini nel form siano pari a 12 pixel e che siano uniformi e coerenti.

- Verificare che le finestre di dialogo siano visualizzate al centro nella shell IDE o nella finestra che le ha generate.

- Se utile, le finestre di dialogo devono essere ridimensionabili. Per le finestre di dialogo ridimensionabili, verificare che al momento del ridimensionamento i controlli appropriati debbano essere ridimensionati mentre altre parti della finestra di dialogo rimangono costanti.

- Verificare che le finestre di dialogo ridimensionabili mantengono le dimensioni modificate dall'utente (dimensioni, posizione, espansione dei controlli della finestra di dialogo e così via).

- Verificare che nella barra del titolo non sia presente alcuna icona.

- Verificare che nella barra del titolo non siano presenti pulsanti Riduci a icona e Ingrandisci.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Pulsanti operazione finestra di dialogo (solo client VS)

- Verificare che i pulsanti per le operazioni siano nell'ordine seguente: **OK**, **Annulla**, **applica**.

- Verificare che i pulsanti **OK** e **Annulla** siano di dimensioni standard: 75x23 pixel.

- Verificare che i pulsanti **OK** e **Annulla** siano di uguale dimensione indipendentemente dalla lunghezza della stringa.

- Se l'etichetta di un pulsante operazione richiede che il pulsante sia più ampio rispetto a standard, verificare che il pulsante **Annulla** corrispondente abbia dimensioni uguali.

- Verificare che sia presente una spaziatura interna di 6 pixel tra i pulsanti e i controlli associati.

- Verificare che i pulsanti **OK** e **Annulla** non includano tasti di scelta (chiavi di accesso definite da una lettera sottolineata).

- Verificare che un pulsante (in genere **OK**) abbia lo stato attivo per impostazione predefinita.

- Verificare che **ESC** cancelli la finestra di dialogo

- Verificare che **invio** esegua il pulsante predefinito se lo stato attivo non si trova in un controllo che elabora l'invio.

- Verificare che i pulsanti **OK** e **Annulla** siano posizionati nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile che siano in pila verticalmente in alto a destra.

- Verificare che la configurazione verticale venga utilizzata solo se altri pulsanti sono in un allineamento orizzontale all'interno della finestra di dialogo.

### <a name="control-standards"></a>Standard di controllo

#### <a name="general"></a>Generale

- Verificare che, quando possibile, siano disponibili valori predefiniti validi per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato sicuro o comune.

- Verificare che i controlli standard si comportino allo stesso modo, in modo che gli utenti sappiano cosa accadrà in base all'esperienza precedente.

#### <a name="label-controls"></a>Controlli Label

- Verificare che ogni controllo disponga di un'etichetta e che ogni etichetta sia abbinata visivamente al controllo (in genere all'interno di un intervallo di 4-6 pixel) e che sia più vicina al controllo corrispondente rispetto ad altri controlli.

- Verificare che le etichette siano posizionate a sinistra con il bordo sinistro del controllo se posizionate sopra e centrate orizzontalmente, in modo che la linea di base dell'etichetta sia allineata con la linea di base del testo di input se posizionata a sinistra.

- Verificare che se più controlli di input e etichetta in pila sono posizionati a sinistra di un controllo, le etichette vengono allineate a sinistra e una distanza uguale dal bordo della finestra di dialogo, non scaricano mai direttamente e una distanza uguale rispetto ai controlli. Le coppie devono essere distribuite uniformemente, a meno che non richiedano spazi aggiuntivi per indicare il raggruppamento.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controlli di input (caselle di testo e caselle combinate)

- Verificare che quando si usa il tipo di carattere ambiente predefinito, l'altezza di visualizzazione per caselle di testo, caselle combinate e pulsanti è di 23 pixel.

- Se si utilizza il testo di suggerimento, verificare che il colore sia impostato sull' `Environment.ControlEditHintText` utilizzo del servizio colore.

- Se il campo è un campo obbligatorio che deve essere identificato come tale, verificare:

  - che lo sfondo sia impostato su `Environment.ControlEditRequiredBackground` e il primo piano sia impostato su `Environment.ControlEditRequiredHintText`

  - si tratta di un testo di suggerimento all'interno del controllo che viene visualizzato come **" \<Required> "**

#### <a name="button-controls"></a>Controlli pulsante

- Verificare che i pulsanti abbiano una dimensione minima di 75x23 pixel, a meno che non sia disponibile un testo più lungo.

- Verificare che i pulsanti abbiano margini sinistro e destro di 3-5 pixel, nonché la spaziatura interna per il contenuto.

- È accettabile usare un piccolo pulsante quadrato con solo i puntini di sospensione **[...]** al posto di un pulsante **[Browse...]** o di una funzionalità simile. Se utilizzata, verificare che le dimensioni del pulsante siano 23x23.

- Se è presente più di un pulsante **[Browse...]** in una finestra di dialogo, verificare che venga usata la versione abbreviata (solo per i puntini di sospensione **[...]**).

- Verificare che i pulsanti con i puntini di sospensione **[...]** non abbiano un tasto di scelta. Quando lo stato attivo si trova accanto al controllo di input, una scheda deve spostare lo stato attivo sul pulsante con i puntini di sospensione.

- Verificare che i pulsanti, i comandi e i collegamenti ai comandi che avviano l'interfaccia utente secondaria che acquisisce più input utente debbano terminare con i puntini di sospensione **[...]**.

#### <a name="hyperlinks"></a>Collegamenti ipertestuali

- Verificare che un controllo collegamento ipertestuale non lampeggi mai rosso quando è attivo. Indica che il servizio colore non è in uso

- Verificare che i colori di Visual Studio usati siano:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Verificare che i collegamenti ipertestuali siano visualizzati in blu senza sottolineatura, a meno che non siano incorporati in un paragrafo.

#### <a name="check-boxes"></a>Caselle di controllo

- Se una casella di controllo contiene testo a più righe, verificare che la casella sia allineata alla prima riga di testo, non centrata verticalmente su tutte le righe.

- Verificare che le caselle di controllo indichino sempre una scelta binaria e non accedano all'utente né aprano nuove finestre o pagine.

- Se una casella di controllo presenta un'opzione correlata a un controllo di input, verificare che sia posizionata a sinistra e molto vicino sotto tale controllo per indicare la relativa relazione.

- Verificare che una casella di controllo **non venga mai** utilizzata come mezzo per abilitare l'intero contenuto di una finestra di dialogo o di una pagina.

#### <a name="group-boxes"></a>Caselle di gruppo

- Verificare che in una finestra di dialogo non sia contenuta una sola casella di gruppo che contenga l'intero contenuto della finestra di dialogo.

- Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.

- Raramente dovrebbero essere presenti più di due caselle di gruppo in una finestra di dialogo.

- Verificare che non siano presenti caselle di gruppo nidificate.

### <a name="icons"></a>Icone

- Verificare che le icone vengano visualizzate correttamente invertite quando si trova nel tema scuro.

- Verificare che tutte le icone siano basate sui concetti di base.

- Verificare che ogni icona sia distinta, facile da riconoscere e che non contenga più di due concetti (senza modificatore di stato/lingua).

- Verificare che l'icona di base appaia centrata all'interno dello spazio.

- Verificare che tutte le icone risultino leggibili in modalità Contrasto elevato.

- Verificare che tutti i colori usati siano allineati con gli standard di utilizzo dei colori.

- Verificare che non siano presenti aloni (bordi) intorno alle icone. (Se presente, l'alone deve corrispondere al colore di sfondo dell'interfaccia utente adiacente).

### <a name="touch-enabled-ui"></a>Interfaccia utente abilitata per il tocco

- Verificare che i controlli interattivi siano sufficientemente grandi da essere facilmente toccabili-dimensioni minime di **23x23 pixel**

- Verificare che le dimensioni dei controlli usati più di frequente siano di almeno **40x40 pixel** .

- Verificare che i controlli interattivi includano almeno **5 pixel di spaziatura tra di** essi
