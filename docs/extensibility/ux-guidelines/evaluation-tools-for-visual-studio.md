---
title: Strumenti di valutazione per Visual Studio | Microsoft Docs
description: Usare questo elenco di controllo per valutare la qualità dell'esperienza utente per i dettagli visivi e di interazione per le nuove funzionalità che si progettano per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baee9f3e2eaefcd659f8428bd566711949d0fe90
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900759"
---
# <a name="evaluation-tools-for-visual-studio"></a>Strumenti di valutazione per Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Elenco di controllo per gli Visual Studio
 Usare questo elenco di controllo per valutare la qualità dell'esperienza utente per i dettagli visivi e di interazione.

### <a name="overview"></a>Panoramica

- Verificare che tutti i comandi disercitino commenti e suggerimenti che comunicano agli utenti che i comandi sono stati eseguiti.

- Verificare che tutti gli elementi e i controlli dell'interfaccia utente siano visibili in tutti i temi e in Contrasto elevato personalizzata.

- Verificare che la selezione inattiva e quella attiva siano sempre differenziate, sia in modalità standard che Contrasto elevato attiva.

- Verificare che lo stato attivo sia sempre visibile ed evidente.

### <a name="performance"></a>Prestazioni

- Verificare che sia visualizzato un indicatore "occupato" se il completamento di un comando richiede più di un secondo.

- Verificare che se il completamento di un comando richiede più di 10 secondi, viene visualizzato un indicatore di stato esplicito, determinato (preferito) o indeterminato.

### <a name="ui-text"></a>Testo dell'interfaccia utente

- Verificare che tutte le etichette siano maiuscole o minuscole e che nessun testo sia interamente minuscolo.

    ||Corretto|Non corretto|
    |-|-------------|---------------|
    |**Testo del comando (tutti)**|Maiuscole/minuscole delle frasi:<br /><br /> **Nome directory:**|Nome directory:|
    |**Testo del pulsante (client)**|Caso del titolo:<br /><br /> **[ Imposta come predefinito ]**|SET AS DEFAULT|
    |**Testo del pulsante (online)**|Maiuscole/minuscole delle frasi:<br /><br /> **[ Imposta come predefinito ]**||

- Verificare che tutte le etichette, ad eccezione delle intestazioni e dei pulsanti di gruppo, terminano con i due punti e precedono il controllo a cui sono abbinate.

- Verificare che i pulsanti, i comandi e i collegamenti ai comandi che avviano l'interfaccia utente per acquisire l'input dell'utente siano terminati con i puntini di **sospensione [...]**.

  Esempi:

  - Pulsante **[Avanzate...]** in una finestra di dialogo.

  - Le opzioni del comando nel menu Strumenti ( Strumenti **>** Opzioni ) non dovrebbero ottenere i puntini di sospensione, perché l'avvio della finestra di dialogo stessa è lo scopo del comando.

- Verificare che l'interfaccia utente non contenga abbreviazioni, ad eccezione dei termini standard del settore. Ad esempio, né HTML né TCP/IP devono essere digitati, anche se la memoria insufficiente e le informazioni personali devono essere digitate.

### <a name="keyboard-access"></a>Accesso da tastiera

- Verificare che sia disponibile un modo per eseguire ogni attività con la tastiera. In genere questa operazione viene eseguita tramite l'accesso tramite tastiera per ogni controllo, ma per alcune aree altamente visive, una soluzione alternativa, ad esempio passare alla visualizzazione codice, è accettabile.

