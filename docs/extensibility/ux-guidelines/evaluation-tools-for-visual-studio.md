---
title: Strumenti di valutazione per Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77e6dca01f728ae4a5a3f0a5f12f50ab581948c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335389"
---
# <a name="evaluation-tools-for-visual-studio"></a>Strumenti di valutazione per Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Elenco di controllo per le proprie abilità per Visual Studio
 Usare questo elenco di controllo per la valutazione di qualità di esperienza utente per i dettagli di oggetto visivo e interazione.

### <a name="overview"></a>Panoramica

- Verificare che tutti i comandi comportare feedback che indica agli utenti che sono stati effettuati i relativi comandi.

- Verificare che tutti gli elementi dell'interfaccia utente e i controlli siano visibili in tutti i temi e in modalità a contrasto elevato.

- Verificare che inattivi e attivo della selezione sono sempre attività sia in modalità a contrasto elevato e standard.

- Verificare che lo stato attivo è sempre visibile e apparente.

### <a name="performance"></a>Prestazioni

- Verificare che alcuni indicatore del tipo di "occupato" viene visualizzato se un comando ha più di un secondo per il completamento.

- Verificare che se un comando richiede più di 10 secondi per il completamento, un indicatore di stato esplicita, ovvero determinato per (scelta consigliata) o indeterminato, viene visualizzato.

### <a name="ui-text"></a>Testo dell'interfaccia utente

- Verificare che tutte le etichette sono maiuscola o titolo e che il testo non è completamente caratteri minuscolo.

    ||Correggere|Non corretto|
    |-|-------------|---------------|
    |**Testo del comando (tutti)**|Maiuscola:<br /><br /> **Nome della directory:**|Nome della directory:|
    |**Testo del pulsante (client)**|Iniziali maiuscole:<br /><br /> **[Predefinito]**|SET AS DEFAULT|
    |**Testo del pulsante (online)**|Maiuscola:<br /><br /> **[Impostato come predefinito]**||

- Verificare che tutte le etichette, ad eccezione di intestazioni di gruppo e i pulsanti, terminano con un carattere due punti e far precedere il controllo con cui essi sono abbinate.

- Verificare che i pulsanti, i comandi e collegamenti ai comandi che avviano l'interfaccia utente per acquisire l'input dell'utente terminare con i puntini di sospensione **[...]** .

     Esempi:

    - Un **[avanzate...]**  pulsante in una finestra di dialogo.

    - Le opzioni di comando nel menu Strumenti (**strumenti > Opzioni**) non dovrebbe essere i puntini di sospensione, perché l'avvio la finestra di dialogo è lo scopo del comando.

- Verificare che l'interfaccia utente non contiene nessun abbreviazioni, ad eccezione di termini standard del settore. Ad esempio, HTML, né TCP/IP necessario pronunciata, anche se informazioni personali (informazioni personali) e memoria insufficiente (esaurito la memoria) deve.

### <a name="keyboard-access"></a>Accesso da tastiera

- Verificare che vi sia un modo per completare ciascuna attività con la tastiera. In genere questa operazione viene eseguita tramite l'accesso da tastiera per ogni controllo, ma per alcune aree elevato impatto visivi, una soluzione alternativa, ad esempio passare alla visualizzazione codice è accettabile.

- Verificare che può spostarsi tra i controlli in ordine logico (da sinistra a destra e alto verso il basso). Si tratta di una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Ad esempio, verificare tale pulsante di opzione sono controlli in un gruppo con un punto di tabulazione singolo.

- Verificare che tutti i controlli dispongono di etichette e che ogni etichetta ha un tasto di scelta (eccezioni includono alcuni controlli con etichetta non potrebbero seguire un controllo nella scheda con etichettato).

- Verificare che non siano presenti conflitti di tasti di scelta rapida.

### <a name="fonts"></a>Tipi di carattere

- Verificare che tutti i tipi di carattere (viso, dimensioni, colore) vengono utilizzati in modo coerente e mantenere la gerarchia.

- Verificare che tutti gli elementi dell'interfaccia utente utilizzano il servizio di tipo di carattere ambiente. (Vedere [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Per determinare se il servizio è in uso, passare a **strumenti > Opzioni > tipi di carattere e colori**. Nell'elenco a discesa delle impostazioni, Scegli tipo di carattere ambiente e modificare il tipo di carattere in modo stilisticamente non corretto diverso (ad esempio Harrington o fumetti nomi alternativi del soggetto) e impostare le dimensioni su 12 pt. Quindi fare clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente cambierà immediatamente. Le aree che non ricevono la modifica del tipo di carattere anche al riavvio non si usano il tipo di carattere ambiente.

