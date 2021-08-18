---
title: Proprietà dei connettori
description: Si apprenderà che i connettori rappresentano relazioni di dominio in una finestra di progettazione generata e che queste proprietà vengono usate per personalizzare ed estendere un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: ada7d2c78b818c18c9fdf21618ce66595eb9acfd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100764"
---
# <a name="properties-of-connectors"></a>Proprietà dei connettori
I connettori rappresentano le relazioni di dominio in una finestra di progettazione generata.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 I connettori hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Color|Colore di questo connettore.|Nero|
|Stile trattino|Stile del trattino per la linea per questo connettore (Tinta unita, Trattino, Punto, DashDot, DashDotDot o Personalizzato).|Tinta unita|
|Stile di fine origine|Stile finale di origine per questo connettore (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Stile di fine destinazione|Stile finale di destinazione per questo connettore (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questo connettore.|Nero|
|Thickness|Spessore della linea per il connettore, misurata in pollici.|0.03125|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Usato per aggiungere attributi alla classe del codice sorgente generata da questo connettore.|\<none>|
|Genera un valore derivato da Double|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal connettore ( `none` , `abstract` o `sealed` ).|Nessuno|
|Connettore di base|Classe di base di questo connettore.|(nessuna)|
|Nome|Nome del connettore.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi associato a questo connettore.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fissa, variabile o nessuna). Se fixed, il valore della proprietà viene usato come descrizione `Fixed Tooltip Text` comando; se variabile, la descrizione comando viene definita nel codice personalizzato.|\<none>|
|Note|Note informali associate a questo connettore.|\<none>|
|Stile di routing|Stile utilizzato per il routing del connettore. Un `Rectilinear` connettore esegue turni ad angolo retto in base alle esigenze, mentre un `Straight` connettore no.|Rettilineo|
|Colore esposto come proprietà<br /><br /> Stile del trattino esposto come proprietà<br /><br /> Spessore esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà specificata di una forma. Per impostare questa proprietà, fare clic con il pulsante destro del mouse sulla definizione della forma e **scegliere Aggiungi esposto.**|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo connettore.|\<none>|
|Correzione del testo della descrizione comando|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida F1 per questo elemento.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))