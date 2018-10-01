---
title: Layout per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25ba43a08bc2c886302894d891800ac1db87a18a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527653"
---
# <a name="layout-for-visual-studio"></a>Layout per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Layout per Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/layout-for-visual-studio).  
  
La maggior parte delle finestre di dialogo di Visual Studio [layout di finestra di dialogo utilità](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), che sono il unthemed finestre di dialogo standard di seguire [principi di layout di finestra di dialogo Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx). Mentre Visual Studio viene spostato alla relativa interfaccia utente di aggiornamento, alcune delle finestre di dialogo più evidenti sono una nuova progettazione che stabilisce le esperienze di definizione del prodotto. Questi [layout di finestra di dialogo con tema](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) hanno un aspetto a tema.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Layout di finestra di dialogo utilità  
  
-   Tutti i controlli all'interno di una finestra di dialogo utilità devono iniziare in alto/a sinistra e verso il basso del flusso.  
  
-   Center mai i controlli in una finestra di dialogo per riempire una vasta area.  
  
-   Usare il tipo di carattere ambiente per tutto il testo della finestra. Quando si scrive una specifica di visual, specificare il tipo di carattere ambiente invece di selezionare un particolare tipo di carattere e dimensioni. Visualizzare [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Usare controllo coerenti con spaziatura e posizionamento per supportare l'obiettivo per la qualità in maestria.  
  
-   Le finestre di dialogo può diventare più complesse da un numero maggiore di controlli, un contatto univoca dei controlli o entrambi. Per tali situazioni complicate, consentire spazio sufficiente tra i raggruppamenti di controllo per consentire all'utente un flusso logico da analizzare.  
  
### <a name="utility-dialog-layout-examples"></a>Esempi di layout di finestra di dialogo utilità  
 Tutte le dimensioni vengono espresse in pixel.  
  
 ![Spaziatura della finestra di dialogo per le etichette sopra i controlli](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **Figura 08.01-r: Linee guida per la spaziatura per le finestre di dialogo utilità con etichette sopra i controlli**  
  
 ![Spaziatura della finestra di dialogo per le etichette a sinistra dei controlli](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **Figura 08.01-b: Linee guida per la spaziatura per le finestre di dialogo utilità con etichette a sinistra dei controlli**  
  
### <a name="layout-details"></a>Dettagli del layout  
  
#### <a name="margins"></a>Margini  
  
-   Tutti i dialoghi devono avere un bordo di 12 pixel intorno ai lati.  
  
-   Margini all'interno di un gruppo devono essere 9 pixel dal bordo del frame.  
  
-   Margini all'interno di un controllo struttura a schede devono essere 6 pixel dal bordo del controllo scheda.  
  
#### <a name="command-buttons"></a>Pulsanti di comando  
  
-   Pulsanti di comando operano su frame di finestra di dialogo non sul contenuto. Che deve essere inseriti nella parte inferiore destra e deve avere sufficiente spazio delle variabili precedente per impostare i pulsanti nettamente separata.  
  
-   Se sono presenti pulsanti orizzontali che operano all'interno della finestra di dialogo, la configurazione di pulsante di comando alternativo è uno stack verticale nell'angolo superiore destro. Visualizzare [pulsanti di comando interni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) sotto.  
  
-   Lo spazio a sinistra dei pulsanti di comando (più basso a sinistra o al centro della finestra di dialogo) viene considerato parte della "banda" dei controlli di finestra di dialogo operazione. L'unica cosa che dovrebbe ostacolano lo spazio è un collegamento alla Guida che è rilevante per l'attività generale o la finestra di dialogo.  
  
-   Pulsanti di comando devono essere 75 x 23 pixel.  
  
-   Pulsanti di comando devono essere 6 pixel di distanza.  
  
 ![Allineamento di base dei pulsanti](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801 c_ButtonAlign")  
  
 **08.01 figura c: Allineamento di base dei pulsanti**  
  
#### <a name="labels"></a>Etichette  
  
-   Allinea a sinistra tutte le etichette.  
  
-   Per le etichette al di sopra un controllo, si devono allineare a sinistra con precisione con il controllo sotto di essa e la parte inferiore dell'etichetta deve essere 5 pixel oltre il margine superiore di altro controllo (ad esempio, una casella combinata).  
  
-   Per le etichette che si trovano a sinistra dei controlli, la larghezza minima tra l'etichetta e il controllo di input è di 10 pixel. Una colonna implicita secondo deve essere stabilita per allineare le caselle di testo, caselle combinate o altri controlli.  
  
-   Le etichette maiuscola e sono seguite da due punti. Visualizzare [stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distanza tra i controlli  
 Sovrapporre controlli ragionevolmente. Non vi è alcun assoluti delle linee guida per la spaziatura tra i controlli in pila. Il livello tra i controlli può variare leggermente tra le finestre di dialogo. La spaziatura consigliata è 20 pixel per le coppie etichetta/controllo verticali e 9 pixel per le coppie etichetta/controllo orizzontale. La spaziatura minima di controlli per le coppie orizzontale è 6 pixel.  
  
 ![Distanza tra i controlli consigliati](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801 d_ControlDistance")  
  
 **Figura 08.01-d: Indicazioni per la distanza tra i controlli**  
  
#### <a name="control-indentation"></a>Rientro di controllo  
 Quando i controlli sono nidificati, allineare i controlli interni in senso orizzontale con il bordo sinistro del controllo precedente, in genere l'etichetta.  
  
 ![Allineamento dei controlli annidati](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801 e_ControlAlign")  
  
 **Figura 08.01-e: Allineamento dei controlli annidati**  
  
#### <a name="control-width"></a>Larghezza del controllo  
 La larghezza di una casella di testo o altri controlli simili deve essere composto l'input medio per il campo. La parola inglese Media è di cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere a condizione che consente il layout orizzontale, mentre un elenco a discesa di nomi di piattaforma devono essere solo una lunghezza che consente la voce più lunga.  
  
#### <a name="helper-text"></a>Testo di supporto  
  
-   Una finestra di dialogo è possibile visualizzare il testo di supporto che fornisce informazioni aggiuntive sullo scopo della finestra di dialogo. Ciò in genere si trova nella parte superiore e può essere 1 o 2 frasi.  
  
-   La lunghezza di riga deve essere una larghezza comoda per un utente di analizzare e di lettura. Una finestra di dialogo medio deve essere non più di 550 pixel di larghezza.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Pulsanti di comando interni  
 Nelle finestre di dialogo più complessi, un controllo interno potrebbe essere relativi pulsanti correlate, che possono influire in cui si trovano i pulsanti di commit della finestra di dialogo.  
  
-   Usare i pulsanti quando l'allineamento verticale (colonna) della parte interna **OK**/**Annulla** è orientato in senso orizzontale nell'angolo inferiore destro.  
  
-   Usare i pulsanti quando l'allineamento orizzontale (riga) della parte interna **OK**/**Annulla** è orientato in senso verticale in alto a destra. Questa situazione è meno comune.  
  
-   Dimensioni del pulsante interni devono avere come destinazione le dimensioni del pulsante standard di 75 x 23 pixel, corrispondenti le dimensioni di **OK**/**Annulla** pulsanti quando possibile. Se un'etichetta del pulsante effettua il pulsante superano le dimensioni del pulsante standard, gli altri pulsanti in tale set devono essere allineate con tale dimensione più ampia.  
  
 ![Pulsanti OK e Annulla orizzontali](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801 f_HorizOKCan")  
  
 **Figura 08.01-f: I pulsanti interno verticale con OK/Annulla orizzontale**  
  
 ![Pulsanti OK e Annulla verticali](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801 g_VertOKCan")  
  
 **Figura 08.01-g: Pulsanti interni orizzontali con OK/Annulla verticale**  
  
#### <a name="browse-button"></a>[Sfoglia...] pulsante  
 **[Sfoglia...]**  pulsanti che seguono una casella di testo devono spiegare chiaramente "Sfoglia..." in modo completo, inclusi i puntini di sospensione. Se lo spazio è insufficiente o ci sono più **[Sfoglia...]**  pulsanti sullo schermo, il pulsante possono essere ridotto a semplicemente i puntini di sospensione.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Layout di finestra di dialogo con tema  
 Finestre di dialogo con tema in Visual Studio hanno un aspetto più chiaro e offrire più spazio vuoto. Funzionalità tipografiche fornisce ulteriori enfasi e interesse, offre più aperta l'interlinea e una variante dei pesi e le dimensioni dei caratteri. Dove possibile, le barre del titolo e chrome sono state ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:  
  
1.  Lo sfondo della finestra di dialogo è bianco.  
  
2.  In un grigio medio valore è presente un bordo regola 1 pixel.  
  
3.  Non è più il titolo della finestra di dialogo si trova in una barra del titolo, ma fornisce l'interesse visivo ed enfasi un aumento delle dimensioni del punto. (Vedere la sezione di dimensioni del carattere in [stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Devono essere associate testo aggiuntivo, ad esempio una descrizione, le etichette **tipo di carattere ambiente + grassetto**.  
  
5.  Colonne interne sono separate da una regola di 1 pixel in grigio chiaro.  
  
6.  Collegamenti predefiniti non hanno nessun carattere di sottolineatura. Al passaggio del mouse e premuti stati dispongono di una modifica del colore e un carattere di sottolineatura.  
  
7.  Eseguire il commit pulsanti (ad esempio **OK**/**Annulla**) si trovano nell'angolo inferiore destro.  
  
### <a name="themed-dialog-layout-examples"></a>Esempi di layout di finestra di dialogo con tema  
 ![Layout di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801 h_ThemedDialog")  
  
 **Figura 08.01-h: Finestra di dialogo con tema**  
  
 ![Le dimensioni di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **Figura 08.01-ricerca per categorie: Finestra di dialogo con tema – dimensioni**  
  
 ![I tipi di carattere di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **Figura 08.01-j: Finestra di dialogo con tema: i tipi di carattere**  
  
 ![I colori di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **Figura 08.01-k: Finestra di dialogo con tema: colori**  
  
## <a name="see-also"></a>Vedere anche  
 [Modelli di applicazione per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controlli (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Finestre di dialogo (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)

