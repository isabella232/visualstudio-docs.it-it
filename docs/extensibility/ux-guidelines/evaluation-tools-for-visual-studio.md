---
title: Strumenti di valutazione per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698422"
---
# <a name="evaluation-tools-for-visual-studio"></a>Strumenti di valutazione per Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Elenco di controllo per l'artigianato per Visual Studio
 Usa questo elenco di controllo per valutare la qualità dell'esperienza utente per i dettagli visivi e di interazione.

### <a name="overview"></a>Panoramica

- Verificare che tutti i comandi generano un feedback che indichi agli utenti che i comandi sono stati eseguiti.

- Verifica che tutti gli elementi e i controlli dell'interfaccia utente siano visibili in tutti i temi e in modalità Contrasto elevato.

- Verificare che la selezione inattiva e attiva siano sempre differenziate, sia in modalità standard che in modalità Contrasto elevato.

- Verificare che lo stato attivo sia sempre visibile e visibile.

### <a name="performance"></a>Prestazioni

- Verificare che venga visualizzato un tipo di indicatore "occupato" se il completamento di un comando richiede più di un secondo.

- Verificare che se il completamento di un comando richiede più di 10 secondi, venga visualizzata un'indicatore di stato esplicito, determinato (preferito) o indeterminato.

### <a name="ui-text"></a>Testo dell'interfaccia utente

- Verificare che tutte le etichette siano maiuscole o minuscole e che nessun testo sia interamente minuscolo.

    ||Versione corretta|Non corretto|
    |-|-------------|---------------|
    |**Testo del comando (tutti)**|Caso di sentenza:<br /><br /> **Nome directory:**|Nome directory:|
    |**Testo pulsante (client)**|Custodia del titolo:<br /><br /> **[ Imposta come predefinito ]**|IMPOSTA COME PREDEFINITO|
    |**Testo del pulsante (online)**|Caso di sentenza:<br /><br /> **[ Imposta come predefinito ]**||

- Verificare che tutte le etichette, ad eccezione delle intestazioni di gruppo e dei pulsanti, terminino con i due punti e precedano il controllo a cui sono associate.

- Verificare che i pulsanti, i comandi e i collegamenti ai comandi che avviano l'interfaccia utente per acquisire l'input dell'utente terminino con i lipsia **[...]**.

  Esempi:

  - Un pulsante **[Avanzate...]** in una finestra di dialogo.

  - Le opzioni di comando nel menu Strumenti (**Strumenti > Opzioni**) non devono ottenere i solcani, perché l'avvio della finestra di dialogo è lo scopo del comando.

- Verificare che l'interfaccia utente non contenga abbreviazioni, ad eccezione dei termini standard del settore. Ad esempio, né HTML né TCP/IP devono essere precisati, anche se OOM (memoria insufficiente) e PII (informazioni personali) dovrebbero.

### <a name="keyboard-access"></a>Accesso da tastiera

- Verificare che sia disponibile un modo per eseguire ogni attività con la tastiera. In genere questa operazione viene eseguita tramite l'accesso da tastiera per ogni controllo, ma per alcune aree altamente visive, una soluzione alternativa, ad esempio passare alla visualizzazione codice è accettabile.

