---
title: Proprietà dei ruoli di dominio
description: Informazioni sulle proprietà associate a un ruolo di dominio, ad esempio Tipo di raccolta, Attributi personalizzati e Esplorabile proprietà.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085572"
---
# <a name="properties-of-domain-roles"></a>Proprietà dei ruoli di dominio
Le proprietà nella tabella seguente sono associate a un ruolo di dominio. Per informazioni sui ruoli di dominio, vedere [Informazioni su modelli, classi e relazioni.](../modeling/understanding-models-classes-and-relationships.md) Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Tipo di raccolta|Se questo ruolo ha molteplicità di 0..*o 1.. , questa proprietà personalizza il tipo generico usato per archiviare la \* raccolta di collegamenti.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene usato|
|Attributi personalizzati|Gli attributi specificati qui verranno aggiunti come attributi alla classe di codice generata.|<nessuno\>|
|Is Property Browsable|Se e se la molteplicità della relazione è `True` 0..1 o 1..1, la proprietà del ruolo può essere visualizzata dall'utente nella **finestra** Proprietà. La proprietà visualizza il nome dell'elemento all'altra estremità del collegamento della relazione.|`True`|
|Generatore di proprietà Is|Se `True` , viene generata una proprietà del ruolo per questo ruolo, che è possibile usare per attraversare la relazione nel codice programma. Se si imposta questo valore false, è possibile attraversare la relazione in modo meno efficiente usando metodi statici della relazione di dominio.|`True`|
|Modificatore di accesso per il getter di proprietà|Modificatore di accesso per il getter per la proprietà generata ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Modificatore di accesso del setter di proprietà|Modificatore di accesso per il setter per la proprietà generata ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Molteplicità|Numero di elementi del modello che possono svolgere il ruolo opposto ( `0..1` , `1..1` , o `0..*` `1..*` ). Se la molteplicità è o , la proprietà generata rappresenta una raccolta; in caso contrario, la proprietà `0..*` generata rappresenta un singolo elemento del `1..*` modello.|Dipende dal tipo di relazione e dal fatto che si tratta del ruolo di origine o di destinazione nella relazione.|
|Nome|Nome del ruolo di dominio. Questa proprietà non può contenere spazi vuoti.|Nome della classe di dominio del ruolo lettore per questo ruolo.|
|Propaga copia|`DoNotPropagateCopy` - Il ruolo lettore copiato non avrà alcuna copia di questo collegamento.<br /><br /> `PropagateCopyToLinkOnly` - Il collegamento copiato punta al lettore di ruolo opposto esistente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` - Il collegamento copiato punta a una copia del lettore di ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine delle incorporamenti.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per altre informazioni, vedere [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)|
|Propaga l'eliminazione|`True` per eliminare l'elemento che svolge questo ruolo quando viene eliminato il collegamento associato.|`True` per la destinazione di un ruolo di incorporamento.<br /><br /> `False` per altri ruoli.|
|Nome della proprietà|Nome della proprietà generata nel codice del ruolo lettore. Questo nome non può contenere spazi vuoti.|Nome del ruolo opposto se questo ruolo ha una molteplicità uno-a-uno o uno-a-uno; in caso contrario, nome pluralizzato del ruolo opposto.|
|Ruolo lettore|Classe di dominio dell'elemento che può svolgere questo ruolo nella relazione. Questa proprietà è di sola lettura.|Classe di dominio del ruolo lettore per questo ruolo.|
|Note|Note informali associate al ruolo del dominio.|<nessuno\>|
|Category|Categoria in cui la proprietà generata viene visualizzata nella **finestra Proprietà** della finestra di progettazione generata. Se questa proprietà è vuota, la proprietà generata viene visualizzata nella **categoria Varie**|<nessuno\>|
|Descrizione|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.<br /><br /> La descrizione viene visualizzata nella descrizione comando di IntelliSense per la proprietà generata nella classe del ruolo lettore.|`Description for`*nome completo del ruolo*|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per il ruolo di dominio.|Valore regolato della proprietà Name.|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida F1 per il ruolo di dominio.|\<none>|
|Nome visualizzato proprietà|Nome visualizzato nella finestra di progettazione generata per la proprietà del ruolo generata.|Valore regolato della proprietà Nome proprietà.|

> [!NOTE]
> Il valore predefinito di un nome visualizzato si basa sul valore della proprietà associata inserendo spazi prima di ogni carattere maiuscolo preceduto da un carattere minuscolo e non seguito da un altro carattere maiuscolo.

## <a name="see-also"></a>Vedi anche

- [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)