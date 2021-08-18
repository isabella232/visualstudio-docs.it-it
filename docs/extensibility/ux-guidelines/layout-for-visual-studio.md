---
title: Layout per Visual Studio | Microsoft Docs
description: Informazioni sul layout per Visual Studio finestre di dialogo, inclusi i dialoghe non intemed e i nuovi dialoghe con un aspetto a base di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ce29e7f2d8d75cf60423cbb65ca3b2da449e4c6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094542"
---
# <a name="layout-for-visual-studio"></a>Layout per Visual Studio
La maggior parte dei dialog Visual Studio è il [layout](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)della finestra di dialogo utilità , ovvero le finestre di dialogo non inteme che seguono i principi di layout Windows [di dialogo](/windows/desktop/uxguide/win-dialog-box)desktop. Quando Visual Studio per aggiornare l'interfaccia utente, alcune delle finestre di dialogo più importanti hanno una nuova progettazione che le definisce esperienze di definizione del prodotto. Il [layout della finestra di dialogo](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) a t-to-tato ha un aspetto a base di testo.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Layout della finestra di dialogo utilità

- Tutti i controlli all'interno di una finestra di dialogo dell'utilità devono iniziare in alto/a sinistra e scorrere verso il basso.

- Non centrare mai i controlli in una finestra di dialogo per riempire un'area di grandi dimensioni.