- Verificare che sia possibile scorrere i controlli in un ordine logico (da sinistra a destra e dall'alto verso il basso). Anche se si tratta di una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Ad esempio, verificare che i controlli pulsante di opzione siano in un gruppo con una singola tabulazione.

- Verificare che tutti i controlli includano etichette e che ogni etichetta abbia un tasto di scelta (le eccezioni includono alcuni controlli senza etichetta che potrebbero seguire un controllo con etichetta nella scheda).

- Verificare che non siano presenti conflitti mnemoici.

### <a name="fonts"></a>Tipi di carattere

- Verificare che tutti i tipi di carattere (viso, dimensioni, colore) siano usati in modo coerente e mantengano la gerarchia.

- Verificare che tutti gli elementi dell'interfaccia utente usino il servizio di tipi di carattere dell'ambiente. Vedere Tipi [di carattere e formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Per verificare se il servizio è in uso, passare a Strumenti **> opzioni > tipi di carattere e colori.** Nell'elenco a discesa Settings (Impostazioni) scegliere Environment Font (Tipo di carattere ambiente) e modificare il tipo di carattere in modo che sia diverso dal punto di vista stilico (ad esempio, Harrrrrr o Sans) e impostare le dimensioni su 12 pt. Fare quindi clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente verrà cambiata immediatamente. Le aree che non selezionano la modifica del tipo di carattere anche al riavvio non usano il tipo di carattere dell'ambiente.

- Verificare che i tipi di carattere derivati dal servizio (ad esempio testo in grassetto o ingrandito) mantenino le dimensioni e la formattazione in relazione al testo "normale" quando le dimensioni del carattere dell'ambiente vengono modificate.

- Verificare che non siano presenti bug di ritaglio a causa di tipi di carattere ingranditi. I tipi di carattere che vengono ritagliati sono probabilmente il risultato di controlli a altezza fissa o contenitori ad altezza fissa.

### <a name="dialogs"></a>Finestre di dialogo

- Verificare che il titolo della finestra di dialogo sia lo stesso del comando che lo ha avviato.

- Verificare che tutti i controlli standard siano coerenti con il sistema operativo: il colore di sfondo è standard e nessun controllo deve avere uno stile speciale basato su modelli che li faccia apparire diversi dai controlli standard.

- Verificare che i margini all'interno del modulo siano di 12 pixel e che siano uniformi e coerenti.

- Verificare che le finestre di dialogo vengano visualizzate al centro nella shell dell'IDE o nella finestra che li ha generati.

- Se utile, le finestre di dialogo devono essere ridimensionabili. Per le finestre di dialogo ridimensionabili, verificare che, al momento del ridimensionamento, i controlli appropriati devono essere ridimensionati mentre le altre parti del dialogo rimangono costanti.

- Verificare che le finestre di dialogo ridimensionabili permangono per tutte le dimensioni regolate dall'utente (dimensioni, posizione, espansione dei controlli della finestra di dialogo e così via).

- Verificare che non sia presente alcuna icona nella barra del titolo.

- Verificare che non siano presenti pulsanti Riduci a icona e Ingrandisci nella barra del titolo.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Pulsanti delle operazioni della finestra di dialogo (solo VS Client)

- Verificare che i pulsanti dell'operazione siano nell'ordine **seguente: OK**, **Annulla**, **Applica**.

- Verificare che **i pulsanti OK** e **Annulla** siano di dimensioni standard: 75x23 pixel.

- Verificare che **i pulsanti OK** e **Annulla** siano di dimensioni uguali indipendentemente dalla lunghezza della stringa.

- Se l'etichetta di un pulsante operazione richiede che il pulsante sia più ampio dello standard, verificare che il pulsante **Annulla** corrispondente sia di dimensioni uguali.

- Verificare che sia presente una spaziatura interna di 6 pixel tra i pulsanti e i controlli associati.

- Verificare che i **pulsanti OK** **e** Annulla non presentino tasti di scelta definiti da una lettera sottolineata.

- Verificare che un pulsante (in genere **OK)** abbia lo stato attivo per impostazione predefinita.

- Verificare che **ESC cancelli** il dialogo

- Verificare che **INVIO** eserciti il pulsante predefinito se lo stato attivo non si trova in un controllo che elabora INVIO.

- Verificare che i **pulsanti OK** **e** Annulla siano posizionati nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile che siano impilabili verticalmente in alto a destra.

- Verificare che la configurazione verticale sia usata solo se altri pulsanti si trova in un allineamento orizzontale all'interno della finestra di dialogo.

### <a name="control-standards"></a>Standard di controllo

#### <a name="general"></a>Generale

- Verificare che, quando possibile, siano disponibili valori predefiniti validi per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato sicuro o comune.

- Verificare che i controlli standard si comportino allo stesso modo in modo che gli utenti sappiano cosa accadrà in base all'esperienza precedente.

#### <a name="label-controls"></a>Controlli Etichetta

- Verificare che ogni controllo abbia un'etichetta e che ogni etichetta sia associata visivamente al relativo controllo (in genere entro un intervallo di 4-6 pixel) e che sia più vicina al controllo corrispondente rispetto ad altri controlli.

- Verificare che le etichette siano posizionate a sinistra con il bordo sinistro del controllo se posizionate sopra e centrate orizzontalmente, in modo che la linea di base dell'etichetta sia allineata alla linea di base del testo di input se posizionata a sinistra.

- Verificare che, se più controlli etichetta e input in pila sono posizionati a sinistra di un controllo, le etichette vengono scaricate a sinistra e a una distanza uguale dal bordo della finestra di dialogo, mai scaricate a destra e a una distanza uguale dai controlli. Le coppie devono essere distribuite in modo uniforme, a meno che non necessitino di una spaziatura aggiuntiva per indicare il raggruppamento.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controlli di input (caselle di testo e caselle combinate)

- Verificare che quando si usa il tipo di carattere dell'ambiente predefinito, l'altezza di visualizzazione per caselle di testo, caselle combinate e pulsanti sia di 23 pixel.

- Se viene usato il testo del suggerimento, verificare che il colore sia impostato su `Environment.ControlEditHintText` usando il servizio colori.

- Se il campo è un campo obbligatorio che deve essere identificato come tale, verificare:

  - che lo sfondo è impostato su `Environment.ControlEditRequiredBackground` e il primo piano è impostato su `Environment.ControlEditRequiredHintText`

  - il testo del suggerimento all'interno del controllo viene visualizzato come **" \<Required> "**

#### <a name="button-controls"></a>Controlli pulsante

- Verificare che i pulsanti siano di dimensioni minime di 75x23 pixel, a meno che il testo non sia più lungo.

- Verificare che i pulsanti presentino margini sinistro e destro di 3-5 pixel, nonché la spaziatura interna per il contenuto.

- È accettabile usare un piccolo pulsante quadrato con solo i puntini di sospensione **[...]** anziché un pulsante **[Sfoglia...]** (o funzionalità simili). Se usato, verificare che le dimensioni del pulsante siano 23x23.

- Se è presente più di un **pulsante [Sfoglia...]** in una finestra di dialogo, verificare che la versione abbreviata (solo puntini di sospensione **[...]**) sia usata per tutti.

- Verificare che i puntini di **sospensione [...]** non presentino un mnemono. Quando lo stato attivo è sul controllo di input accanto, una scheda dovrebbe spostare lo stato attivo sul pulsante con i puntini di sospensione.

- Verificare che i pulsanti, i comandi e i collegamenti di comando che avviano l'interfaccia utente secondaria che acquisisce più input utente devono terminare con i puntini di **sospensione [...]**.

#### <a name="hyperlinks"></a>Collegamenti ipertestuali

- Verificare che un controllo collegamento ipertestuale non lampeggia mai in rosso quando è attivo. Si tratta di un indicatore che indica che il servizio colori non è in uso

- Verificare che i colori di Visual Studio usati siano:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Verificare che i collegamenti ipertestuali siano visualizzati in blu senza sottolineatura, a meno che non siano incorporati in un paragrafo.

#### <a name="check-boxes"></a>Caselle di controllo

- Se una casella di controllo contiene testo su più righe, verificare che la casella sia allineata alla prima riga di testo, non centrata verticalmente su tutte le righe.

- Verificare che le caselle di controllo indichino sempre una scelta binaria e non esplorare l'utente o aprire nuove finestre o pagine.

- Se una casella di controllo presenta un'opzione correlata a un controllo di input, verificare che sia posizionato a sinistra e molto vicino sotto tale controllo per indicarne la relazione.

- Verificare che una casella di controllo non **sia mai** usata come mezzo per abilitare l'intero contenuto di una finestra di dialogo o di una pagina.

#### <a name="group-boxes"></a>Caselle di gruppo

- Verificare che una finestra di dialogo non contenga al suo interno una singola casella di gruppo contenente l'intero contenuto della finestra di dialogo.

- Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.

- Raramente devono essere presenti più di due caselle di gruppo in una finestra di dialogo.

- Verificare che non siano presenti caselle di gruppo annidate.

### <a name="icons"></a>Icone

- Verificare che le icone vengano visualizzate correttamente invertiti nel tema scuro.

- Verificare che tutte le icone siano basate sui concetti di base.

- Verificare che ogni icona sia distinta, facile da riconoscere e non contenga più di due concetti (senza modificatore di stato/linguaggio).

- Verificare che l'icona di base sia centrata all'interno dello spazio.

- Verificare che tutte le icone siano leggibili in Contrasto elevato attiva.

- Verificare che qualsiasi colore usato sia allineato agli standard di utilizzo dei colori.

- Verificare che non siano presenti aloni (bordi) intorno alle icone. Se presente, l'alone deve corrispondere al colore di sfondo dell'interfaccia utente adiacente.

### <a name="touch-enabled-ui"></a>Interfaccia utente abilitata per il tocco

- Verificare che i controlli interattivi siano sufficientemente grandi da essere facilmente toccabili, con dimensioni minime **di 23x23** pixel

- Verificare che le dimensioni dei controlli usati più di frequente siano di **almeno 40x40** pixel.

- Verificare che i controlli interattivi hanno almeno **5 pixel di spaziatura** tra di essi
