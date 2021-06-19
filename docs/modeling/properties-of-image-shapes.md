---
title: Proprietà delle forme d'immagine
description: Informazioni sulle forme immagine e su come è possibile usare le forme immagine per specificare la modalità di visualizzazione delle classi di dominio in una finestra di progettazione generata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98198b1197de6f5fda6a05a5bae58378a323f718
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390555"
---
# <a name="properties-of-image-shapes"></a>Proprietà delle forme d'immagine

È possibile usare forme immagine per specificare la modalità di visualizzazione delle classi di dominio in una finestra di progettazione generata. Definire una forma di immagine impostando `Image` la proprietà della classe su un file di immagine predefinito. Sono supportati i formati seguenti:

- gif

- jpg

- jpeg

- bmp

- Wmf

- emf

- png

Per impostazione predefinita, i file di risorse della finestra di progettazione, ad esempio i file di immagine, si trovano nella **cartella Risorse** del **progetto Dsl.**

Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

Le forme immagine hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento della forma.|White|
|Modalità sfumatura di riempimento|Modalità sfumatura di riempimento di questa forma.|Ridimensionamento orizzontale|
|Dispone di punti di connessione predefiniti|Se `True` , la forma userà i punti di connessione superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|Falso|
|Colore del contorno|Colore del contorno della forma.|Nero|
|Stile tratteggio del contorno|Stile del tratteggio del contorno di questa forma (Tinta unita, Trattino, Punto, DashDot, DashDotDot o Personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Modificatore di accesso della forma geometrica (public o internal).|Blockchain pubblica|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe del codice sorgente generata da questa forma.|\<none>|
|Genera un valore derivato da Double|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla forma dell'immagine ( `none` , `abstract` o `sealed` ).|Nessuno|
|Forma immagine di base|Classe di base di questa forma.|(nessuna)|
|Nome|Nome della forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi associato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Posizione in cui è definita la descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione `Fixed Tooltip Text` comando; se variabile, la descrizione comando viene definita nel codice personalizzato.|Nessuno|
|Note|Note informali associate a questa forma.|\<none>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale della forma, espressa in pollici.|1.5|
|Esposizione del colore di riempimento come proprietà<br /><br /> Modalità sfumatura di riempimento esposta<br /><br /> Colore del contorno esposto come proprietà<br /><br /> Stile del trattino del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla definizione della forma e **scegliere Aggiungi esposto.**|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida F1 per questo elemento.|\<none>|
|Immagine|Percorso del file di immagine utilizzato per questa forma.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))