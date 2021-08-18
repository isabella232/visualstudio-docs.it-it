---
title: Proprietà delle forme d'immagine
description: Informazioni sulle forme immagine e su come usare le forme immagine per specificare la modalità di visualizzazione delle classi di dominio in una finestra di progettazione generata.
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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: bf8e185030f459e758a578c38ede44e14588326a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116604"
---
# <a name="properties-of-image-shapes"></a>Proprietà delle forme d'immagine

È possibile usare forme immagine per specificare la modalità di visualizzazione delle classi di dominio in una finestra di progettazione generata. Definire una forma immagine impostando `Image` la proprietà della classe su un file di immagine predefinito. Sono supportati i formati seguenti:

- gif

- jpg

- jpeg

- bmp

- Wmf

- emf

- png

Per impostazione predefinita, i file di risorse della finestra di progettazione, ad esempio i file di immagine, si trovano nella **cartella Resources** del **progetto Dsl.**

Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [Personalizzazione](../modeling/customizing-and-extending-a-domain-specific-language.md)ed estensione di un Domain-Specific language .

Le forme immagine hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento della forma.|White|
|Modalità sfumatura di riempimento|Modalità sfumatura di riempimento di questa forma.|Ridimensionamento orizzontale|
|Dispone di punti di connessione predefiniti|Se , la forma userà i punti di connessione `True` superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|Falso|
|Colore contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggio contorno|Stile del trattino del contorno di questa forma (Tinta unita, Tratteggio, Punto, DashDot, DashDotDot o Personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Modificatore di accesso della forma geometry (pubblico o interno).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe del codice sorgente generata da questa forma.|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla forma dell'immagine ( `none` o `abstract` `sealed` ).|Nessuno|
|Forma immagine di base|Classe di base di questa forma.|(nessuna)|
|Nome|Nome della forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Posizione in cui è definita la descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione comando; se variabile, la descrizione comando `Fixed Tooltip Text` viene definita nel codice personalizzato.|Nessuno|
|Note|Note informali associate a questa forma.|\<none>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale della forma, espressa in pollici.|1.5|
|Proprietà Exposed Fill Color As<br /><br /> Modalità sfumatura di riempimento esposta<br /><br /> Proprietà Exposed Outline Color As<br /><br /> Proprietà Exposed Outline Dash Style As<br /><br /> Proprietà Exposed Outline Thickness As<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposto**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave usata per indicizzare la Guida di F1 per questo elemento.|\<none>|
|Immagine|Percorso del file di immagine utilizzato per questa forma.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))