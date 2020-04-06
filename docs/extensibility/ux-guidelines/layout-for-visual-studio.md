---
title: Layout per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698400"
---
# <a name="layout-for-visual-studio"></a>Layout per Visual Studio
La maggior parte delle finestre di dialogo di Visual Studio sono il layout della finestra di [dialogo Utility](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), ovvero le finestre di dialogo senza tema che seguono i principi standard di layout delle finestre di [dialogo di Windows Desktop](/windows/desktop/uxguide/win-dialog-box). Come Visual Studio si sposta per aggiornare l'interfaccia utente, alcune delle finestre di dialogo più importanti hanno una nuova progettazione che le stabilisce come esperienze di definizione del prodotto. Questi [layout di finestra di dialogo a](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tema hanno un aspetto tema.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Layout della finestra di dialogo Utilità

- Tutti i controlli all'interno di una finestra di dialogo di utilità devono iniziare in alto/sinistra e scorrere verso il basso.

- Non centrare mai i controlli in una finestra di dialogo per riempire un'area di grandi dimensioni.

- Utilizzare il tipo di carattere dell'ambiente per tutto il testo della finestra di dialogo. Quando si scrive una specifica visiva, specificare il tipo di carattere dell'ambiente anziché selezionare un tipo di carattere e una dimensione specifici. Consultate [Il font dell'ambiente.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)

- Utilizzare la spaziatura e il posizionamento del controllo coerenti per supportare l'obiettivo per la qualità nell'artigianato.

- Le finestre di dialogo possono diventare più complesse da un numero maggiore di controlli, da una giustapposizione univoca di controlli o da entrambi. Per queste situazioni complesse, consentire uno spazio adeguato tra i raggruppamenti di controlli per fornire all'utente un flusso logico da analizzare.

### <a name="utility-dialog-layout-examples"></a>Esempi di layout della finestra di dialogo Utilità
 Tutte le dimensioni sono espresse come pixel.

 ![Spaziatura della finestra di dialogo per le etichette sopra i controlli](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08.01-a: Linee guida per la spaziatura per le finestre di dialogo di utilità con etichette sopra i controlli**

 ![Spaziatura della finestra di dialogo per le etichette a sinistra dei controlli](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08.01-b: Linee guida per la spaziatura per le finestre di dialogo di utilità con etichette a sinistra dei controlli**

### <a name="layout-details"></a>Dettagli del layout

#### <a name="margins"></a>Margini

- Tutte le finestre di dialogo devono avere un bordo di 12 pixel intorno a tutti i bordi.

- I margini all'interno di una cornice di gruppo devono essere di 9 pixel dal bordo della cornice.

- I margini all'interno di un controllo struttura a schede devono essere di 6 pixel dal bordo del controllo struttura a schede.

#### <a name="command-buttons"></a>Pulsanti di comando

- I pulsanti di comando operano sulla cornice della finestra di dialogo, non sul contenuto. Essi devono essere posizionati in basso a destra e dovrebbero avere abbastanza spazio variabile sopra per impostare i pulsanti distintamente separati.

- Se sono presenti pulsanti orizzontali che operano all'interno della finestra di dialogo, la configurazione del pulsante di comando alternativo è una pila verticale in alto a destra. Vedere [Pulsanti](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) di comando interni di seguito.

- Lo spazio a sinistra dei pulsanti di comando (in basso a sinistra/centro della finestra di dialogo) è considerato parte della "banda" dei controlli delle operazioni della finestra di dialogo. L'unica cosa che dovrebbe intromettersi in tale spazio è un collegamento alla Guida che è rilevante per l'attività complessiva o la finestra di dialogo.

- I pulsanti di comando devono essere 75x23 pixel.

- I pulsanti di comando devono essere distanti 6 pixel.

  ![Allineamento di base dei pulsanti](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08.01-c: Allineamento di base dei pulsanti**

#### <a name="labels"></a>Etichette

- Allineare tutte le etichette a sinistra.

- Per le etichette che si trovano sopra un controllo, devono essere allineate a sinistra con precisione con il controllo sottostante e la parte inferiore dell'etichetta deve essere di 5 pixel sopra la parte superiore dell'altro controllo (ad esempio, una casella combinata).

- Per le etichette che si trova a sinistra dei controlli, la larghezza minima tra l'etichetta e il controllo di input è 10 pixel. È necessario stabilire una seconda colonna implicita per allineare le caselle di testo, le caselle combinate o altri controlli.

- Le etichette sono maiuscole/minuscole e sono seguite da due punti. Consultate [Stile testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Distanza tra i comandi
 Controlli dello stack ragionevolmente. Non esiste una linea guida assoluta per la spaziatura tra i controlli impilati. La tenuta tra i controlli può variare leggermente tra le finestre di dialogo. La spaziatura consigliata è di 20 pixel per le coppie controllo/etichetta verticali e di 9 pixel per le coppie controllo/etichetta orizzontali. La spaziatura di controllo minima per le coppie orizzontali è di 6 pixel.

 ![Distanza consigliata tra controlli](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08.01-d: Raccomandazioni per la distanza tra i controlli**

#### <a name="control-indentation"></a>Controllare il rientro
 Quando i controlli sono annidati, allineare i controlli interni orizzontalmente con il bordo sinistro del controllo precedente, in genere l'etichetta.

 ![Allineamento dei controlli annidati](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08.01-e: allineamento dei controlli annidati**

#### <a name="control-width"></a>Larghezza controllo
 La larghezza di una casella di testo o di altri controlli simili non deve essere maggiore dell'input medio per il campo. La parola inglese media è di cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere lunga come il layout orizzontale consentito, mentre un elenco a discesa per i nomi di piattaforma deve essere solo una lunghezza che consente la voce più lunga.

#### <a name="helper-text"></a>Testo di supporto

- Una finestra di dialogo può visualizzare testo di supporto che fornisce ulteriori informazioni sullo scopo della finestra di dialogo. Questo in genere si trova in alto e può essere 1-2 frasi.

- La lunghezza della riga deve essere una larghezza comoda per l'utente da analizzare e leggere. Una finestra di dialogo media deve avere una larghezza non superiore a 550 pixel.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Pulsanti di comando interni
 Nelle finestre di dialogo più complesse, un controllo interno potrebbe avere i propri pulsanti correlati, che potrebbero influire sulla posizione dei pulsanti di commit della finestra di dialogo.

- Utilizzare un allineamento verticale (colonna) dei pulsanti interni quando **OK**/**Annulla** sono orientati orizzontalmente nell'angolo inferiore destro.

- Utilizzare un allineamento orizzontale (riga) dei pulsanti interni quando **OK**/**Annulla** sono orientati verticalmente nell'angolo superiore destro. Questa situazione è meno comune.

- Le dimensioni dei pulsanti interni devono essere rivolte alla dimensione standard del pulsante di 75x23 pixel, corrispondente alle dimensioni dei pulsanti **OK**/**Annulla** quando possibile. Se l'etichetta di un pulsante fa sì che il pulsante superi le dimensioni standard del pulsante, gli altri pulsanti in tale set devono essere allineati a quelle di dimensioni maggiori.

  ![Pulsanti OK e Annulla orizzontali](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08.01-f: Pulsanti Interni verticali con orizzontale OK/Annulla**

  ![Pulsanti OK e Annulla verticali](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08.01-g: Pulsanti interni orizzontali con verticale OK/Annulla**

#### <a name="browse-button"></a>[Sfoglia...] Pulsante
 **[Sfoglia...]** pulsanti che seguono una casella di testo dovrebbe scrivere "Sfoglia..." completamente, compresi i ellissi. Se lo spazio è ridotto o sono presenti più pulsanti **[Sfoglia...]** sullo schermo, il pulsante può essere ridotto solo ai solchi.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Layout della finestra di dialogo a tema
 Finestre di dialogo a tema in Visual Studio hanno un aspetto più leggero e offrono più spazio vuoto. La tipografia fornisce maggiore enfasi e interesse, offrendo un'interlinea più aperta e una variazione delle dimensioni e degli spessori dei caratteri. Se possibile, le barre cromate e del titolo sono state ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:The layout of these dialogs should follow this basic pattern:

1. Lo sfondo della finestra di dialogo è bianco.

2. È presente un bordo della regola di 1 pixel in un grigio valore intermedio.

3. Il titolo della finestra di dialogo non si trova più in una barra del titolo, ma fornisce interesse visivo e enfasi in una dimensione in punti più grande. Consultate la sezione relativa alla dimensione del carattere in [Stile testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Le etichette associate a testo aggiuntivo, ad esempio una descrizione, devono essere **Tipo di carattere ambiente , grassetto.**

5. Le colonne interne sono separate da una regola di 1 pixel in grigio chiaro.

6. I collegamenti predefiniti non hanno un segno di sottolineatura. Gli stati al passaggio del mouse e premuti hanno un cambiamento di colore più il sottolineatura.

7. I pulsanti di commit (ad esempio **OK**/**Annulla**) si esibiscono nell'angolo inferiore destro.

### <a name="themed-dialog-layout-examples"></a>Esempi di layout di finestre di dialogo a tema
 ![Layout della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08.01-h: finestra di dialogo a tema**

 ![Dimensioni della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08.01-i: Finestra di dialogo a tema - Dimensioni**

 ![Tipi di carattere della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08.01-j: Finestra di dialogo a tema - Tipi di carattere**

 ![Colori della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08.01-k: Finestra di dialogo a tema - Colori**

## <a name="see-also"></a>Vedere anche
- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controlli (Windows)](/windows/desktop/uxguide/controls)
- [Finestre di dialogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
