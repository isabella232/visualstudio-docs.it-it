---
title: Proprietà dei ruoli di dominio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dcad8664fd0759a81e7c676c2d266475a3db9fe
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923278"
---
# <a name="properties-of-domain-roles"></a>Proprietà dei ruoli di dominio
Le proprietà nella tabella seguente sono associate a un ruolo di dominio. Per informazioni sui ruoli di dominio, vedere [informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Tipo di raccolta|Se questo ruolo ha molteplicità pari a 0.. * o 1... \*, questa proprietà consente di personalizzare il tipo generico che viene utilizzato per memorizzare la raccolta di collegamenti.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene usato|
|Attributi personalizzati|Gli attributi specificati in questo punto verranno aggiunto come attributi alla classe del codice generato.|< Nessuno\>|
|È possibile visualizzare proprietà|Se `True`, e se la molteplicità della relazione è 0..1 1 o 1, la proprietà del ruolo può essere visualizzata dall'utente nella finestra di **proprietà** finestra. La proprietà consente di visualizzare il nome dell'elemento a altra estremità del collegamento della relazione.|`True`|
|Generatore di proprietà|Se `True`, viene generata una proprietà di ruolo per questo ruolo, che è possibile usare per attraversare la relazione nel codice del programma. Se si imposta questa false, è possibile attraversare la relazione in modo meno efficiente usando metodi statici della relazione di dominio.|`True`|
|Modificatore di accesso Getter proprietà|Il modificatore di accesso per il metodo Get per la proprietà generata (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Modificatore di accesso Setter di proprietà|Il modificatore di accesso per il setter per la proprietà generata (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Multiplicity|Il numero di elementi del modello che svolge il ruolo opposto (`0..1`, `1..1`, `0..*`, o `1..*`). Se la molteplicità `0..*` o `1..*`, quindi la proprietà generata rappresenta una raccolta; in caso contrario, la proprietà generata rappresenta un singolo elemento del modello.|Dipende dal tipo di relazione e se si tratta del ruolo di origine o destinazione della relazione.|
|nome|Il nome del ruolo del dominio. Questa proprietà non può contenere spazi vuoti.|Il nome della classe di dominio dell'assegnatario del ruolo per questo ruolo.|
|Propaga copia|`DoNotPropagateCopy` -L'assegnatario del ruolo copiato non avrà alcuna copia del collegamento.<br /><br /> `PropagateCopyToLinkOnly` -Il collegamento copiato punta a esistente assegnatario di ruolo opposto.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Il collegamento copiato punta a una copia dell'assegnatario del ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine di rappresentazioni distribuite.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per altre informazioni, vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)|
|Propaga eliminazione|`True` Per eliminare l'elemento che riveste il ruolo quando viene eliminato il collegamento associato.|`True` per la destinazione di un ruolo di incorporamento.<br /><br /> `False` per altri ruoli.<br /><br /> Per altre informazioni, vedere [personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md).|
|Nome proprietà|Il nome della proprietà generata nel codice dell'assegnatario del ruolo. Questo nome non può contenere spazi vuoti.|Il nome del ruolo opposto se questo ruolo dispone di un zero-a-uno o una molteplicità uno a uno; in caso contrario, il nome pluralizzato del ruolo opposto.|
|Assegnatario del ruolo|La classe di dominio dell'elemento che può rivestire questo ruolo nella relazione. Questa proprietà è di sola lettura.|La classe di dominio dell'assegnatario del ruolo per questo ruolo.|
|Note|Note informali associate con il ruolo di dominio.|< Nessuno\>|
|Category|La categoria in cui la proprietà generata viene visualizzata nella **proprietà** finestra nella finestra di progettazione generata. Se questa proprietà è vuota, quindi la proprietà generata viene visualizzata sotto il **Misc** categoria|< Nessuno\>|
|Descrizione|La descrizione che consente di documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generata.<br /><br /> La descrizione viene visualizzata nella descrizione comandi IntelliSense per la proprietà generata nella classe dell'assegnatario di ruolo.|`Description for` *il nome completo del ruolo*|
|Nome visualizzato|Il nome visualizzato nella finestra di progettazione generata per il ruolo di dominio.|Valore modificato della proprietà Name.|
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida F1 per il ruolo di dominio.|\<nessuno>|
|Nome visualizzato proprietà|Il nome visualizzato nella finestra di progettazione generata per la proprietà di ruolo generato.|Valore della proprietà del nome di proprietà modificato.|

> [!NOTE]
> Il valore predefinito di un nome visualizzato è basato sul valore della proprietà associato tramite l'inserimento di spazi prima di ogni carattere maiuscolo, che è preceduto da un carattere minuscolo e che non è seguito da un altro carattere maiuscolo.

## <a name="see-also"></a>Vedere anche

- [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)