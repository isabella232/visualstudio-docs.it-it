---
title: Proprietà delle forme di raggruppamento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ad53866c1930edb01ccd163131ce5e23644929c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747503"
---
# <a name="properties-of-compartment-shapes"></a>Proprietà delle forme di raggruppamento
Le forme raggruppamento sono una delle forme che è possibile utilizzare per visualizzare una classe di dominio in un linguaggio specifico di dominio. È possibile espandere e comprimere i raggruppamenti.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le forme di raggruppamento hanno le proprietà elencate nella tabella seguente.

|proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Espandi stato di compressione predefinito|Se `Expanded`, i raggruppamenti vengono visualizzati durante la creazione. Se `Collapsed`, non lo sono.|Espanso|
|Colore riempimento|Colore di riempimento di questa forma.|bianco|
|Modalità gradiente riempimento|Modalità di sfumatura riempimento di questa forma.|Orizzontale|
|Geometry|Geometria di questa forma (rettangolo o rettangolo arrotondato).|Rettangolo|
|Con punti di connessione predefiniti|Se `True`, la forma utilizzerà i punti di connessione superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|False|
|Intestazione a raggruppamento singolo visibile|Se `False` e la forma presenta un unico raggruppamento, l'intestazione del raggruppamento non è visibile.|True|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggiato contorno|Stile di tratteggio del contorno di questa forma (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto, personalizzata).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Livello di accesso della forma raggruppamento (`public` o `internal`).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questa forma di raggruppamento|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla forma raggruppamento (`none`, `abstract` o `sealed`).|Nessuno|
|Forma raggruppamento di base|Classe di base di questa forma.|(nessuno)|
|Name|Nome di questa forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fixed, variable o None). Se è fixed, il valore della proprietà `Fixed Tooltip Text` viene usato come descrizione comando; Se variabile, la descrizione comando è definita nel codice personalizzato.|none|
|Note|Note informali associate a questa forma.|\<nessuno>|
|Altezza iniziale|Altezza iniziale di questa forma, in pollici. Per le forme di raggruppamento, si tratta dell'altezza della sezione dell'intestazione e non può essere ridimensionata.|1|
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1.5|
|Colore riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposta<br /><br /> Colore struttura esposto come proprietà<br /><br /> Stile tratteggiato del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|False|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<nessuno>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questa forma.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)