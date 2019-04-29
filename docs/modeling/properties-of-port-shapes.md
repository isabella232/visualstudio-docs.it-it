---
title: Proprietà delle forme delle porte
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97de488672ac201a418326e39535b7e7c9bd643b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823926"
---
# <a name="properties-of-port-shapes"></a>Proprietà delle forme delle porte
È possibile usare le forme porta per rappresentare le classi di dominio nella finestra di progettazione generata.

 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Forme porta hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Colore riempimento|Il colore di riempimento di questa forma.|Bianco|
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma.|Orizzontale|
|Geometry|La geometria della forma (rettangolo, rettangolo con angoli arrotondati, dell'ellisse o cerchio).|Rettangolo|
|Offre punti di connessione predefinito|Se `True`, la forma userà superiore, inferiore, sinistro e i punti di connessione a destra nella finestra di progettazione generata.|False|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile del tratteggio di struttura|Lo stile di tratteggio contorno di questa forma (tinta unita, Dash, Dot, Trattopunto, Trattopuntopunto o personalizzato).|Tinta unita|
|Spessore del contorno|Lo spessore del contorno di questa forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Il livello di accesso della classe (`public` o `internal`).|Public|
|Attributi personalizzati|Consente di aggiungere attributi alla classe del codice sorgente che viene generata da questa forma.|\<nessuno>|
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla porta (`none`, `abstract` o `sealed`).|none|
|Porta di base|Classe di base di questa forma.|(nessuno)|
|Nome|Il nome di questa forma.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di suggerimento dello strumento|Modalità la descrizione comando viene definito (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene usata come descrizione comando; se la variabile, la descrizione comando è definito nel codice personalizzato.|none|
|Note|Note informali associate a questa forma.|\<nessuno>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1,5|
|Colore di riempimento esposte come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Esposizione del colore del contorno come proprietà<br /><br /> Esposta dello stile di tratteggio di struttura come proprietà<br /><br /> Esposti come proprietà dello spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà specificata di una forma. Per procedere, fare doppio clic la definizione della forma e fare clic su **Aggiungi esposta**.|False|
|Descrizione|Consente di documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<nessuno>|
|Testo della descrizione comando fissa|Testo che viene usato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questa forma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)