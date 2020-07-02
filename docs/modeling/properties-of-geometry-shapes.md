---
title: Proprietà delle forme geometriche
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1d97cc53e55a809b9dd43d572e7395abc5a8344
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544131"
---
# <a name="properties-of-geometry-shapes"></a>Proprietà delle forme geometriche
È possibile utilizzare forme Geometry per specificare il modo in cui le istanze delle classi di dominio vengono visualizzate in un linguaggio specifico di dominio. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le forme Geometry hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento di questa forma.|bianco|
|Modalità gradiente riempimento|Modalità di sfumatura riempimento di questa forma (orizzontale, verticale, diagonale in avanti, diagonale posteriore o nessuna).|Ridimensionamento orizzontale|
|Geometry|Geometria di questa forma (rettangolo, rettangolo arrotondato, ellisse o cerchio).|Rettangolo|
|Con punti di connessione predefiniti|Se `True` , la forma utilizzerà i punti di connessione superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|False|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggiato contorno|Stile di tratteggio del contorno di questa forma (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto o personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Modificatore di accesso della classe (Public o Internal).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata per questa forma.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla forma ( `none` , `abstract` o `sealed` ).|Nessuno|
|Forma geometria di base|Classe di base di questa forma.|(nessuna)|
|Name|Nome di questa forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fixed, variable o None). Se è corretto, il valore della `Fixed Tooltip Text` proprietà viene usato come descrizione comando; se variabile, la descrizione comando è definita nel codice personalizzato.|nessuno|
|Note|Note informali associate a questo elemento.|\<none>|
|Altezza iniziale|Altezza iniziale della forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale della forma, in pollici.|1.5|
|Colore riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposta<br /><br /> Colore struttura esposto come proprietà<br /><br /> Stile tratteggiato del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|False|
|Descrizione|Descrizione utilizzata per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questa forma.|\<none>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)