- Verificare che i tipi di carattere derivato del servizio (ad esempio, testo in grassetto o ingrandito) mantenere le dimensioni e la formattazione in relazione al testo "normale" quando viene modificata la dimensione del carattere di ambiente.

- Verificare che non esistono Nessun bug ritaglio a causa di tipi di carattere ingrandite. I tipi di carattere che ottenere ritagliate sono probabilmente il risultato dell'altezza fissa controlli o i contenitori di altezza fissa.

### <a name="dialogs"></a>Finestre di dialogo

- Verificare che il titolo della finestra di dialogo è identico al comando che l'ha avviata.

- Verificare che tutti i controlli standard sono coerenti con il sistema operativo: colore di sfondo è standard e non i controlli devono avere uno stile basato ri speciale che li rende un aspetto diverso dai controlli standard.

- Verificare che i margini interno del modulo devono essere 12 pixel e dovrebbe essere visualizzato uniforme e coerente.

- Verificare che le finestre di dialogo vengono visualizzati al centro all'interno di shell dell'IDE o nella finestra che li ha generato.

- Quando è utile, finestre di dialogo possono essere ridimensionati. Per le finestre di dialogo che è possibile ridimensionare, verificare che al momento del ridimensionamento, i controlli appropriati è necessario ridimensionare mentre altre parti della finestra di dialogo rimangono costanti.

- Verificare che le finestre di dialogo ridimensionabili salvare in modo permanente qualsiasi dimensione regolata l'utente (dimensioni, posizione, espansione dei controlli di finestra di dialogo e così via).

- Non verificare che sia presente alcuna icona nella barra del titolo.

- Verificare che non sono presenti pulsanti Riduci a icona e Ingrandisci nella barra del titolo.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Pulsanti di operazione della finestra (solo Client di Visual Studio)

- Verificare che i pulsanti di operazione sono nell'ordine indicato: **OK**, **annullare**, **applicare**.

- Verificare che **OK** e **Annulla** pulsanti sono le dimensioni standard: 75 x 23 pixel.

- Verificare che **OK** e **Annulla** pulsanti sono della stessa dimensione indipendentemente dalla lunghezza della stringa.

- Se l'etichetta di un pulsante di operazione richiede il pulsante sia largo standard, verificare che la corrispondente **annullare** pulsante è di dimensioni uguali.

- Verificare che sia presente un riempimento 6 pixel tra i pulsanti e i controlli associati.

- Verificare che il **OK** e **Annulla** pulsanti non hanno i tasti di scelta (definite da una lettera sottolineata. le chiavi di accesso).

- Verificare che un pulsante (in genere **OK**) ha lo stato attivo per impostazione predefinita.

- Verificare che **Esc** Annulla la finestra di dialogo

- Verificare che **invio** esegue il pulsante predefinito, se lo stato attivo non è presente in un controllo che elabora l'invio.

- Verificare che il **OK** e **Annulla** sono posizionati i pulsanti nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile per poter essere sovrapposti in verticale in alto a destra.

- Verificare che la configurazione verticale viene utilizzata solo se altri pulsanti si trovano l'allineamento orizzontale nella finestra di dialogo.

### <a name="control-standards"></a>Standard del controllo

#### <a name="general"></a>Generale

- Verificare che, quando possibile, esistono buone valori predefiniti per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato comune o sicuri.

- Verificare che i controlli standard si comportano allo stesso modo, in modo che gli utenti sappiano cosa accadrà in base all'esperienza precedente.

#### <a name="label-controls"></a>Controlli Label

- Verificare che ogni controllo dispone di un'etichetta e che ogni etichetta visivamente viene confrontato con il relativo controllo (in genere entro un intervallo di pixel 4-6) e si avvicina al relativo controllo corrispondente rispetto ad altri controlli.

- Verificare che le etichette vengono posizionate flush sinistra con il controllo bordo sinistro se posizionata di sopra e al centro in senso orizzontale, in modo che la linea di base dell'etichetta è allineata alla linea di base del testo di input se posizionata a sinistra.

- Verificare che se diverse barre in pila etichetta e i controlli di input vengano posizionati a sinistra di un controllo, le etichette sono allineamento a sinistra e una distanza dal bordo della finestra di dialogo uguale non flush mai a destra e alla stessa distanza dai controlli. Coppie devono essere distribuite in modo uniforme a meno che non hanno bisogno di spaziatura aggiuntiva per indicare il raggruppamento.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controlli di input (caselle di testo e caselle combinate)

- Verificare che quando si usa il tipo di carattere ambiente predefinito, l'altezza di visualizzazione per le caselle di testo, pulsanti e caselle combinate sono tutti di 23 pixel.

