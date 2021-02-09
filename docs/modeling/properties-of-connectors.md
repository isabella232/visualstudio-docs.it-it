---
title: Proprietà dei connettori
description: Informazioni sui connettori che rappresentano le relazioni di dominio in una finestra di progettazione generata e che vengono utilizzate per personalizzare ed estendere un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b09ec4278dd78f797067c3acdf3152736fb395c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899854"
---
# <a name="properties-of-connectors"></a>Proprietà dei connettori
I connettori rappresentano le relazioni di dominio in una finestra di progettazione generata.

 Per ulteriori informazioni, vedere [come definire un linguaggio Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 I connettori hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Colore|Colore di questo connettore.|Nero|
|Stile tratteggiato|Stile tratteggiato per la linea per questo connettore (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto o personalizzato).|Tinta unita|
|Stile dell'estremità di origine|Stile dell'estremità di origine per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|nessuno|
|Stile fine destinazione|Stile dell'estremità di destinazione per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|nessuno|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questo connettore.|Nero|
|Thickness|Spessore della linea per il connettore, misurata in pollici.|0,03125|
|Modificatore di accesso|Livello di accesso della classe ( `public` o `internal` ).|Pubblico|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questo connettore.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal connettore ( `none` `abstract` o `sealed` ).|Nessuno|
|Connettore di base|Classe di base di questo connettore.|(nessuna)|
|Nome|Nome del connettore.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi affiliato a questo connettore.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fixed, variable o None). Se è corretto, il valore della `Fixed Tooltip Text` proprietà viene usato come descrizione comando; se variabile, la descrizione comando è definita nel codice personalizzato.|\<none>|
|Note|Note informali associate a questo connettore.|\<none>|
|Stile di routing|Stile utilizzato per il routing del connettore. Un `Rectilinear` connettore esegue le svolte con angolo destro come richiesto; un `Straight` connettore non lo esegue.|Rettilineo|
|Colore esposto come proprietà<br /><br /> Stile tratteggiato esposto come proprietà<br /><br /> Spessore esposto come proprietà<br /><br /> Espone il colore del testo|Se `True` , l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|Falso|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo connettore.|\<none>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<none>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo elemento.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))