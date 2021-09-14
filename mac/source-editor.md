---
title: Editor standard
description: Uso dell'editor standard in Visual Studio per Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: c4a22ec0765c39a8bec83f9e2acff7b22b706890
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710473"
---
# <a name="source-editor"></a>Editor standard

Un editor standard affidabile è essenziale per scrivere codice in modo conciso ed efficiente. Visual Studio per Mac offre un editor standard sofisticato, centrale per le interazioni con l'ambiente di sviluppo integrato. L'editor standard offre funzionalità necessarie per lavorare in modo agevole: da funzioni di base, come ad esempio evidenziazione della sintassi, frammenti di codice e riduzione del codice, ai vantaggi derivanti dall'integrazione del compilatore Roslyn, ad esempio il completamento di codice completamente funzionale IntelliSense.

L'editor standard in Visual Studio per Mac consente un'esperienza ottimale di uso di tutte le altre funzionalità nell'IDE, ad esempio debug, refactoring e integrazione del controllo della versione.

Questo articolo presenta alcune delle funzionalità chiave dell'editor standard e illustra come è possibile usare Visual Studio per Mac nel modo più produttivo possibile.

## <a name="the-source-editor-experience"></a>Esperienza d'uso dell'editor standard

L'efficienza di visualizzazione e di spostamento nel codice è una parte essenziale del flusso di lavoro di sviluppo. Il modo esatto in cui si desidera visualizzare e gestire il codice è una decisione personale che varia da uno sviluppatore all'altro e spesso anche tra un progetto e l'altro.

Visual Studio per Mac offre molte funzionalità potenti per rendere lo sviluppo multipiattaforma il più accessibile e utile possibile. Le sezioni seguenti descrivono alcune delle caratteristiche principali.

## <a name="code-folding"></a>Riduzione del codice

La riduzione del codice agevola la gestione di file di codice sorgente di grandi dimensioni consentendo agli sviluppatori di mostrare o nascondere intere sezioni di codice, ad esempio direttive, codice e commenti boilerplate e istruzioni #region. La riduzione del codice è disattivata per impostazione predefinita in Visual Studio per Mac

Per attivare la riduzione del codice, spostarsi su **Visual Studio > Preferenze > Editor di testo > Generale > Riduzione del codice**:

![Opzioni di riduzione del codice](media/source-neweditor-image1.png)

Questo menu include anche l'opzione per ridurre #region e commenti per impostazione predefinita, visualizzando un hint denominato anziché il codice.

Per mostrare o nascondere sezioni, usare il widget di divulgazione accanto al numero di riga:

![Mostrare o nascondere sezioni nel codice](media/source-neweditor-image2.png)

È anche possibile selezionare alternativamente se visualizzare o nascondere le riduzioni, usando la voce di menu **Visualizza > Riduzione > Toggle Fold / Toggle All Folds (Attiva riduzione / Attiva/disattiva tutte le riduzioni)**:

![Voce di menu Riduzione](media/source-editor-image19.png)

Questa voce di menu può anche essere usata per abilitare o disabilitare la riduzione del codice.

## <a name="word-wrap"></a>A capo automatico

Il ritorno a capo automatico consente di gestire lo spazio quando si lavora su lunghe righe di codice o con spazio di visualizzazione limitato. Il ritorno a capo automatico può inoltre garantire che la visualizzazione del codice includa tutto il contenuto del file di origine anche quando si aprono riquadri che potrebbero nascondere la visualizzazione o ridurre la larghezza della visualizzazione origine. 

Il ritorno a capo automatico è disabilitato per impostazione predefinita, ma può essere abilitato tramite **Preferenze** in Visual Studio per Mac. 

Per abilitare il ritorno a capo automatico, passare a Visual Studio > Preferenze > editor di **testo > ritorno a capo automatico:**

![Opzioni di ritorno a capo automatico](media/source-neweditor-wordwrap1.png)

Se il ritorno a capo automatico è abilitato, le righe che superano la larghezza della visualizzazione dell'editor standard passano automaticamente alla riga successiva all'interno del file di origine. È anche possibile abilitare un'opzione che visualizza un glifo accanto alle righe con ritorno a capo. Ciò consente di distinguere tra le righe con ritorno a capo automatico e quelle con ritorno a capo impostato manualmente.

![Testo con ritorno a capo con funzionalità di ritorno a capo automatico abilitata](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Righello

Il righello per le colonne è utile per determinare le lunghezze delle righe, in particolare quando si lavora in un team che ha linee guida per tali lunghezze. Per attivare o disattivare il righello per le colonne, passare a **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli** e selezionare (o deselezionare) **Show Column ruler** (Mostra righello per le colonne), come illustrato nell'immagine seguente:

![Finestra di dialogo Preferenze con opzione "show column ruler" evidenziata](media/source-editor-image5.png)

 Verrà visualizzata una linea grigia verticale nell'editor standard.

## <a name="highlight-identifier-references"></a>Evidenzia riferimenti identificatore

Quando l'opzione "Highlight identifier references (Evidenzia riferimenti identificatore)" è attivata, è possibile selezionare qualsiasi simbolo nel codice sorgente e l'editor offrirà una guida visiva per tutti gli altri riferimenti in tale file. Per attivare questa opzione, passare a **Visual Studio > Preferenze > Editor di testo > Marcatori e righelli** e selezionare _Highlight identifier references_ (Evidenzia riferimenti identificatore), come illustrato nell'immagine seguente:

![Finestra di dialogo Preferenze con opzione "Highlight identifier references" evidenziata](media/source-editor-image6.png)

Anche il colore dell'evidenziazione è utile per indicare che qualcosa è assegnato o referenziato. Se qualcosa è assegnato, è evidenziato in rosso, se qualcosa è referenziato, è evidenziato in blu:

![esempio che illustra il colore dell'evidenziazione](media/source-editor-image7.png)

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor del codice (Visual Studio in Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Struttura (Visual Studio in Windows)](/visualstudio/ide/outlining)
