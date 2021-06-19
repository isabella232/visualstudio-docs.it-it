---
title: Proprietà dei connettori
description: Informazioni sul fatto che i connettori rappresentano relazioni di dominio in una finestra di progettazione generata e che queste proprietà vengono usate per personalizzare ed estendere un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43f55aecf134bf8e4d043a4fc7f6ffa2201f8e95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390815"
---
# <a name="properties-of-connectors"></a>Proprietà dei connettori
I connettori rappresentano le relazioni di dominio in una finestra di progettazione generata.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 I connettori hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Color|Colore di questo connettore.|Nero|
|Stile tratteggio|Stile del trattino per la linea per questo connettore (Solid, Dash, Dot, DashDot, DashDotDot o Custom).|Tinta unita|
|Stile di fine origine|Stile finale di origine per questo connettore (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Stile di fine di destinazione|Stile finale di destinazione per questo connettore (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questo connettore.|Nero|
|Thickness|Spessore della linea per il connettore, misurata in pollici.|0.03125|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Blockchain pubblica|
|Attributi personalizzati|Usato per aggiungere attributi alla classe del codice sorgente generata da questo connettore.|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dal connettore ( `none` o `abstract` `sealed` ).|Nessuno|
|Connettore di base|Classe di base di questo connettore.|(nessuna)|
|Nome|Nome del connettore.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questo connettore.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione comando; se variabile, la descrizione comando `Fixed Tooltip Text` viene definita nel codice personalizzato.|\<none>|
|Note|Note informali associate a questo connettore.|\<none>|
|Stile di routing|Stile utilizzato per il routing del connettore. Un `Rectilinear` connettore esegue i turni ad angolo retto in base alle esigenze, mentre un `Straight` connettore no.|Rettilineo|
|Proprietà Exposed Color As<br /><br /> Proprietà Exposed Dash Style As<br /><br /> Proprietà Thickness As esposta<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposto**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo connettore.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave usata per indicizzare la Guida di F1 per questo elemento.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))