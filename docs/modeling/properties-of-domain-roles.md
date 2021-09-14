---
title: Proprietà dei ruoli di dominio
description: Informazioni sulle proprietà associate a un ruolo di dominio, ad esempio Tipo di raccolta, Attributi personalizzati e Is Property Browsable.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f542faecf3ba1ac64076f145cc1e280cf255aad6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637532"
---
# <a name="properties-of-domain-roles"></a>Proprietà dei ruoli di dominio
Le proprietà nella tabella seguente sono associate a un ruolo di dominio. Per informazioni sui ruoli di dominio, vedere [Informazioni su modelli, classi e relazioni.](../modeling/understanding-models-classes-and-relationships.md) Per altre informazioni su come usare queste proprietà, vedere [Personalizzazione](../modeling/customizing-and-extending-a-domain-specific-language.md)ed estensione di un Domain-Specific language .

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Tipo di raccolta|Se questo ruolo ha molteplicità 0..*o 1.. , questa proprietà personalizza il tipo generico usato per archiviare la \* raccolta di collegamenti.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene usato|
|Attributi personalizzati|Gli attributi specificati qui verranno aggiunti come attributi alla classe di codice generata.|<nessuno\>|
|Proprietà esplorabile|Se e se la molteplicità della relazione è `True` 0..1 o 1...1, la proprietà  del ruolo può essere visualizzata dall'utente nella finestra Proprietà. La proprietà visualizza il nome dell'elemento all'altra estremità del collegamento alla relazione.|`True`|
|Generatore di proprietà Is|Se , viene generata una proprietà del ruolo per questo ruolo, che è possibile usare per `True` attraversare la relazione nel codice del programma. Se si imposta questo valore false, è possibile attraversare la relazione in modo meno efficiente usando metodi statici della relazione di dominio.|`True`|
|Modificatore di accesso del metodo Property|Modificatore di accesso per il metodo get per la proprietà generata ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Modificatore di accesso del setter di proprietà|Modificatore di accesso per il setter per la proprietà generata ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Molteplicità|Numero di elementi del modello che possono svolgere il ruolo opposto ( `0..1` , `1..1` , o `0..*` `1..*` ). Se la molteplicità è o , la proprietà generata rappresenta una raccolta; in caso contrario, la proprietà `0..*` generata rappresenta un singolo elemento del `1..*` modello.|Dipende dal tipo di relazione e dal fatto che si tratta del ruolo di origine o di destinazione nella relazione.|
|Nome|Nome del ruolo di dominio. Questa proprietà non può contenere spazi vuoti.|Nome della classe di dominio del ruolo lettore per questo ruolo.|
|Propaga copia|`DoNotPropagateCopy` - Il ruolo lettore copiato non avrà alcuna copia di questo collegamento.<br /><br /> `PropagateCopyToLinkOnly` : il collegamento copiato punta al lettore di ruolo opposto esistente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` : il collegamento copiato punta a una copia del lettore di ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine degli incorporamenti.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per altre informazioni, vedere [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)|
|Propaga eliminazioni|`True` per eliminare l'elemento che svolge questo ruolo quando viene eliminato il collegamento associato.|`True` per la destinazione di un ruolo di incorporamento.<br /><br /> `False` per altri ruoli.|
|Nome della proprietà|Nome della proprietà generata nel codice del ruolo lettore. Questo nome non può contenere spazi vuoti.|Nome del ruolo opposto se questo ruolo ha una molteplicità uno-a-uno o uno-a-uno; in caso contrario, nome pluralizzato del ruolo opposto.|
|Ruolo lettore|Classe di dominio dell'elemento che può svolgere questo ruolo nella relazione. Questa proprietà è di sola lettura.|Classe di dominio del ruolo lettore per questo ruolo.|
|Note|Note informali associate al ruolo di dominio.|<nessuno\>|
|Category|Categoria in cui la proprietà generata viene visualizzata nella **finestra Proprietà** della finestra di progettazione generata. Se questa proprietà è vuota, la proprietà generata viene visualizzata nella **categoria Misc**|<nessuno\>|
|Descrizione|Descrizione usata per documentare il codice e usata nell'interfaccia utente della finestra di progettazione generata.<br /><br /> La descrizione viene visualizzata nella descrizione comando intelliSense per la proprietà generata nella classe del ruolo player.|`Description for`*nome completo del ruolo*|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per il ruolo di dominio.|Valore modificato della proprietà Name.|
|Parola chiave della Guida|Parola chiave facoltativa usata per indicizzare la Guida F1 per il ruolo di dominio.|\<none>|
|Nome visualizzato della proprietà|Nome visualizzato nella finestra di progettazione generata per la proprietà del ruolo generata.|Valore modificato della proprietà Nome proprietà.|

> [!NOTE]
> Il valore predefinito di un nome visualizzato si basa sul valore della proprietà associata inserendo spazi prima di ogni carattere maiuscolo preceduto da un carattere minuscolo e non seguito da un altro carattere maiuscolo.

## <a name="see-also"></a>Vedi anche

- [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)