- Usare il tipo di carattere dell'ambiente per tutto il testo della finestra di dialogo. Quando si scrive una specifica visiva, specificare il tipo di carattere dell'ambiente anziché selezionare un tipo di carattere e una dimensione specifici. Vedere [Il tipo di carattere dell'ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Usare una spaziatura di controllo e un posizionamento coerenti per supportare l'obiettivo della qualità nell'uso manuale.

- I dialoghe possono diventare più complessi da un numero maggiore di controlli, da una combinazione univoca di controlli o da entrambi. Per queste situazioni complesse, consentire uno spazio adeguato tra i raggruppamenti di controllo per fornire all'utente un flusso logico da analizzare.

### <a name="utility-dialog-layout-examples"></a>Esempi di layout della finestra di dialogo utilità
 Tutte le dimensioni sono espresse in pixel.

 ![Spaziatura della finestra di dialogo per le etichette sopra i controlli](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08.01-a: Linee guida sulla spaziatura per le finestre di dialogo dell'utilità con etichette sopra i controlli**

 ![Spaziatura della finestra di dialogo per le etichette a sinistra dei controlli](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08.01-b: Linee guida sulla spaziatura per le finestre di dialogo dell'utilità con etichette a sinistra dei controlli**

### <a name="layout-details"></a>Dettagli del layout

#### <a name="margins"></a>Margini

- Tutti i dialognti devono avere un bordo di 12 pixel intorno a tutti i bordi.

- I margini all'interno di un frame di gruppo devono essere di 9 pixel dal bordo del frame.

- I margini all'interno di un controllo Struttura a schede devono essere di 6 pixel dal bordo del controllo struttura a schede.

#### <a name="command-buttons"></a>Pulsanti di comando

- I pulsanti di comando operano sulla cornice della finestra di dialogo, non sul contenuto. Devono essere posizionati in basso a destra e devono avere spazio variabile sufficiente sopra per impostare i pulsanti distintamente separati.

- Se sono presenti pulsanti orizzontali che operano all'interno della finestra di dialogo, la configurazione alternativa del pulsante di comando è uno stack verticale in alto a destra. Vedere [Pulsanti di comando interni di](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) seguito.

- Lo spazio a sinistra dei pulsanti di comando (in basso a sinistra/al centro della finestra di dialogo) è considerato parte della "banda" dei controlli delle operazioni del dialogo. L'unico elemento che deve intromettersi in tale spazio è un collegamento alla Guida pertinente per l'attività o la finestra di dialogo complessiva.

- I pulsanti di comando devono essere di 75 x 23 pixel.

- I pulsanti di comando devono essere separati da 6 pixel.

  ![Allineamento di base dei pulsanti](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08.01-c: Allineamento dei pulsanti di base**

#### <a name="labels"></a>Etichette

- Allinea a sinistra tutte le etichette.

- Per le etichette che siedono sopra un controllo, devono allinearsi a sinistra esattamente con il controllo sottostante e la parte inferiore dell'etichetta deve essere 5 pixel sopra la parte superiore dell'altro controllo (ad esempio, una casella combinata).

- Per le etichette a sinistra dei controlli, la larghezza minima tra l'etichetta e il controllo di input è di 10 pixel. Deve essere stabilita una seconda colonna implicita per allineare le caselle di testo, le caselle combinate o altri controlli.

- Le etichette sono maiuscole e minuscole e sono seguite da due punti. Vedere [Stile del testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Distanza tra i controlli
 Controlli stack ragionevolmente. Non esistono linee guida assolute per la spaziatura tra i controlli in pila. La stretta tra i controlli può variare leggermente tra i dialoghe. La spaziatura consigliata è di 20 pixel per le coppie controllo/etichetta verticale e 9 pixel per le coppie controllo/etichetta orizzontali. La spaziatura minima del controllo per le coppie orizzontali è di 6 pixel.

 ![Distanza consigliata tra controlli](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08.01-d: Consigli per la distanza tra i controlli**

#### <a name="control-indentation"></a>Rientro del controllo
 Quando i controlli sono annidati, allineare orizzontalmente i controlli interni al bordo sinistro del controllo precedente, in genere l'etichetta.

 ![Allineamento dei controlli annidati](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08.01-e: Allineamento dei controlli annidati**

#### <a name="control-width"></a>Larghezza del controllo
 La larghezza di una casella di testo o di altri controlli simili non deve essere superiore all'input medio per il campo. La parola inglese media è di cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere quella consentita dal layout orizzontale, mentre un elenco a discesa per i nomi di piattaforma deve essere solo una lunghezza che consenta l'immissione più lunga.

#### <a name="helper-text"></a>Testo helper

- Una finestra di dialogo può visualizzare testo helper che fornisce altre informazioni sullo scopo della finestra di dialogo. In genere si trova nella parte superiore e può essere di 1-2 frasi.

- La lunghezza della riga deve essere una larghezza comoda che un utente può analizzare e leggere. Una finestra di dialogo media non deve avere una larghezza superiore a 550 pixel.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Pulsanti di comando interni
 Nelle finestre di dialogo più complesse, un controllo interno potrebbe avere pulsanti correlati, che potrebbero influire sulla posizione in cui si trovano i pulsanti di commit del dialogo.

- Usare un allineamento verticale (colonna) dei pulsanti interni quando **OK** / **Annulla** è orientato orizzontalmente nell'angolo inferiore destro.

- Usare un allineamento orizzontale (riga) dei pulsanti interni quando **OK** / **Annulla** è orientato verticalmente nell'angolo superiore destro. Questa situazione è meno comune.

- Le dimensioni dei pulsanti interni devono avere come destinazione le dimensioni standard del pulsante di 75x23 pixel, corrispondenti alle dimensioni dei pulsanti **OK** / **Annulla,** se possibile. Se un'etichetta di pulsante fa in modo che il pulsante superi le dimensioni standard del pulsante, gli altri pulsanti nel set devono essere allineati a tale dimensione più ampia.

  ![Pulsanti OK e Annulla orizzontali](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08.01-f: Pulsanti interni verticali con OK/Annulla orizzontali**

  ![Pulsanti OK e Annulla verticali](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08.01-g: Pulsanti interni orizzontali con OK/Annulla verticale**

#### <a name="browse-button"></a>[Sfoglia...] Pulsante
 **[Sfoglia...]** I pulsanti che seguono una casella di testo devono digitare "Sfoglia..." in modo completo, inclusi i puntini di sospensione. Se lo spazio è ridotto o sono presenti più **pulsanti [Sfoglia...]** sullo schermo, il pulsante può essere ridotto solo ai puntini di sospensione.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Layout della finestra di dialogo a t-to-tato
 Le finestre di dialogo a Visual Studio hanno un aspetto più chiaro e offrono più spazio vuoto. La tipografia offre maggiore enfasi e interesse, offrendo un'interlinea più aperta e una variazione delle dimensioni e dei pesi dei caratteri. Laddove possibile, le barre del titolo e del colore sono state ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:

1. Lo sfondo del dialogo è bianco.

2. È presente un bordo regola di 1 pixel in un grigio medio.

3. Il titolo della finestra di dialogo non si trova più in una barra del titolo, ma offre interesse visivo e enfasi in dimensioni in punti più grandi. Vedere la sezione relativa alle dimensioni del carattere in [Stile testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Le etichette abbinate a testo aggiuntivo, ad esempio una descrizione, devono essere **Carattere ambiente + Grassetto.**

5. Le colonne interne sono separate da una regola di 1 pixel in grigio chiaro.

6. I collegamenti predefiniti non hanno caratteri di sottolineatura. Gli stati di passaggio del mouse e premuto hanno una modifica del colore e un carattere di sottolineatura.

7. I pulsanti commit (ad **esempio OK** / **Annulla)** siedono nell'angolo inferiore destro.

### <a name="themed-dialog-layout-examples"></a>Esempi di layout di finestre di dialogo con tate
 ![Layout della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08.01-h: Finestra di dialogo con tuffi**

 ![Dimensioni della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08.01-i: Finestra di dialogo con tuffi - Dimensioni**

 ![Tipi di carattere della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08.01-j: finestra di dialogo Con tema - Tipi di carattere**

 ![Colori della finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08.01-k: finestra di dialogo con tema - Colori**

## <a name="see-also"></a>Vedi anche
- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controlli (Windows)](/windows/desktop/uxguide/controls)
- [Finestre di dialogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