- Verificare che sia possibile scorrere i controlli in ordine logico (da sinistra a destra e dall'alto verso il basso). Sebbene questa sia una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Ad esempio, verificare che i controlli pulsante di opzione siano in un gruppo con una singola tabulazione.

- Verificare che tutti i controlli dispongano di etichette e che ogni etichetta disponga di un tasto di scelta (eccezioni includono alcuni controlli senza etichetta che potrebbero seguire un controllo con etichetta nella scheda).

- Verificare che non siano presenti conflitti mnemonici.

### <a name="fonts"></a>Tipi di carattere

- Verificare che tutti i tipi di carattere (faccia, dimensione, colore) siano utilizzati in modo coerente e mantengano la gerarchia.

- Verificare che tutti gli elementi dell'interfaccia utente utilizzino il servizio di tipi di carattere dell'ambiente. (Vedere [tipi di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Per verificare se il servizio è in uso, passare a **Strumenti > Opzioni > Tipi di carattere e colori**. Nell'elenco a discesa Impostazioni, scegliete Carattere ambiente e impostate il tipo di carattere in stile stilino diverso (ad esempio Harrington o Comic Sans) e impostate la dimensione su 12 pt. Fare quindi clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente verrà modificata immediatamente. Le aree che non rilevano la modifica del tipo di carattere anche al riavvio non utilizzano il tipo di carattere dell'ambiente.

- Verificare che i tipi di carattere derivati dal servizio (ad esempio, testo in grassetto o ingrandito) mantengano le dimensioni e la formattazione in relazione al testo "normale" quando viene modificata la dimensione del carattere dell'ambiente.

- Verificare che non siano presenti bug di ritaglio dovuti a caratteri ingranditi. I tipi di carattere che vengono ritagliati sono probabilmente il risultato di controlli di altezza fissa o contenitori di altezza fissa.

### <a name="dialogs"></a>Finestre di dialogo

- Verificare che il titolo della finestra di dialogo sia lo stesso del comando che l'ha avviata.

- Verificare che tutti i controlli standard siano coerenti con il sistema operativo: il colore di sfondo è standard e nessun controllo deve avere uno stile speciale basato su modelli che li renda diversi dai controlli standard.

- Verificare che i margini all'interno del modulo siano di 12 pixel e che appaiano uniformi e coerenti.

- Verificare che le finestre di dialogo vengano visualizzate centrate all'interno della shell dell'IDE o della finestra che le ha generate.

- Quando è utile, le finestre di dialogo devono essere ridimensionabili. Per le finestre di dialogo ridimensionabili, verificare che al momento del ridimensionamento i controlli appropriati devono essere ridimensionati mentre altre parti della finestra di dialogo rimangono costanti.

- Verificare che le finestre di dialogo ridimensionabili manchino di qualsiasi dimensione regolata dall'utente (dimensioni, posizione, espansione dei controlli finestra di dialogo e così via).

- Verificare che non sia presente alcuna icona nella barra del titolo.

- Verificare che non siano presenti pulsanti Riduci a icona e Ingrandisci nella barra del titolo.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Pulsanti di operazione della finestra di dialogo (solo client VS)

- Verificare che i pulsanti di operazione siano nell'ordine seguente: **OK**, **Annulla**, **Applica**.

- Verificare che i pulsanti **OK** e **Annulla** siano delle dimensioni standard: 75x23 pixel.

- Verificare che i pulsanti **OK** e **Annulla** siano di dimensioni uguali indipendentemente dalla lunghezza della stringa.

- Se l'etichetta su un pulsante di operazione richiede che il pulsante sia più largo dello standard, verificare che il pulsante **Annulla** corrispondente sia di uguale dimensione.

- Verificare che sia presente una spaziatura interna di 6 pixel tra i pulsanti e i controlli associati.

- Verificare che i pulsanti **OK** e **Annulla** non dispongano di tasti di scelta definiti da una lettera sottolineata.

- Verificare che un pulsante (in genere **OK**) abbia lo stato attivo per impostazione predefinita.

- Verificare che **Esc** annulli la finestra di dialogo

- Verificare che **Enter** esegua il pulsante predefinito se lo stato attivo non si trova in un controllo che elabora Invio.

- Verificare che i pulsanti **OK** e **Annulla** siano posizionati nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile che vengano impilati verticalmente in alto a destra.

- Verificare che la configurazione verticale venga utilizzata solo se altri pulsanti sono in allineamento orizzontale all'interno della finestra di dialogo.

### <a name="control-standards"></a>Norme di controllo

#### <a name="general"></a>Generale

- Verificare che, quando possibile, siano presenti valori predefiniti ottimali per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato sicuro o comune.

- Verificare che i controlli standard si comportino allo stesso modo in modo che gli utenti sappiano cosa accadrà in base all'esperienza precedente.

#### <a name="label-controls"></a>Controlli etichetta

- Verificare che ogni controllo disponga di un'etichetta e che ogni etichetta sia visivamente associata al relativo controllo (in genere all'interno di un intervallo di 4-6 pixel) e che sia più vicina al controllo corrispondente rispetto ad altri controlli.

- Verificare che le etichette siano posizionate allineate a sinistra con il bordo sinistro del controllo se posizionate sopra e centrate orizzontalmente, in modo che la linea di base dell'etichetta sia allineata alla linea di base del testo di input se posizionata a sinistra.

- Verificare che se più controlli di input e etichetta in pila sono posizionati a sinistra di un controllo, le etichette vengono allineate a sinistra e una distanza uguale dal bordo della finestra di dialogo, mai a destra e una distanza uguale dai controlli. Le coppie devono essere distribuite in modo uniforme, a meno che non necessitino di una spaziatura aggiuntiva per indicare il raggruppamento.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controlli di input (caselle di testo e caselle combinate)

- Verificare che quando si utilizza il tipo di carattere di ambiente predefinito, l'altezza di visualizzazione per le caselle di testo, le caselle combinate e i pulsanti siano tutti di 23 pixel.

- Se viene utilizzato il testo del suggerimento, verificare che il colore sia impostato su `Environment.ControlEditHintText` utilizzo del servizio colore.

- Se il campo è un campo obbligatorio che deve essere identificato come tale, verificare quanto segue:

  - su cui è `Environment.ControlEditRequiredBackground` impostato lo sfondo e il primo piano è impostato su`Environment.ControlEditRequiredHintText`

  - che è presente testo di suggerimento all'interno del controllo che viene visualizzato come **\<"Obbligatorio>"**

#### <a name="button-controls"></a>Controlli pulsante

- Verificare che i pulsanti hanno una dimensione minima di 75x23 pixel, a meno che il testo non sia più lungo.

- Verificare che i pulsanti abbiano margini sinistro e destro di 3-5 pixel, nonché spaziatura interna per il contenuto.

- È accettabile utilizzare un piccolo pulsante quadrato con solo i lipsia **[...]** invece di un pulsante **[Sfoglia...]** (o funzionalità simili). Se utilizzato, verificare che il pulsante sia di dimensioni 23x23.

- Se in una finestra di dialogo è presente più di un pulsante **[Sfoglia...],** verificare che la versione abbreviata (solo i lipsia **[...]**) viene utilizzata per tutti.

- Verificare che i pulsanti con i solchi **[...]** non dispongano di un tasto di scelta rapida. Quando lo stato attivo è sul controllo di input accanto, una scheda deve spostare lo stato attivo sul pulsante con i coniatori a i lipsia.

- Verificare che i pulsanti, i comandi e i collegamenti ai comandi che avviano un'interfaccia utente secondaria che acquisisce più input dell'utente devono terminare con i lipsia **[...]**.

#### <a name="hyperlinks"></a>Collegamenti ipertestuali

- Verificare che un controllo collegamento ipertestuale non lampeggi mai in rosso quando è attivo. Questo è un indicatore che il servizio colore non è in uso

- Verificare che i colori VS utilizzati siano:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Verificare che i collegamenti ipertestuali appaiano in blu senza sottolineatura, a meno che non siano incorporati in un paragrafo.

#### <a name="check-boxes"></a>Caselle di controllo

- Se una casella di controllo contiene testo su più righe, verificare che la casella sia allineata alla prima riga di testo, non centrata verticalmente su tutte le righe.

- Verificare che le caselle di controllo indichino sempre una scelta binaria e non si spostino all'utente né aprano nuove finestre o pagine.

- Se una casella di controllo presenta un'opzione relativa a un controllo di input, verificare che sia posizionata a sinistra e molto vicina sotto tale controllo per indicarne la relazione.

- Verificare che una casella di controllo non venga **mai** utilizzata come mezzo per abilitare l'intero contenuto di una finestra di dialogo o di una pagina.

#### <a name="group-boxes"></a>Caselle di gruppo

- Verificare che una finestra di dialogo non contenga una singola casella di gruppo al suo interno che contiene l'intero contenuto della finestra di dialogo.

- Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.

- Raramente dovrebbero essere presenti più di due caselle di gruppo in una finestra di dialogo.

- Verificare che non siano presenti caselle di gruppo nidificate.

### <a name="icons"></a>Icone

- Verificare che le icone appaiano correttamente invertite quando si è nel tema scuro.

- Verificare che tutte le icone siano basate sui concetti di base.

- Verificare che ogni icona sia distinta, facile da riconoscere e non contenga più di due concetti (senza modificatore/lingua di stato).

- Verificare che l'icona di base sia centrata all'interno dello spazio.

- Verificare che tutte le icone siano leggibili in modalità Contrasto elevato.

- Verificare che qualsiasi colore utilizzato sia allineato agli standard di utilizzo del colore.

- Verificare che non siano presenti aloni (bordi) intorno alle icone. (Se presente, l'alone deve corrispondere al colore di sfondo dell'interfaccia utente adiacente).

### <a name="touch-enabled-ui"></a>Interfaccia utente abilitata per il tocco

- Verificare che i controlli interattivi siano abbastanza grandi da essere facilmente toccabili - dimensioni minime **23x23 pixel**

- Verificare che le dimensioni dei controlli utilizzati più di frequente siano di almeno **40x40 pixel.**

- Verificare che i controlli interattivi abbiano almeno **5 pixel di spaziatura** tra di essi
