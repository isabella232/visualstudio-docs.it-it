---
title: Layout per Visual Studio | Microsoft Docs
description: Informazioni sul layout per le finestre di dialogo di Visual Studio, incluse le finestre di dialogo non con tema e le nuove finestre di dialogo con un aspetto con tema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16a4178231c575f590a13b8205cd872668f46143
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951940"
---
# <a name="layout-for-visual-studio"></a>Layout per Visual Studio
La maggior parte delle finestre di dialogo di Visual Studio è il [layout della finestra di dialogo utilità](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), ovvero le finestre di dialogo che seguono i principi standard di layout delle finestre di [dialogo desktop di Windows](/windows/desktop/uxguide/win-dialog-box). Quando Visual Studio si sposta per aggiornare l'interfaccia utente, alcune delle finestre di dialogo più importanti hanno un nuovo progetto che li definisce come esperienze di definizione dei prodotti. Il [layout della finestra di dialogo con tema](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) presenta un aspetto con tema.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Layout della finestra di dialogo utilità

- Tutti i controlli all'interno di una finestra di dialogo di utilità devono iniziare in alto a sinistra e scorrere verso il basso.

- Non centrare mai i controlli in una finestra di dialogo per riempire un'area di grandi dimensioni.

- Utilizzare il tipo di carattere ambiente per tutto il testo della finestra di dialogo. Quando si scrive una specifica visiva, specificare il tipo di carattere dell'ambiente anziché selezionare un tipo di carattere e una dimensione specifici. Vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utilizzare la spaziatura e la posizione di controllo coerenti per supportare l'obiettivo di qualità nell'artigianato.

- I dialoghi possono diventare più complessi da un numero maggiore di controlli, una giustapposizione univoca di controlli o entrambi. Per tali situazioni complesse, consentire agli utenti di analizzare un flusso logico tra i raggruppamenti dei controlli.

