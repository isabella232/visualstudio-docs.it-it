---
title: Personalizzazione dell'IDE
description: È possibile personalizzare Visual Studio per Mac in diversi modi, consentendo agli utenti di sviluppare app in un ambiente in grado di soddisfare sia le esigenze di efficienza che quelle estetiche. Questo articolo illustra i diversi modi in cui Visual Studio per Mac adattabili in base alle esigenze.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: 710f4f9b941719deecbc516ba4d14a1976f3fcfb312b341fd915b0f5c4acb1c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439381"
---
# <a name="customizing-the-ide"></a>Personalizzazione dell'IDE

Visual Studio per Mac possono essere personalizzate, consentendo agli utenti di sviluppare app in un ambiente che soddisfi le proprie esigenze di efficienza ed etica. Questo articolo esamina i diversi modi in cui è possibile adattare Visual Studio per Mac alle proprie esigenze.

## <a name="dark-theme"></a>Tema scuro

![Visualizzazione tema scuro](media/customizing-the-ide-image7a.png)

Per cambiare tema in Visual Studio per Mac, scegliere **Visual Studio > Preferenze > Ambiente > Stile di visualizzazione** e selezionare il tema desiderato nell'elenco a discesa **Tema dell'interfaccia utente**, come illustrato nell'immagine seguente:

