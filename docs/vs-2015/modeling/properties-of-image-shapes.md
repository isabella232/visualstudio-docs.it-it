---
title: Proprietà delle forme immagine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 79ec5470a8bac83d8e60454c984739f1e520b634
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671381"
---
# <a name="properties-of-image-shapes"></a>Proprietà delle forme d'immagine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare le forme immagine per specificare la modalità di visualizzazione delle classi di dominio in una finestra di progettazione generata. Definire una forma immagine impostando la proprietà `Image` della classe su un file di immagine predefinito. Sono supportati i formati seguenti:

- .gif

- . jpg

- . jpeg

- . bmp

- WMF

- . EMF

- .png

  Per impostazione predefinita, i file di risorse della finestra di progettazione, ad esempio i file di immagine, si trovano nella cartella **risorse** del progetto **DSL** .

  Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

  Le forme immagine hanno le proprietà elencate nella tabella seguente.

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Colore riempimento|Colore di riempimento di questa forma.|bianco|
|Modalità gradiente riempimento|Modalità di sfumatura riempimento di questa forma.|Orizzontale|
|Con punti di connessione predefiniti|Se `True`, la forma utilizzerà i punti di connessione superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|False|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggiato contorno|Stile di tratteggio del contorno di questa forma (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto o personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Modificatore di accesso della forma geometrica (Public o Internal).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questa forma.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla forma dell'immagine (`none`, `abstract` o `sealed`).|none|
|Forma immagine di base|Classe di base di questa forma.|(nessuno)|
|Name|Nome di questa forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Posizione in cui è definita la descrizione comando (fixed, variable o None). Se è fixed, il valore della proprietà `Fixed Tooltip Text` viene usato come descrizione comando; Se variabile, la descrizione comando è definita nel codice personalizzato.|none|
|Note|Note informali associate a questa forma.|\<nessuno>|
|Altezza iniziale|Altezza iniziale di questa forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1.5|
|Colore riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposta<br /><br /> Colore struttura esposto come proprietà<br /><br /> Stile tratteggiato del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|False|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<nessuno>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo elemento.|\<nessuno>|
|Immagine|Percorso del file di immagine usato per la forma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