### <a name="utility-dialog-layout-examples"></a>Esempi di layout della finestra di dialogo utilità
 Tutte le dimensioni sono espresse come pixel.

 ![Spaziatura della finestra di dialogo per le etichette sopra i controlli](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08,01-a: linee guida per la spaziatura per le finestre di dialogo di utilità con etichette sopra i controlli**

 ![Spaziatura della finestra di dialogo per le etichette a sinistra dei controlli](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08,01-b: linee guida per la spaziatura per le finestre di dialogo di utilità con etichette a sinistra dei controlli**

### <a name="layout-details"></a>Dettagli layout

#### <a name="margins"></a>Margini

- Tutte le finestre di dialogo devono avere un bordo di 12 pixel intorno a tutti i bordi.

- I margini all'interno di un frame di gruppo devono essere di 9 pixel dal bordo del frame.

- I margini in un controllo struttura a schede devono essere di 6 pixel dal bordo del controllo struttura a schede.

#### <a name="command-buttons"></a>Pulsanti di comando

- I pulsanti di comando operano sulla cornice della finestra di dialogo, non sul contenuto. Devono essere posizionati in basso a destra e devono disporre di spazio variabile sufficiente per impostare i pulsanti in modo distinto.

- Se sono presenti pulsanti orizzontali che operano all'interno della finestra di dialogo, la configurazione del pulsante di comando alternativo è uno stack verticale in alto a destra. Vedere i [pulsanti di comando interni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) di seguito.

- Lo spazio a sinistra dei pulsanti di comando (in basso a sinistra/centrale della finestra di dialogo) viene considerato parte della "banda" dei controlli dell'operazione della finestra di dialogo. L'unica cosa che dovrebbe inserirsi su tale spazio è un collegamento alla guida rilevante per l'attività o la finestra di dialogo complessiva.

- I pulsanti di comando devono essere 75x23 pixel.

- I pulsanti di comando devono essere separati da 6 pixel.

  ![Allineamento di base dei pulsanti](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08,01-c: allineamento del pulsante di base**

#### <a name="labels"></a>Etichette

- Allinea a sinistra tutte le etichette.

- Per le etichette che si trovano sopra un controllo, devono essere allineate esattamente con il controllo sottostante e la parte inferiore dell'etichetta deve essere di 5 pixel al di sopra della parte superiore dell'altro controllo, ad esempio una casella combinata.

- Per le etichette che si trovano a sinistra dei controlli, la larghezza minima tra l'etichetta e il controllo di input è 10 pixel. È necessario stabilire una seconda colonna implicita per allineare le caselle di testo, le caselle combinate o altri controlli.

- Le etichette sono maiuscole e minuscole e sono seguite da due punti. Vedere [stile testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distanza tra i controlli
 Controlli dello stack ragionevolmente. Non esiste alcuna linea guida assoluta per la spaziatura tra i controlli in pila. La rigidità tra i controlli può variare leggermente tra le finestre di dialogo. La spaziatura consigliata è 20 pixel per le coppie di controllo/etichetta verticali e 9 pixel per le coppie di controllo/etichetta orizzontali. La spaziatura minima del controllo per le coppie orizzontali è 6 pixel.

 ![Distanza consigliata tra controlli](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08,01-d: suggerimenti per la distanza tra i controlli**

#### <a name="control-indentation"></a>Rientro del controllo
 Quando i controlli sono annidati, allineare orizzontalmente i controlli interni al bordo sinistro del controllo precedente, in genere l'etichetta.

 ![Allineamento dei controlli annidati](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08,01-e: allineamento del controllo annidato**

#### <a name="control-width"></a>Larghezza del controllo
 La larghezza di una casella di testo o altri controlli simili non devono essere più lunghi dell'input medio per il campo. La parola media inglese è di cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere purché il layout orizzontale consenta, mentre un elenco a discesa per i nomi di piattaforma deve essere solo una lunghezza che consente la voce più lunga.

#### <a name="helper-text"></a>Testo Helper

- In una finestra di dialogo è possibile visualizzare il testo dell'helper che fornisce ulteriori informazioni sullo scopo della finestra di dialogo. Si trova in genere nella parte superiore e può essere costituito da 1-2 frasi.

- La lunghezza della riga deve essere una larghezza comoda per l'analisi e la lettura da parte di un utente. Una finestra di dialogo Media non deve superare i 550 pixel di larghezza.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Pulsanti di comando interni
 Nelle finestre di dialogo più complesse, un controllo interno potrebbe avere i propri pulsanti correlati, che potrebbero influire sulla posizione in cui si trovano i pulsanti di commit della finestra di dialogo.

- Usare un allineamento verticale (colonna) di pulsanti interni quando **OK** / **Annulla** è orientato orizzontalmente nell'angolo inferiore destro.

- Usare un allineamento orizzontale (riga) dei pulsanti interni quando **OK** / **Annulla** sono orientati verticalmente nell'angolo superiore destro. Questa situazione è meno comune.

- Le dimensioni del pulsante interno devono avere come destinazione le dimensioni del pulsante standard di 75x23 pixel, quando possibile, corrispondenti alle dimensioni dei pulsanti **OK** / **Annulla** . Se l'etichetta di un pulsante consente di superare le dimensioni del pulsante standard, gli altri pulsanti del set devono essere allineati alla dimensione più ampia.

  ![Pulsanti OK e Annulla orizzontali](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08,01-f: pulsanti interni verticali con OK/Annulla orizzontali**

  ![Pulsanti OK e Annulla verticali](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08,01-g: pulsanti interni orizzontali con OK/Annulla verticale**

#### <a name="browse-button"></a>[Sfoglia...] pulsante
 **[Sfoglia...]** i pulsanti che seguono una casella di testo devono digitare "Sfoglia". completo, inclusi i puntini di sospensione. Se lo spazio è limitato o sono presenti più pulsanti **[Browse.** ..] sullo schermo, il pulsante può essere ridotto solo ai puntini di sospensione.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Layout della finestra di dialogo con tema
 Le finestre di dialogo con tema in Visual Studio hanno un aspetto più chiaro e offrono più spazio vuoto. La funzionalità tipografica offre maggiore enfasi e interesse, offrendo una maggiore interlinea di apertura e una variazione di dimensioni e pesi dei tipi di carattere. Laddove possibile, le barre Chrome e title sono state ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:

1. Lo sfondo della finestra di dialogo è bianco.

2. Il bordo di una regola da 1 pixel è in grigio di valore medio.

3. Il titolo della finestra di dialogo non si trova più in una barra del titolo, ma fornisce interesse visivo e enfasi in una dimensione del punto più grande. (Vedere la sezione relativa alle dimensioni del carattere nello [stile testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)).

4. Le etichette associate a testo aggiuntivo, ad esempio una descrizione, devono essere un **tipo di carattere ambiente + grassetto**.

5. Le colonne interne sono separate da una regola di 1 pixel in grigio chiaro.

6. I collegamenti predefiniti non hanno un carattere di sottolineatura. Gli Stati con passaggio del mouse e premuto hanno una modifica del colore e un carattere di sottolinea

7. I pulsanti di commit (ad esempio **OK** / **Annulla**) si trovano nell'angolo inferiore destro.

### <a name="themed-dialog-layout-examples"></a>Esempi di layout della finestra di dialogo con tema
 ![Layout della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08,01-h: finestra di dialogo con tema**

 ![Dimensioni della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08,01-i: finestra di dialogo con tema-dimensioni**

 ![Tipi di carattere della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08,01-j: finestra di dialogo con tema-tipi di carattere**

 ![Colori della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08,01-k: finestra di dialogo con tema-colori**

## <a name="see-also"></a>Vedi anche
- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controlli (Windows)](/windows/desktop/uxguide/controls)
- [Finestre di dialogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
