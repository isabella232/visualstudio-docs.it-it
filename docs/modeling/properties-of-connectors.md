---
title: Proprietà dei connettori
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2244b191bac2456886368992d1dc8f1c571dc227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658251"
---
# <a name="properties-of-connectors"></a>Proprietà dei connettori
I connettori rappresentano le relazioni di dominio in una finestra di progettazione generata.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 I connettori hanno le proprietà elencate nella tabella seguente.

|proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Colore|Colore del connettore.|Nero|
|Stile tratteggiato|Stile tratteggiato per la linea per questo connettore (tinta unita, trattino, punto, DashDot, TrattoPuntoPunto o personalizzato).|Tinta unita|
|Stile dell'estremità di origine|Stile dell'estremità di origine per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Stile fine destinazione|Stile dell'estremità di destinazione per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Nessuno|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questo connettore.|Nero|
|Thickness|Spessore della linea per questo connettore, misurato in pollici.|0,03125|
|Modificatore di accesso|Livello di accesso della classe (`public` o `internal`).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questo connettore.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dal connettore (`none`, `abstract` o `sealed`).|none|
|Connettore di base|Classe di base di questo connettore.|(nessuno)|
|Name|Nome del connettore.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi affiliato a questo connettore.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (fixed, variable o None). Se è fixed, il valore della proprietà `Fixed Tooltip Text` viene usato come descrizione comando; Se variabile, la descrizione comando è definita nel codice personalizzato.|\<nessuno>|
|Note|Note informali associate a questo connettore.|\<nessuno>|
|Stile di routing|Stile utilizzato per il routing del connettore. Un connettore `Rectilinear` esegue le svolte con angolo destro secondo le esigenze. un connettore `Straight` non lo è.|Rettilineo|
|Colore esposto come proprietà<br /><br /> Stile tratteggiato esposto come proprietà<br /><br /> Spessore esposto come proprietà<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà dichiarata di una forma. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla definizione della forma e scegliere **Aggiungi esposti**.|False|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questo connettore.|\<nessuno>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questo elemento.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)