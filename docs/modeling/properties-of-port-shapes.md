---
title: Proprietà delle forme delle porte
description: Informazioni sulle forme porta e su come è possibile usare le forme porta per rappresentare le classi di dominio nella finestra di progettazione generata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c51d770392fd219478b3e8f8aa428cdcbab6ef3e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362821"
---
# <a name="properties-of-port-shapes"></a>Proprietà delle forme delle porte
È possibile utilizzare le forme porta per rappresentare le classi di dominio nella finestra di progettazione generata.

 Per ulteriori informazioni, vedere [come definire un linguaggio Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le forme porta hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore riempimento|Colore di riempimento di questa forma.|bianco|
|Modalità gradiente riempimento|Modalità di sfumatura riempimento di questa forma.|Ridimensionamento orizzontale|
|Geometria|Geometria di questa forma (rettangolo, rettangolo arrotondato, ellisse o cerchio).|Rettangolo|
|Con punti di connessione predefiniti|Se `True` , la forma utilizzerà i punti di connessione superiore, inferiore, sinistro e destro nella finestra di progettazione generata.|Falso|
|Colore del contorno|Colore del contorno di questa forma.|Nero|
|Stile tratteggiato contorno|Stile di tratteggio del contorno di questa forma (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto o personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno di questa forma.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa forma.|Nero|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questa forma.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla porta ( `none` `abstract` o `sealed` ).|Nessuno|
|Porta di base|Classe di base di questa forma.|(nessuna)|
|Nome|Nome di questa forma.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa forma.|Spazio dei nomi corrente|
|Tipo descrizione comando|Modalità di definizione della descrizione comando (fixed, variable o None). Se è corretto, il valore della `Fixed Tooltip Text` proprietà viene usato come descrizione comando; se variabile, la descrizione comando è definita nel codice personalizzato.|Nessuno|
|Note|Note informali associate a questa forma.|\<none>|
|Altezza iniziale|Altezza iniziale di questa forma, in pollici.|1|
|Larghezza iniziale|Larghezza iniziale di questa forma, in pollici.|1.5|
|Colore riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposta<br /><br /> Colore struttura esposto come proprietà<br /><br /> Stile tratteggiato del contorno esposto come proprietà<br /><br /> Spessore del contorno esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|Falso|
|Description|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa forma.|\<none>|
|Testo del suggerimento dello strumento fisso|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questa forma.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))