- Se viene utilizzato testo di suggerimento, verificare che il colore è impostato su `Environment.ControlEditHintText` usando il servizio di colore.

- Se il campo è un campo obbligatorio che deve essere identificato come tali, verificare che:

    - che lo sfondo è impostato su `Environment.ControlEditRequiredBackground` e primo piano è impostato su `Environment.ControlEditRequiredHintText`

    - che vi sia all'interno del controllo che viene visualizzato come testo del suggerimento **"\<necessarie >"**

#### <a name="button-controls"></a>Controlli pulsante

- Verificare che i pulsanti sono una dimensione minima di 75 x 23 pixel, a meno che non da tenere conto di un testo più lungo.

- Verificare che i pulsanti hanno sinistro e destro dei margini di 3 a 5 pixel, nonché la spaziatura interna per il contenuto.

- È accettabile usare un pulsante quadrato piccolo solo puntini di sospensione **[...]**  su di esso anziché un **[Sfoglia...]**  pulsante (o una funzionalità simile). Se usato, verificare che il pulsante 23 x 23 nella dimensione.

- Se è presente più di un **[Sfoglia...]**  in una finestra di dialogo e quindi verificare che la versione abbreviata (solo con puntini di sospensione **[...]** ) viene usato per tutti.

- Verificare che i puntini di sospensione **[...]**  pulsanti non hanno un tasto di scelta rapida. Quando lo stato attivo si trova sul controllo input accanto a esso, una scheda deve spostare lo stato attivo al pulsante con puntini di sospensione.

- Verificare che i pulsanti, i comandi e collegamenti ai comandi che avviano l'interfaccia utente secondaria per l'acquisizione di più input dell'utente deve terminare con i puntini di sospensione **[...]** .

#### <a name="hyperlinks"></a>Collegamenti ipertestuali

- Verificare che un controllo collegamento ipertestuale fa mai lampeggia rosso quando è attivo. Si tratta di un indicatore che il servizio di colore non viene uso

- Verificare che siano usati i colori di Visual Studio:

    - `Environment.ControlLinkText`

    - `Environment.ControlLinkTextHover`

    - `Environment.ControlLinkTextPressed`

- Verificare che i collegamenti ipertestuali vengono visualizzati con alcun carattere di sottolineatura blu a meno che non incorporato in un paragrafo.

#### <a name="check-boxes"></a>Caselle di controllo

- Se una casella di controllo presenta testo su più righe, verificare che la casella in linea con la prima riga del testo, non è centrato verticalmente su tutte le righe.

- Verificare che le caselle di controllo sempre indicare una scelta binaria e non l'utente potrà passare o aprire nuove finestre o pagine.

- Se una casella di controllo presenta un'opzione correlata a un controllo di input, verificare che sia posizionato flush a sinistra e lavoriamo a stretto sotto tale controllo per indicare la relazione.

- Verificare che sia una casella di controllo **mai** usato come mezzo per abilitare l'intero contenuto di una pagina o finestra di dialogo.

#### <a name="group-boxes"></a>Caselle di gruppo

- Verificare che una finestra di dialogo non contiene una casella di gruppo singola in esso contenuti che contiene l'intero contenuto della finestra di dialogo.

- Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.

- Raramente devono essere presenti più di due caselle di gruppo in una finestra di dialogo.

- Verificare che non esistono alcuna casella gruppi annidati.

### <a name="icons"></a>Icone

- Verificare che le icone vengono visualizzate invertite correttamente quando nel tema scuro.

- Verificare che tutte le icone sono basate su concetti di base.

- Verificare che ogni icona è distinct, risulterà più semplice riconoscerle e non contiene più di due concetti (senza stato modificatore/linguaggio).

- Verificare che l'icona di base viene visualizzata al centro all'interno dello spazio.

- Verificare che tutte le icone vengono visualizzate leggibile in modalità a contrasto elevato.

- Verificare che qualsiasi colore utilizzato in linea con gli standard di utilizzo di colore.

- Verificare che non esistono Nessun aloni (bordi) attorno a icone. (Se presente, l'alone deve corrispondere il colore di sfondo dell'interfaccia utente adiacente).

### <a name="touch-enabled-ui"></a>Interfaccia utente abilitato per il tocco

- Verificare che siano sufficientemente grandi da essere facilmente touchable: minimo controlli interattivi **23 x 23 pixel** dimensioni

- Verificare che i controlli usati più di frequente sono almeno **40 x 40 pixel** nella dimensione.

- Verificare che i controlli interattivi abbiano almeno **5 pixel di spaziatura** tra di essi