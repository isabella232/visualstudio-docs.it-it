---
title: Proprietà delle forme d'immagine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e58467d9a1600b96069bcd5dd271980faaf9ee7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938150"
---
# <a name="properties-of-image-shapes"></a>Proprietà delle forme d'immagine

È possibile usare forme d'immagine per specificare l'aspetto delle classi di dominio in una finestra di progettazione generata. Definire una forma immagine impostando il `Image` proprietà della classe in un file di immagine predefinito. Sono supportati i formati seguenti:

- .gif

- .jpg

- .jpeg

- .bmp

- .wmf

- .emf

- .png

Per impostazione predefinita, i file di risorse della finestra di progettazione, ad esempio i file di immagine, si trovano nel **risorse** cartella le **Dsl** progetto.

Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

Forme d'immagine hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Colore riempimento|Il colore di riempimento di questa forma.|Bianco|
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma.|Orizzontale|
|Offre punti di connessione predefinito|Se `True`, la forma userà superiore, inferiore, sinistro e i punti di connessione a destra nella finestra di progettazione generata.|False|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile del tratteggio di struttura|Lo stile di tratteggio contorno di questa forma (tinta unita, Dash, Dot, Trattopunto, Trattopuntopunto o personalizzato).|Tinta unita|
|Spessore del contorno|Lo spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Il modificatore di accesso della forma geometria (pubblico o interno).|Public|
|Attributi personalizzati|Consente di aggiungere attributi alla classe del codice sorgente che viene generata da questa forma.|\<nessuno>|
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla forma dell'immagine (`none`, `abstract` o `sealed`).|none|
|Forma immagine di base|Classe di base di questa forma.|(nessuno)|
|nome|Il nome di questa forma.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo della descrizione comando|La posizione in cui è definito la descrizione comando (fissata, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene usata come descrizione comando; se la variabile, la descrizione comando è definito nel codice personalizzato.|none|
|Note|Note informali associate a questa forma.|\<nessuno>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1,5|
|Colore di riempimento esposte come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Esposizione del colore del contorno come proprietà<br /><br /> Esposta dello stile di tratteggio di struttura come proprietà<br /><br /> Esposti come proprietà dello spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà specificata di una forma. Per procedere, fare doppio clic la definizione della forma e fare clic su **Aggiungi esposta**.|False|
|Descrizione|Consente di documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<nessuno>|
|Testo della descrizione comando fissa|Testo che viene usato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questo elemento.|\<nessuno>|
|Image|Il percorso del file di immagine che viene usato per questa forma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)