![Selezione del tema scuro](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localizzazione

Visual Studio per Mac è disponibile nelle 14 lingue seguenti ed è quindi accessibile a un maggior numero di sviluppatori:

* Cinese (Cina)
* Cinese (Taiwan)
* Ceco
* Francese
* Tedesco
* Inglese
* Italiano
* Giapponese
* Coreano
* Polacco
* Portoghese (Brasile)
* Russo
* Spagnolo
* Turco

Per cambiare la lingua visualizzata da Visual Studio per Mac, scegliere **Visual Studio > Preferenze > Ambiente > Stile di visualizzazione** e selezionare la lingua desiderata nell'elenco a discesa **Lingua dell'interfaccia utente**, come illustrato nell'immagine seguente:

![Selezione lingua](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informazioni sull'autore

Il pannello Informazioni sull'autore consente all'utente di aggiungere informazioni personali pertinenti manualmente, ad esempio il nome, l'indirizzo di posta elettronica, il titolare del copyright per il lavoro, la società e il marchio:

![Sezione di modifica delle informazioni sull'autore](media/customizing-the-ide-image9a.png)

Queste informazioni vengono usate per popolare le intestazioni standard dei file, ad esempio le licenze, che è possibile aggiungere ai nuovi file:

![Opzioni per le intestazioni standard](media/customizing-the-ide-image8a.png)

I campi **Nome** e **Posta elettronica** vengono usati in tutti i commit eseguiti tramite il controllo della versione in Visual Studio per Mac. Se questi campi non sono stati popolati, Visual Studio per Mac verrà richiesto di farlo quando si tenta di usare il controllo della versione.

## <a name="key-bindings"></a>Associazioni di chiave

I tasti di scelta rapida, o tasti di scelta rapida, consentono di adattare l'ambiente di sviluppo in modo che sia possibile spostarsi in modo più efficiente in Visual Studio per Mac. Sono disponibili tasti di scelta rapida familiari presenti nelle interfacce IDE più diffuse, ad esempio Visual Studio (in Windows), ReSharper, Visual Studio Code e Xcode.

Per impostare tasti di scelta rapida, passare a **Visual Studio > Preferenze > Ambiente > Tasti di scelta rapida**, come illustrato nell'immagine seguente:

![Impostare tasti di scelta rapida](media/customizing-the-ide-image10a.png)

Da qui è possibile cercare combinazioni di tasti di scelta rapida, visualizzare tasti di scelta rapida in conflitto, aggiungere nuovi tasti di scelta rapida e modificare quelli esistenti.

Queste associazioni possono essere impostate anche durante la configurazione iniziale Visual Studio per Mac, tramite la schermata **Selezione tastiera:**

![Impostare i tasti di scelta, prima esecuzione](media/ide-tour-2019-keyboard-shortcut.png)

## <a name="workspace-layout"></a>Layout area di lavoro

L'area di lavoro di Visual Studio per Mac è costituita da un'area del documento principale  (in genere l'editor, l'area di progettazione o il file di opzioni), racchiusa tra finestre degli strumenti complementari che contengono informazioni utili per l'accesso e la gestione dei file dell'applicazione, il test e il debug.

 ![Layout area di lavoro](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-tool-windows"></a>Visualizzazione e disposizione delle finestre degli strumenti

Quando si apre una nuova soluzione o un nuovo  file in Visual Studio per Mac, si noteranno alcune finestre degli strumenti nell'area di lavoro, tra cui la finestra della soluzione, la struttura del documento e gli errori:

![Finestra degli strumenti](media/customizing-the-ide-image2a.png)

Visual Studio per Mac offre finestre degli strumenti contenenti informazioni aggiuntive, strumenti e strumenti di navigazione, a cui è possibile accedere esplorando la voce di **menu** Visualizza e selezionando una finestra degli strumenti per aggiungerla:

![Selezionare una nuova finestra degli strumenti](media/customizing-the-ide-image3a.png)

Le Windows possono anche essere aperte automaticamente da vari comandi, ad esempio il comando Cerca **nei** file (MAIUSC+CMD+F), che apre una finestra disconnessa dei risultati della ricerca.

Gli Windows possono essere spostati e disposti in tutto il flusso di lavoro nel modo più utile possibile. Ad esempio, possono essere ancorati su qualsiasi lato dell'editor di documenti, accanto a un'altra finestra degli strumenti, sopra o sotto un'altra finestra o come un set di finestre a schede che consentono di passare rapidamente da una finestra all'altra.

Per le finestre degli strumenti usate di frequente, è anche possibile scollegarle completamente dalla finestra Visual Studio per Mac e nella nuova finestra.

I Windows possono essere aggiunti e chiusi dai controlli nell'angolo superiore destro di ogni finestra:

:::image type="content" source="media/customizing-the-ide-image5a.png" alt-text="Uso dei controlli per bloccare o chiudere le finestre degli strumenti":::

Le finestre bloccate sono ancorate ai lati dell'area di lavoro e rimangono aperte per un accesso più rapido quando necessario. Le finestre non bloccate sono ancorate, ma non vengono visualizzate fino a quando non si passa il mouse sulla scheda della finestra con il mouse o lo stato attivo con la tastiera; possono essere nascosti quando lo stato attivo del mouse e della tastiera li lascia.

### <a name="organizing-layouts"></a>Organizzazione dei layout

Le finestre degli strumenti visualizzate in qualsiasi momento dipendono dal contesto corrente. Ad esempio, quando si usa la finestra di progettazione visiva, le finestre della casella degli strumenti e della griglia delle proprietà sono più importanti. Durante il debug, è utile disporre delle finestre del debugger per visualizzare lo stack e le variabili locali.

Lo stato delle finestre degli strumenti aperte è rappresentato da un *layout*. I layout possono essere alternati manualmente tramite il menu Visualizza, come illustrato nell'immagine seguente, oppure automaticamente quando si esegue un'azione, ad esempio il debug o l'apertura di uno storyboard:

![Selezione di nuovi layout](media/customizing-the-ide-image6b.png)

È possibile creare un nuovo layout usando la voce di menu **> layout** > Salva layout corrente. Questo comando aggiungerà il layout corrente al menu in modo che sia possibile selezionarlo in qualsiasi momento:

![Salva layout corrente](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Supporto della modifica affiancata

Visual Studio per Mac consente di affiancare diversi editor di testo aperti o di visualizzare un editor in una finestra mobile scollegata.

La modalità a due colonne può essere abilitata tramite la voce di menu Visualizza selezionando Visualizza colonne dell'editor **> > 2** colonne oppure trascinando una scheda dell'editor su uno dei bordi dell'area dell'editor:

![Modalità due colonne affiancate](media/customizing-the-ide-sbs.png)

Le schede dell'editor possono essere trascinate fuori dall'area del documento per creare una finestra dell'editor mobile. Anche la finestra mobile supporta editor affiancati e può contenere diverse schede dell'editor:

![Creare una nuova finestra](media/customizing-the-ide-sbs1.png)

![Due colonne affiancate con schede aggiuntive](media/customizing-the-ide-sbs2.png)

Per tornare a un solo editor aperto, selezionare **Vista > Colonne editor > Una colonna**.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>Vedi anche

- [Personalizzare l'IDE di Visual Studio (in Windows)](/visualstudio/ide/personalizing-the-visual-studio-ide)